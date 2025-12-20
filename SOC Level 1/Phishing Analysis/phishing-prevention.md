# [Phishing Analysis]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [Phishing Prevention]  
**Date Completed**: [12/20/2025]

---

## 🧠 Summary

> In this lab, I learned about the importance of understanding 

---

## 🎯 Objectives
- [ ] 
      
---

## 🧰 Tools Used
- THM AttackBox
  
---

## 📊 Analysis & Screenshots

*** Analyzing SMTP Responses ***

> For this room, after going through all the sections i had to analyze a PCAP file with SMTP traffic. For the first question i had to figure out which Wireshark filter can be used
to narrow down the search results based on SMTP response codes. To figure this out i had to first launch the virtual machine on THM. After launching the virtual machine i then
opened the "traffic.pcap" file on the virtual machine's desktop.
>
> <img width="389" height="657" alt="pp1" src="https://github.com/user-attachments/assets/50e3d954-1101-426c-add5-6dd034d9033e" />

> I then navigated to the top of the Wireshark web application, then entered "smtp.response.code" into the input field, then pressed the green arrow on the left. After doing this,
this retrieved all the search results based on "SMTP response codes."
>
> <img width="864" height="539" alt="pp2" src="https://github.com/user-attachments/assets/3ea6953e-7251-453e-b3c2-afc1014c36cc" />

> Moving onto the second question i had to figure how many packets in the pcap file contained the SMTP response code "220 Service ready." To figure this out i navigated to the top
of the Wireshark web application, then inputted "smtp response code == 220," then pressed the arrow on the right, After doing this, this returned a total of 19 packets.
>
> <img width="606" height="310" alt="pp3" src="https://github.com/user-attachments/assets/16e5fee5-ca93-4a27-8c8f-3e488d6d8d1a" />
> <img width="409" height="186" alt="pp4" src="https://github.com/user-attachments/assets/4dae79ba-169a-4049-9db1-52f294ee9ab5" />

> Moving onto the next question i had to figure out the response code that the server returned for an email that was blocked by domain "spamhaus.org." To figure this out i
navigated to the top of the Wireshark web application, inputted "smtp" into the input field, then clicked the arrow on the right to return the results. After getting the results
i searched through all of the packets for one packet that contained "Email" within its info.
>
> <img width="762" height="370" alt="pp5" src="https://github.com/user-attachments/assets/25d4bd8c-ee3b-4d2e-bffc-34c049c5cdcf" />

> After finding the packet that contained the keyword "Email" within its description i navigated to the bottom, clicked the dropdown "SMTP," and retrieved the response code of
"553" under the "Response" sub-heading. I also had to figure out the full "Response code:" message, which was "Requested action not taken: mailbox name not allowed (553)."
>
> <img width="894" height="176" alt="pp6" src="https://github.com/user-attachments/assets/7b98fac1-2ae1-4178-9023-3b4cfc3a8ae1" />

> Moving onto the last question of this section i had to figure out how many messages were blocked for presenting potential security issues. To figure this out i had to
navigate to the top of Wireshark web application, then input "smtp.response.code == 552," then click the arrow on the right, which then returned a total of 6 messages that were
blocked for presenting potential security issues.
>
> <img width="773" height="282" alt="pp7" src="https://github.com/user-attachments/assets/25e7b03b-e93d-4aa5-85a1-4f6e064bb553" />
> <img width="407" height="219" alt="pp8" src="https://github.com/user-attachments/assets/4a6e2028-7393-4002-807e-54a58e6cf91f" />

*** Inspecting Emails and Attachments ***

> For this section, i had to utilize IMF to examine the inner details of emails. For the first question, i had to figure out how many SMTP packets were available for analysis.
To figure this out i had to navigate to the top of the Wireshark web application, then input "smtp" into the input field, then press the green arrow. After doing this, this
returned a total of "512" SMTP packets available for analysis.
>
> <img width="554" height="300" alt="pp9" src="https://github.com/user-attachments/assets/36c722cd-5e12-47c6-a425-a57f4c17cd7b" />
> <img width="411" height="209" alt="pp10" src="https://github.com/user-attachments/assets/da787aa6-77db-42ce-ad10-0b9baf2d2800" />

>











---

## Reflection

> This lab provided me with knowledge about 
