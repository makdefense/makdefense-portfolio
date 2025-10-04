# [Defensive Security Tooling]

**TryHackMe Path**: [Cyber Security 101]  
**Lab Topic**: [FlareVM: Arsenal of Tools]  
**Date Completed**: [10/04/2025]

---

## 🧠 Summary

> In this lab, I learned about the importance of understanding 

---

## 🎯 Objectives
- [ ] Learn 

---

## 🧰 Tools Used
- THM Windows
- THM Flare VM
  
---

## 📊 Analysis & Screenshots

*** Commonly Used Tools For Investigation: Overview ***

> After reading the sections within FlareVM: Arsenal of Tools i was given my task under "Commonly Used Tools for Investigation: Overview" section. I had to figure out under which process we could find
"smss.exe" by using the "procexp" tool. To figure this out i first launched the "procexp" tool from the "Desktop," and saw that the "smss.exe" was under the process "System."

> <img width="447" height="286" alt="fvm1" src="https://github.com/user-attachments/assets/530433ab-f9da-4da7-9136-b1636681df73" />

> I then had to figure out the sha256 value of the file "cryptominer.bin" that was kept in the Desktop\Sample folder using PEStudio. To figure this out i first went to the Desktop, double-clicked on
"Sample" folder to open it, and selected the "cryptominer.bin" file.

> <img width="212" height="191" alt="fvm2" src="https://github.com/user-attachments/assets/374833ef-7a8c-46f6-b088-09cc3535eeec" />
> <img width="672" height="399" alt="fvm3" src="https://github.com/user-attachments/assets/96809c18-be42-4c88-a086-573e9b8ae8d8" />

> I then opened the "PEStudio" application and dragged the "cryptominer.bin" file into the application and saw that the sha256 value was "E9627EBAAC562067759681DCEBA8DDE8D83B1D813AF8181948C549E342F67C0E."

> <img width="1084" height="328" alt="fvm4" src="https://github.com/user-attachments/assets/621b60b5-3ad9-4b99-ac21-d0707d1bfff8" />

> I then had to figure out how many functions did the same exact file "cryptominer.bin" have. To figure this out i kept the "PEStudio" application open and navigated to the left and selected the
"functions" sections. After selecting that section i retrieved a total of "102" functions.

> <img width="487" height="423" alt="fvm5" src="https://github.com/user-attachments/assets/90c67114-bc45-4f4b-a35a-1755deee502b" />

> Next i had to figure out the MD5 of a file named "possible_medusa.txt" which was held in the Desktop\Sample folder using the CFF explorer application. So to figure this out i opened the "Sample"
folder that was on the Desktop and selected the "possible_medusa.txt" file.

> <img width="725" height="423" alt="fvm6" src="https://github.com/user-attachments/assets/5013af0e-743a-4974-b9ee-3d2f0ae18042" />

> I then opened the CFF explorer application, dragged the "possible_medusa.txt" file into the application and saw that the MD5 value was "646698572AFBBF24F50EC5681FEB2DB7."

> <img width="656" height="485" alt="fvm7" src="https://github.com/user-attachments/assets/e0fd304d-b1a0-4a46-b528-2072325a26c3" />

> Next i had to figure out the "e_magic value" of the same "possible_medusa.txt" file by using the same application so to do this i just navigated to the left of the application and selected "DOS Header"
section and saw that the "e_magic value" was "5A4D."

> <img width="705" height="271" alt="fvm8" src="https://github.com/user-attachments/assets/a3202b27-8325-4a71-8edb-858c66d54f22" />

*** Analyzing Malicious Files! ***

> For my next practical, i had first figure out the "entropy value" of the "windows.exe" file. To figure this out i first had to navigate to the Desktop, then double-click on the "Sample" folder, then
select the "windows.exe" file.

> <img width="752" height="425" alt="fvm9" src="https://github.com/user-attachments/assets/1763e62f-bd1a-45f9-b6ab-ee29ae3e54a1" />

> I then had to open "PEStudio" application and drag the "windows.exe" file into the application which returned the "entropy value" of "7.999."

> <img width="968" height="415" alt="fvm10" src="https://github.com/user-attachments/assets/5b691dd5-241b-4391-81ea-0dab8080b2d2" />

> I then had to figure out the value under "requestedExecutionLevel" of the same "windows.exe" file. To figure this out i kept the "PEStudio" application open, navigated to the "administrator section,"
scrolled through the script and saw that the value under "requestedExecutionLevel" was "requireAdministrator."

> <img width="993" height="287" alt="fvm11" src="https://github.com/user-attachments/assets/a84eb147-b899-406e-b266-9296f98c2ba7" />

> Moving on, i had to figure out the Imphash of "cobaltstrike.exe." To figure this out i first had to navigate back to the "Sample" folder and select the "cobaltstrike.exe" file, then dragged the file into
the "PEStudio" application and retrieved the "Imphash" of "92EEF189FB188C541CBD83AC8BA4ACF5."

> <img width="831" height="525" alt="fvm12" src="https://github.com/user-attachments/assets/03869f24-fe5d-4507-bace-17669b6bc0c8" />

> I then had to figure out both the defanged IP address to which the process "cobaltstrike.exe" is connecting, and the destination port number used by "cobaltstrike.exe" when connecting to its C2
IP address. To fiugre this out i first had to navigate to the Desktop, double-click on the "Sample" folder, then double-click on the "cobaltstrike_capture.pcapng" file, which opened up the "Wireshark"
application, i then navigated to the top of the application, selected "Display Filters," selected the "+" icon to add a filter. After selecting the "+" icon i added a filter that contained
"ip.addr == 47.120.46.210" as the expression. The reason why i added that specific IP address was because that was the IP address to which the process "cobaltstrike.exe" is connecting as shown in the
process monitor application. So the defanged IP address was "47[.]120[.]46[.]210."

> <img width="694" height="540" alt="fvm15" src="https://github.com/user-attachments/assets/78efe95b-d1e1-45ce-812a-1d8d8a1fc992" />
> <img width="788" height="205" alt="fvm13" src="https://github.com/user-attachments/assets/a9633444-884e-4b39-8a27-dcbd79742a82" />

> To retrive the destination port number i then went back to "Wireshark" and navigated to the top of the application, selected the top input field and entered the filter i created earlier which was
"ip.addr == 47.120.46.210" to filter out all the packets for packets containing only this filter expression. After clicking the "Go" button the destination port number that was returned was "81."

> <img width="744" height="249" alt="fvm14" src="https://github.com/user-attachments/assets/1512e748-fd45-47db-a3f0-d45de42014a1" />

> For the last question i had figure out the parent process of "cobaltstrike.exe." To figure this out i simply just launched the "Process Explorer" application, went back to the "Sample" folder,
double-clicked on the "cobaltstrike.exe" file, went back to the "Process Explorer," and saw that the parent process of "cobaltstrike.exe" was "explorer.exe."

> <img width="1008" height="187" alt="fvm16" src="https://github.com/user-attachments/assets/afdf4ba8-becf-498c-aa57-bf34097a7e09" />

---

## Reflection

> This lab provided me with knowledge about 

