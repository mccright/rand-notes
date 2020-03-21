## Note about cloning GIT repositories in a docker container

Most GIT servers support SSH for authenticating access to a Git repository,
see [Git Server Protocols Doc](https://git-scm.com/book/en/v2/Git-on-the-Server-The-Protocols).

SSH is preferable over username/password for several reasons:
- Some repositories like GitHub require a unique SSH key per repository.
  This helps minize the impact of a potential security breach where
  an SSH private key is compromised to just the repository that it is used for.
- See [Wikipedia Key Size](https://en.wikipedia.org/wiki/Key_size) for recommendations
  about RSA key size that are considered safe against brute force attacks.
  Even with the recommended RSA 3072-bit or larger key size, it is highly 
  unlikely that a practical username/password will be stronger against brute-force
  attacks than an RSA key.

## Instructions for generating SSH keys and using them in a docker container environment

- Generate SSH key and configure the repository

  The instructions vary according to the Git repository service used.
  The following list is not intended to be comprehensive but
  to convey the fact that this process is well supported across
  a wide range of Git repository services.
  
  - [Azure Repos](https://docs.microsoft.com/en-us/azure/devops/repos/git/use-ssh-keys-to-authenticate?view=azure-devops)
  - [Bitbucket](https://confluence.atlassian.com/bitbucketserver/ssh-access-keys-for-system-use-776639781.html)
  - [GitHub](https://help.github.com/en/articles/connecting-to-github-with-ssh)
  - [GitLab](https://docs.gitlab.com/ee/ssh/)

  Recommend creating an SSH RSA 4096-bit key *without a passphrase* as 
  this simplifies secret management for automated containerized workflows.
  It is necessary to manage the private SSH key as a secret that needs
  to be made available to the docker container environment
  (e.g., via a volume mount). Adding a passphrase is possible but
  adds some complexity in the configuration management of secret information
  to feed the passphrase to ssh without compromising security (e.g., environment variables).
  Git offers several mechanisms for [requesting credentials](https://git-scm.com/docs/gitcredentials#_requesting_credentials),
  including configuring the `GIT_ASKPASS` and `SSH_ASKPASS` environment variables
  to refer to a script, that, when executed will emit the passphrase on 
  standard output. There could be practical problems due to the fact
  that this mechanism is intended to work for environments with a terminal or display.
  In an automated environment where neither are available, this mechanism
  could become a source of configuration problems.
  
  Using a repository-specific SSH key without a passphrase limits the
  security risk to the disclosure of the SSH private key. For automated
  containerized workflows, this risk can be easily addressed by
  encrypting the private key in a way that is safe to store even on
  a publicly-accessible repository, e.g., see: [sealedsecrets](https://github.com/bitnami-labs/sealed-secrets).
  
  Example for creating an SSH RSA 4096-bit key without a passphrase
  for an automated service:
  
  ```bash
  umask 0077
  ssh-keygen \
    -t rsa \
    -b 4096 \
    -N '' \
    -C "your_email@example.com (your automated service name)" \
    -f SomeKeyFileName
  ```
  
  This will generate two files: `SomeKeyFileName` and `SomeKeyFileName.pub`.
  The `umask` command will ensure the generated files will not be
  accessible by `group` or `other` users.
  
  The file `SomeKeyFileName` needs to be made available to the docker container,
  for example using [docker volumes](https://docs.docker.com/engine/reference/run/#volume-shared-filesystems).
  
- Make sure that DNS addresses resolve by name inside the docker container environment

  Assuming that the docker container image includes the unix utilities
  specified in this project, start a container and verify the following works:
  
  ```bash
  nslookup <github repository host> 
  ```
  
  If the above command fails in the docker container environment,
  then [configure DNS for Docker](https://docs.docker.com/engine/reference/run/#network-settings).
  
  Specifically, find the DNS resolver host needed for `<github repository host>`. 
  Typically, this involves selecting at least one address from `/etc/resolv.conf` 
  on the host, for example, `<dns resolver1>,<dns resolver2>`, and running the
  container like this:
  
  ```bash
  docker run \
    --dns <dns resolver1> \
    --dns <dns resolver2> \
    ...
  ```
  
- Add the github repository host keys

  In the docker container environment:
  
  ```bash
  mkdir /root/.ssh
  ssh-keyscan <repository host> > /root/.ssh/known_hosts
  ```
  
- Configure SSH options

  In the docker container environment, create `/root/.ssh/config` with the following:
  
  ```text
  StrictHostKeyChecking=no
  ```
  
- Create an agent and load the private key

  In the docker container environment:

  ```bash
  eval $(ssh-agent -s)
  ssh-add SomeKeyFileName
  ```
  
- Verify access to the repository
  
  In the docker container environment:
  
  ```bash
  ssh -T git@<github host address>
  ```
  
- Verify the repository deploy key works

  In the docker container environment:

  ```bash
  git clone git@<github host address>:<github organization>/<github repository name>.git
  ```
  
 Thank You to [NicolasRouquette](https://github.com/NicolasRouquette) for original the [content](https://github.com/opencaesar/docker-git-utilities/blob/master/README.md) that I am caching here 
(from his 7aa4100 on Jun 17, 2019 version).  I will be evolving these directions to align with my local needs here.  
If I have broadly-applicable input, I'll submit a pull request.
