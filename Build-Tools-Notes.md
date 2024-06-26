# Build Tooling  

There are many options for application build tooling.  Anyone involved in application security (*which includes everyone involved in developing and maintaining, even deploying applications*) needs at least a passing familiarity with risk-appropriate use of their build tools.  There is an increasingly broad spectrum of Internet-hosted services that incorporate some or all of the features developers require of build tooling.  That said, a lot of hands-on development still occurs on one or another type of user endpoint (*whether it be a virtual or physical endpoing*).  

Anyone wanting to specialize in *application security* work should have some awareness of what is required to build a range of application types in across a range of development languages and frameworks *and a willingness to research, troubleshoot and ask for help when developers make creative/sophisticated use of their build tooling*.  Here is a list of the build tool kits that I have run into in the course of my application security work in recent years.  It is not meant to be comprehensive...  

### Endpoint hosted build tooling  
* [ant](https://ant.apache.org/manual/tutorial-HelloWorldWithAnt.html)  
* bower  
* buildr  
* bundle  
* cargo (cargo.loml)  
* composer  
* dotnet  
* gem (gemfile.lock)  
* git  
* gradle (build.gradle, build.gradle.kts)  
* make (makefile)  
* makepkg  
* msbuild  
* mvn [Maven] (pom.xml)  
* ninja  
* npm (package.json, package-lock.json)  
* nuget  
* packrat (packrat.lock)  
* pip (requirements.txt, dependency resolver)  
* [pipenv](https://github.com/pypa/pipenv) (Pipfile and Pipfile.lock, dependency resolver), and [pipenv docs](https://pipenv.pypa.io/en/latest/)  
* poetry (poetry.lock, dependency resolver)  
* setuptools (python)  
* rake  
* rant  
* rye [https://rye-up.com/](https://rye-up.com/)  
* sbt  
* **scons**: A multi-language software construction tool [https://scons.org/](https://scons.org/)  
* Thoth ([dependency resolver](https://developers.redhat.com/articles/2022/03/07/manage-python-security-thoths-cloud-based-dependency-resolver#thoth_security_for_python_applications))  
* uv (*pursuing a "Cargo for Python"*) [https://github.com/astral-sh/uv](https://github.com/astral-sh/uv)  
* waf  
* vagrant  
* yarn (yarn.lock)  


Here is a more comprehensive list from WhiteSource Software: [https://whitesource.atlassian.net/wiki/spaces/WD/pages/842596447/Advanced+Technical+Information#Supported-Package-Manager-Dependency-Files](https://whitesource.atlassian.net/wiki/spaces/WD/pages/842596447/Advanced+Technical+Information#Supported-Package-Manager-Dependency-Files)  
