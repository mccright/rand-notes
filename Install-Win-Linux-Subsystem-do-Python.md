## Enabling WSL & Doing Python Development on Windows  

Go see: "Get started using Python for web development on Windows."  [https://docs.microsoft.com/en-us/windows/python/web-frameworks](https://docs.microsoft.com/en-us/windows/python/web-frameworks)  

This has links to an excellent 'how to' on Enabling Windows Subsystem for Linux and Installing a Linux distribution into it.  
Most of that content is at: [https://docs.microsoft.com/en-us/windows/wsl/install-win10](https://docs.microsoft.com/en-us/windows/wsl/install-win10)  
And I found the installation manual of your Linux distribution helpful: [https://docs.microsoft.com/en-us/windows/wsl/install-manual](https://docs.microsoft.com/en-us/windows/wsl/install-manual)  
Unless you have a compelling reason to do otherwise, [use WSL 2](https://docs.microsoft.com/en-us/windows/wsl/compare-versions) (*and set it as your default*) to increase file system performance and support full system call compatibility (*as it runs a full Linux kernel*).  

Then add Windows Terminal: [https://docs.microsoft.com/en-us/windows/terminal/get-started](https://docs.microsoft.com/en-us/windows/terminal/get-started) and [https://github.com/microsoft/terminal/releases/latest](https://github.com/microsoft/terminal/releases/latest).  Then configure the application settings to your preferences and add the latest WSL 2 OS image that you may have added above and set up VS Code integration in your chosen OS (*'code .' from a terminal prompt in that OS should get you set up*).  

Finally, install Docker Desktop: [https://docs.docker.com/desktop/windows/](https://docs.docker.com/desktop/windows/) and for the WSL 2-specifics [https://docs.docker.com/desktop/windows/wsl/](https://docs.docker.com/desktop/windows/wsl/)  
