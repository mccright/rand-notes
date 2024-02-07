## Enabling WSL & Doing Python Development on Windows  

Go see: "Get started using Python for web development on Windows."  [https://docs.microsoft.com/en-us/windows/python/web-frameworks](https://docs.microsoft.com/en-us/windows/python/web-frameworks) and more specifically [https://learn.microsoft.com/en-us/windows/python/web-frameworks#install-python-pip-and-venv](https://learn.microsoft.com/en-us/windows/python/web-frameworks#install-python-pip-and-venv)  

This has links to an excellent 'how to' on Enabling Windows Subsystem for Linux and Installing a Linux distribution into it.  
Most of that content is at: [https://docs.microsoft.com/en-us/windows/wsl/install-win10](https://docs.microsoft.com/en-us/windows/wsl/install-win10) with supporting content at [https://learn.microsoft.com/en-us/windows/wsl/install](https://learn.microsoft.com/en-us/windows/wsl/install)  
And I found the installation manual of your Linux distribution helpful: [https://docs.microsoft.com/en-us/windows/wsl/install-manual](https://docs.microsoft.com/en-us/windows/wsl/install-manual)  
Unless you have a compelling reason to do otherwise, [use WSL 2](https://docs.microsoft.com/en-us/windows/wsl/compare-versions) (*and set it as your default*) to increase file system performance and support full system call compatibility (*as it runs a full Linux kernel*).  

Then add Windows Terminal: [https://docs.microsoft.com/en-us/windows/terminal/get-started](https://docs.microsoft.com/en-us/windows/terminal/get-started) and [https://github.com/microsoft/terminal/releases/latest](https://github.com/microsoft/terminal/releases/latest).  Then configure the application settings to your preferences and add the latest WSL 2 OS image that you may have added above and set up VS Code integration in your chosen OS (*'code .' from a terminal prompt in that OS should get you set up*).  There may also be useful information at the [Windows Command Line blog](https://devblogs.microsoft.com/commandline/), which has WSL entries.  


### Community Links:

- Stack Overflow: https://stackoverflow.com/questions/tagged/wsl  
- Ask Ubuntu: https://askubuntu.com/questions/tagged/wsl  
- reddit: https://www.reddit.com/r/bashonubuntuonwindows  
- List of programs that work and don't work  
    - https://github.com/ethanhs/WSL-Programs  
    - https://github.com/davatron5000/can-i-subsystem-it  
- Awesome WSL: https://github.com/sirredbeard/Awesome-WSL  
- Tips and guides for new bash users: https://github.com/abergs/ubuntuonwindows  
*Community Links downloaded from [Microsoft](https://github.com/microsoft/WSL/blob/master/README.md) on 2024/02/07  

### Troubleshooting:

Common WSL troubleshooting issues and solutions are available on [MSDN WSL troubleshooting documentation](https://msdn.microsoft.com/en-us/commandline/wsl/troubleshooting).


Finally, consider installing Docker Desktop: [https://docs.docker.com/desktop/windows/](https://docs.docker.com/desktop/windows/) and for the WSL 2-specifics [https://docs.docker.com/desktop/windows/wsl/](https://docs.docker.com/desktop/windows/wsl/)  
