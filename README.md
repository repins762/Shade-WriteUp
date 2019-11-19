# Shade-WriteUp
Shade Ransomware Analysis
[ZooKeeper.pdf](https://github.com/repins762/Shade-WriteUp/files/3862035/ZooKeeper.pdf)
In the spring of 2019 there was US uptick of this 2014 Ransomware normally found in Russia
![Done](https://user-images.githubusercontent.com/42683298/69119278-4be3b900-0a53-11ea-80db-21f1c1a9ad84.png)

Windows Defender wouldn't even download the zip-file without disabling features. First indicator found was it trying to find it's external IP address. Shade also will delete volume snapshots while spawning a lot of processes. It will query kernel debugger information along with process information. Envirnmentally it will query CPU information, read the active computer name and the crypto machine GUID. Shade Creates new processes and drops executable files. It sends HTTP traffic on typical outbound ports, but without headers. 

![mitre](https://user-images.githubusercontent.com/42683298/69119483-f8259f80-0a53-11ea-8fa2-d16cb81debcd.png)

It will will use a common user agent found on common browsers, even though a browser was not launched. 

Found user agent(s): Mozilla/5.0 (Windows NT 6.0; rv:34.0) Gecko/20100101 Firefox/34.0

The It can register a top-level exception handler for anti-debugging.It also installs hooks.
It drops files marked as "clean". Shade opens the Kernel Security Device Driver (KsecDD) of Windows
 
![malware_blockedDL](https://user-images.githubusercontent.com/42683298/69119389-a54be800-0a53-11ea-97dc-8671d5ce067e.png)

Inital findings that were interesting from pcaps after intial file execution 

![malware_checking_connections](https://user-images.githubusercontent.com/42683298/69119465-ea701a00-0a53-11ea-8acb-2025905219eb.png)

![not_good](https://user-images.githubusercontent.com/42683298/69119473-ef34ce00-0a53-11ea-826f-5cc3dd23cbd8.png)

Some IOCs found were the use of uncommon ports 9001 9101

![port_9001](https://user-images.githubusercontent.com/42683298/69119636-75511480-0a54-11ea-9d9b-0182c6f4b591.png)
