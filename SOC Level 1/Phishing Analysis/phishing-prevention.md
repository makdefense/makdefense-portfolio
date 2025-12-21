# [Phishing Analysis]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [Phishing Prevention]  
**Date Completed**: [12/20/2025]

---

## 🧠 Summary

> In this lab, I learned about the importance of understanding core email security controls (SPF, DKIM, DMARC, S/MIME), which are the foundational controls that
protect email authenticity, integrity, and trust. Knowing how they work allows analysts to identify spoofed emails, validate sender legitimacy, detect phishing and BEC attacks,
and accurately investigate suspicious messages. These controls are essential for adequate email security and incident response. Next, I learned about the importance of
understanding SMTP traffic and email content analysis because it allows analysts to detect phishing, spoofing, malware delivery, and data exfiltration by examining how emails are
transmitted and what they contain. This dual visibility helps validate email authenticity, identify malicious behavior, and investigate incidents accurately. Finally, I learned
about the importance of understanding anti-phishing protection measures, which is that they prevent credential theft, malware delivery, and business email compromise by stopping
malicious emails before users interact with them. Knowing how these controls work allows analysts to evaluate why attacks succeed or fail, tune defenses, reduce false positives,
and respond effectively when phishing bypasses protections.

---

## 🎯 Objectives
- [ ] Understand core email security controls (SPF, DKIM, DMARC, S/MIME)
- [ ] Analyze SMTP network traffic and email content
- [ ] Explore anti-phishing protection measures
      
---

## 🧰 Tools Used
- THM AttackBox
- THM Wireshark
  
---

## 📊 Analysis & Screenshots

*** Analyzing SMTP Responses ***

> For this room, after reviewing all the sections, I had to analyze a PCAP file containing SMTP traffic. For the first question, I had to figure out which Wireshark filter can be
used to narrow down the search results based on SMTP response codes. To figure this out, I first had to launch the virtual machine on THM. After launching the virtual machine, I
then opened the "traffic.pcap" file on the virtual machine's desktop.
>
> <img width="389" height="657" alt="pp1" src="https://github.com/user-attachments/assets/50e3d954-1101-426c-add5-6dd034d9033e" />

> I navigated to the top of the Wireshark web application, entered "smtp.response.code" into the input field, and pressed the green arrow on the right. After doing this,
this retrieved all the search results based on "SMTP response codes."
>
> <img width="864" height="539" alt="pp2" src="https://github.com/user-attachments/assets/3ea6953e-7251-453e-b3c2-afc1014c36cc" />

> Moving on to the second question, I had to figure out how many packets in the pcap file contained the SMTP response code "220 Service ready." To figure this out, I navigated to
the top in the Wireshark web application, entered "smtp response code == 220," then pressed the right arrow. This returned 19 packets.
>
> <img width="606" height="310" alt="pp3" src="https://github.com/user-attachments/assets/16e5fee5-ca93-4a27-8c8f-3e488d6d8d1a" />
> <img width="409" height="186" alt="pp4" src="https://github.com/user-attachments/assets/4dae79ba-169a-4049-9db1-52f294ee9ab5" />

> Moving on to the next question, I had to determine the response code the server returned for an email blocked by the domain "spamhaus.org." To figure this out, I
navigated to the top of the Wireshark web application, inputted "smtp" into the input field, then clicked the arrow on the right to return the results. After getting the results,
I searched through all the packets for one that contained "Email" in its info.
>
> <img width="762" height="370" alt="pp5" src="https://github.com/user-attachments/assets/25d4bd8c-ee3b-4d2e-bffc-34c049c5cdcf" />

> After finding the packet that contained the keyword "Email" within its description, I navigated to the bottom, clicked the dropdown "SMTP," and retrieved the response code of
"553" under the "Response" sub-heading. I also had to figure out the whole "Response code:" message, which was "Requested action not taken: mailbox name not allowed (553)."
>
> <img width="894" height="176" alt="pp6" src="https://github.com/user-attachments/assets/7b98fac1-2ae1-4178-9023-3b4cfc3a8ae1" />

> Moving on to the last question in this section, I had to figure out how many messages were blocked for presenting potential security issues. To figure this out, I had to
navigate to the top of the Wireshark web application, then input "smtp.response.code == 552," then click the arrow on the right, which then returned a total of 6 messages that
were blocked for presenting potential security issues.
>
> <img width="773" height="282" alt="pp7" src="https://github.com/user-attachments/assets/25e7b03b-e93d-4aa5-85a1-4f6e064bb553" />
> <img width="407" height="219" alt="pp8" src="https://github.com/user-attachments/assets/4a6e2028-7393-4002-807e-54a58e6cf91f" />

*** Inspecting Emails and Attachments ***

> For this section, I had to utilize the IMF to examine the inner details of emails. For the first question, I had to figure out how many SMTP packets were available for analysis.
To figure this out, I had to navigate to the top of the Wireshark web application, enter "smtp" in the input field, then press the green arrow. After doing this, this
returned a total of "512" SMTP packets available for analysis.
>
> <img width="554" height="300" alt="pp9" src="https://github.com/user-attachments/assets/36c722cd-5e12-47c6-a425-a57f4c17cd7b" />
> <img width="411" height="209" alt="pp10" src="https://github.com/user-attachments/assets/da787aa6-77db-42ce-ad10-0b9baf2d2800" />

> Moving on to the next question, I had to figure out the name of the attachment in packet 270. To figure this out, I navigated through all the SMTP packets to find the packet
number 270, I then clicked the main drop-down menu "SMTP," then the sub-drop-down menu "Line-based text data," scrolled down, and saw the attachment name "document.zip."
>
> <img width="562" height="380" alt="pp11" src="https://github.com/user-attachments/assets/070306d5-e09d-4b28-a5e3-be67de5dafaf" />
> <img width="440" height="242" alt="p12" src="https://github.com/user-attachments/assets/8307b457-eaa7-4ef2-b30c-b520dd631af6" />

> Moving on to the next question, I had to figure out which Host IP address is not responding, making the message undeliverable. To figure this out, I scrolled through
the sub-drop-down menu "Line-based text data," and saw the IP address "212.253.25.152."
>
> <img width="613" height="213" alt="pp13" src="https://github.com/user-attachments/assets/f53d35ab-87a6-4d8d-ab15-ebb74f892117" />

> For the next question, I had to figure out which email client was used to send the message containing the "attachment.scr" by filtering for "imf." To figure this out, I
navigated to the top of the Wireshark web application, then inputted "imf" within the input field, then selected packet number 685, and then navigated to the "Internet Message
Format," clicked it, and retrieved the email client to be "Microsoft Outlook Express 6.00.2600.0000."
>
> <img width="648" height="391" alt="pp14" src="https://github.com/user-attachments/assets/a0946db9-eb7e-440e-9b09-1782ae1d57ef" />
> <img width="795" height="284" alt="pp15" src="https://github.com/user-attachments/assets/261df1f3-01d2-4dba-9649-bee8dc41e6a4" />

> Finally, for the last question, I had to figure out which type of encoding is used for this potentially malicious attachment, which was "attachment.scr." To figure this out, I
navigated further down to the "MIME Multipart Media Encapsulation" drop-down header, then to the "Encapsulated multipart part" sub-drop-down header. After doing this, it
retrieved the type of encoding to be "base64."
>
> <img width="581" height="304" alt="pp16" src="https://github.com/user-attachments/assets/d3af5677-aa09-4ebd-8bb7-dd0966a946d3" />
---

## Reflection

> This lab provided me with knowledge about how to defend against phishing emails.
