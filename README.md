# Shade-WriteUp
Shade Ransomware Analysis
[ZooKeeper.pdf](https://github.com/repins762/Shade-WriteUp/files/3862035/ZooKeeper.pdf)
In the spring of 2019 there was US uptick of this 2014 Ransomware normally found in Russia
![Done](https://user-images.githubusercontent.com/42683298/69119278-4be3b900-0a53-11ea-80db-21f1c1a9ad84.png)

Windows Defender wouldn't even download the zip-file without disabling features. First indicator found was it trying to find it's external IP address. Shade also will delete volume snapshots while spawning a lot of processes. It will query kernel debugger information along with process information. Envirnmentally it will query CPU information, read the active computer name and the crypto machine GUID. Shade Creates new processes and drops executable files. It sends HTTP traffic on typical outbound ports, but without headers. 

It will will use a common user agent found on common browsers, even though a browser was not launched. 

Found user agent(s): Mozilla/5.0 (Windows NT 6.0; rv:34.0) Gecko/20100101 Firefox/34.0

The It can register a top-level exception handler for anti-debugging.It also installs hooks.

"2019-10-15-Shade-ransomware-EXE-retrieved-by-JS-file.exe" wrote bytes "711175027a3b7402ab8b02007f950200fc8c0200729602006cc805001ecd71027d267102" to virtual address "0x756807E4" (part of module "USER32.DLL")
"2019-10-15-Shade-ransomware-EXE-retrieved-by-JS-file.exe" wrote bytes "7d07db7781edd977ae86d877c6e0d777effdda772d16d9776014db77478dd877a8e2d7776089d87700000000ad37a5758b2da575b641a57500000000" to virtual address "0x74D31000" (part of module "WSHTCPIP.DLL")
"2019-10-15-Shade-ransomware-EXE-retrieved-by-JS-file.exe" wrote bytes "c0dfd7771cf9d677ccf8d6770d64d87700000000c0114d7700000000fc3e4d7700000000e0134d77000000009457787525e0d777c6e0d77700000000bc6a777500000000cf314d770000000093197875000000002c324d7700000000" to virtual address "0x75651000" (part of module "NSI.DLL")
"cmd.exe" wrote bytes "711175027a3b7402ab8b02007f950200fc8c0200729602006cc805001ecd71027d267102" to virtual address "0x756807E4" (part of module "USER32.DLL")
"chcp.com" wrote bytes "711175027a3b7402ab8b02007f950200fc8c0200729602006cc805001ecd71027d267102" to virtual address "0x756807E4" (part of module "USER32.DLL")

It drops files marked as "clean"

Antivirus vendors marked dropped file "CHCP.COM.5DBB585C.bin" as clean (type is "PE32 executable (console) Intel 80386 for MS Windows"), Antivirus vendors marked dropped file "CHCP.COM.5DBB5FB4.bin" as clean (type is "PE32 executable (console) Intel 80386 for MS Windows")
 
 Shade opens the Kernel Security Device Driver (KsecDD) of Windows
 "2019-10-15-Shade-ransomware-EXE-retrieved-by-JS-file.exe" opened "\Device\KsecDD"
"vssadmin.exe" opened "\Device\KsecDD"

 

![malware_blockedDL](https://user-images.githubusercontent.com/42683298/69119389-a54be800-0a53-11ea-97dc-8671d5ce067e.png)

Inital findings that were interesting from pcaps after intial file execution 

![malware_checking_connections](https://user-images.githubusercontent.com/42683298/69119465-ea701a00-0a53-11ea-8acb-2025905219eb.png)

![not_good](https://user-images.githubusercontent.com/42683298/69119473-ef34ce00-0a53-11ea-826f-5cc3dd23cbd8.png)

Some IOCs found were the use of uncommon ports 9001 9101

![port_9001](https://user-images.githubusercontent.com/42683298/69119636-75511480-0a54-11ea-9d9b-0182c6f4b591.png)
