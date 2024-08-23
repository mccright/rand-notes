## Use "Mermaid" For Flow Diagrams  

Mermaid is a markdown dialetc and a JavaScript library that is just a fantastic toolkit.  It supports creating diagrams as code.  When you host your markdown on github.com or [use Visual Studio Code](https://github.com/mjbvz/vscode-markdown-mermaid) it renders well using the approach below (and there are an [increasing number of integrations](https://github.com/mermaid-js/mermaid/blob/develop/docs/integrations.md) with other platforms).  It has features to support a range of diagramming types.  

Here is a Mermaid block:  

*code*  
```terminal
'''mermaid
graph TD;
  Root-->Node1;
  Node1-->Node3;
  Node1-->Node2;
  Root-->Node2;
  Node2-->Node3;
'''
```

*renders as*  
```mermaid 
graph TD;
  Root-->Node1;
  Node1-->Node3;
  Node1-->Node2;
  Root-->Node2;
  Node2-->Node3;
```
  
#### There are a broad spectrum of use cases where diagramming with Marmaid is a good fit.  
  
* Mermaid JS [https://github.com/mermaid-js/mermaid/releases/latest](https://github.com/mermaid-js/mermaid/releases/latest)  
* Mermaid integrations [https://github.com/mermaid-js/mermaid/blob/develop/docs/integrations.md](https://github.com/mermaid-js/mermaid/blob/develop/docs/integrations.md)  
* Mermaid server [https://github.com/TomWright/mermaid-server](https://github.com/TomWright/mermaid-server)  
* Linux Format Article: "[Dynamic diagrams with Mermaid](https://www.pressreader.com/australia/linux-format/20210309/281715502348881)." by Mihalis Tsoukalos - source code available at [https://www.linuxformat.com/archives?issue=274](https://www.linuxformat.com/archives?issue=274)  


#### There is also some alternative tooling:  
* Also see Mermaid-Server by Tom Wright [https://github.com/TomWright/mermaid-server](https://github.com/TomWright/mermaid-server)  
