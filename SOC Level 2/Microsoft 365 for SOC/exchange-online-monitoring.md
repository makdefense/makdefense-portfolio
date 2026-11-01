# [Microsoft 365 for SOC]

**TryHackMe Path**: [SOC Level 2]  
**Lab Topic**: [Exchange Online Monitoring]  
**Date Completed**: [11/01/2026]

**Lab Link**: [https://tryhackme.com/room/exchangeonlinemonitoring]

---

## 🧠 Summary

> In this lab, I learned about common cyberattacks targeting Microsoft Exchange Online and how Security Operations Center (SOC) analysts detect, investigate, and respond to these
threats. I explored various attack techniques, including email account compromise, phishing, malicious inbox rules, unauthorized email forwarding, and abuse of mailbox permissions. I
also gained a deeper understanding of how attackers exploit compromised accounts to access sensitive information, maintain persistence, and potentially move further within an
organization's environment. Additionally, I learned how to analyze Exchange Online audit logs, mailbox activities, and suspicious email-related events to identify indicators of
compromise and detect unauthorized actions.

---

## 🎯 Objectives

- [ ] Understand how Exchange Online generates logs and where to find them
- [ ] Identify suspicious mailbox rules creation and email forwarding
- [ ] Detect phishing campaigns launched from compromised mailboxes
- [ ] Use message trace and audit logs to scope an incident
- [ ] Investigate a real-world Exchange Online compromise

---


## 🧰 Tools Used
- THM AttackBox
- Splunk

---

## 📊 Analysis & Screenshots

*** Exchange Online Logging ***

> For this section, I had to answer a series of questions related to Microsoft Exchange Online logging. For the first question, I had to identify the appDisplayName value that confirms a
user accessed their Exchange Online mailbox. Upon reviewing the provided reading material, I was able to determine that the appDisplayName value was "One Outlook Web."
>
> <img width="762" height="596" alt="1" src="https://github.com/user-attachments/assets/88619ac2-b8ad-4f04-89dd-ac16c3a448be" />
> <img width="2092" height="660" alt="2" src="https://github.com/user-attachments/assets/b352ce68-38f5-4831-b979-a3a50ae0235a" />

> For the next question, I had to identify which Microsoft Exchange Online feature attackers can abuse to automatically delete replies to phishing emails. Upon further review of the
provided reading material, I was able to determine that the feature was New-InboxRule, which allows users to create automated rules for managing incoming emails. Attackers can exploit
this functionality to automatically delete or move email responses to phishing messages, potentially concealing malicious activity and preventing legitimate users from noticing
suspicious communications within their mailboxes.
>
> <img width="535" height="320" alt="3" src="https://github.com/user-attachments/assets/ab52aa5b-a014-4ea6-9a5c-4c75e7c55115" />

*** Detecting Mailbox Rule Abuse ***

> Moving on to this section, I was tasked with utilizing a Splunk instance to conduct an investigation and answer a series of questions related to suspicious activity within Microsoft
Exchange Online. For the first question, I had to identify the suspicious inbox rule created by a user to automatically forward emails to an external email address. Upon further
investigation, using the appropriate Splunk query, I was able to identify the suspicious inbox rule as "Cleanup." This finding suggested that the rule may have been created to redirect
incoming emails to an external address, potentially allowing an attacker to access sensitive information and exfiltrate confidential communications without the legitimate user's
knowledge.
>
> <img width="1614" height="592" alt="4" src="https://github.com/user-attachments/assets/19c41c39-853d-467f-af93-8d0b62e137c1" />

> For the next question, I had to identify the specific keyword in the email subject line that triggered the suspicious forwarding inbox rule. Upon further investigation of the Splunk
logs, I was able to determine that the keyword was "Verify." This finding indicated that the inbox rule was configured to automatically forward emails containing this keyword in their
subject lines to an external email address, potentially allowing the attacker to intercept sensitive communications without the legitimate user's knowledge.
>
> <img width="1024" height="453" alt="6" src="https://github.com/user-attachments/assets/1c01014e-c0ef-4634-b493-36585819761c" />

> For the next question, I had to identify the external email address to which messages were being forwarded by the suspicious inbox rule. Upon further investigation of the Splunk logs,
I was able to determine that the destination email address was d4ruy6g@protonmail.com. This finding indicated that the inbox rule was configured to forward matching emails to an external
mailbox, potentially allowing the attacker to intercept sensitive information and exfiltrate confidential communications without the legitimate user's knowledge.
>
> <img width="2558" height="954" alt="5" src="https://github.com/user-attachments/assets/4b8d968e-8836-4db3-bb1d-f46e2709b4f1" />

*** Detecting Phishing From Compromised Mailbox ***

> Moving on to this section, I was tasked with conducting an investigation using another index within the Splunk instance and answering a series of questions related to suspicious email
activity. For the first question, I had to identify the subject line of a suspicious email received by a colleague. Upon further investigation of the Splunk logs, I was able to determine
that the subject line was "Urgent: Verify Your Account." Additionally, I identified that two colleagues had received the same phishing email, suggesting that the attacker was targeting
multiple users within the organization in an attempt to obtain sensitive information or compromise their accounts.
>
> <img width="2467" height="552" alt="7" src="https://github.com/user-attachments/assets/6f8924bd-ede1-43c8-9aae-548a7d3ab3ef" />

> For the next question, I had to identify the IP address from which the suspicious phishing emails originated. Upon further investigation of the Splunk logs, I was able to determine
that the source IP address was 190.2.149.93. This finding helped identify the origin of the suspicious email activity and provided a potential indicator of compromise (IOC) that could be
used to investigate related phishing attempts and detect additional malicious activity within the organization's environment.
>
> <img width="2559" height="592" alt="8 " src="https://github.com/user-attachments/assets/d481ed07-85ad-4017-843a-1241fa366869" />

*** Incident Investigation ***

> For this final section, I was tasked with conducting a comprehensive investigation into an unusual sign-in attempt from the perspective of a Level 2 Security Operations Center (SOC)
Analyst. Following the investigation, I had to answer a series of questions related to the suspicious authentication activity. For the first question, I had to identify the city from
which the malicious sign-in originated. Upon further investigation, using the appropriate Splunk query, I was able to determine that the sign-in was associated with Ursynów, Warsaw,
Poland. This finding helped establish the geographic origin of the suspicious authentication attempt and provided valuable context for identifying potential unauthorized access to the
compromised account.
>
> <img width="2320" height="494" alt="9" src="https://github.com/user-attachments/assets/2e7c95f4-c758-4456-bafb-2d064b636d05" />

> For the next question, I had to identify the name of the suspicious inbox rule created by the attacker within the compromised user's Exchange Online mailbox. Upon further investigation
of the Splunk logs, I was able to determine that the suspicious inbox rule was named "Maintenance." This finding suggested that the attacker may have created the rule to manipulate
incoming emails, conceal malicious activity, or maintain unauthorized access to sensitive communications within the compromised mailbox.
>
> <img width="1851" height="600" alt="10" src="https://github.com/user-attachments/assets/826ef985-c18b-4bc1-a4d2-655629e7d0eb" />

> For the next question, I had to identify the external email address configured by the attacker for automatic email forwarding within the compromised user's Exchange Online mailbox.
Upon further investigation of the Splunk logs, I was able to determine that the email address specified in the ForwardingSmtpAddress property was x7tpq2m@protonmail.com. This finding
indicated that the attacker had configured email forwarding to an external mailbox, potentially allowing sensitive communications and confidential organizational information to be
exfiltrated without the legitimate user's knowledge.
>
> <img width="1824" height="560" alt="11" src="https://github.com/user-attachments/assets/19465a5f-863c-407e-be52-d756e09aac77" />

> For the next question, I had to identify the subject line of the phishing email received by Robert's colleague. Upon further investigation of the Splunk logs, I was able to determine
that the subject line was "Action Required: Password Reset." This finding suggested that the attacker was attempting to deceive the recipient into taking immediate action by disguising
the phishing email as a legitimate password reset notification, potentially leading to credential theft or unauthorized access to the recipient's account.
>
> <img width="1613" height="575" alt="12" src="https://github.com/user-attachments/assets/ea2b5d60-baa4-4374-b1e4-7a8dd5bb687d" />

> For the next question, I had to identify the IP address used by the attacker to send phishing emails while connected to a Virtual Private Network (VPN). Upon further investigation of
the Splunk logs, I was able to determine that the source IP address was 138.199.21.211. This finding indicated that the attacker was using a VPN to potentially conceal their actual IP
address and geographic location while conducting the phishing campaign. Identifying this IP address provided a valuable indicator of compromise (IOC) that could assist security analysts
in detecting related malicious activity and investigating additional phishing attempts within the organization's environment.
>
> <img width="647" height="300" alt="13" src="https://github.com/user-attachments/assets/86394d5a-90d9-483d-9c7e-de10d1045f4c" />

> For the next question, I had to identify the user who responded to the phishing email sent by the attacker. Upon further investigation of the Splunk logs, I was able to determine that
the email address associated with the user who replied was emma.clarke@techcorp.thm. This finding indicated that the recipient had interacted with the phishing email, potentially
exposing them to further social engineering attempts or credential theft. Identifying the responding user provided valuable information for assessing the potential impact of the phishing
campaign and determining whether additional investigation was necessary.
>
> <img width="957" height="510" alt="14" src="https://github.com/user-attachments/assets/0d8c521a-d18e-40e7-b8e6-6ec8565e8afc" />

---

## Reflection

> This lab strengthened my understanding of Microsoft 365 email security, cloud-based threat detection, and the importance of monitoring Exchange Online activities to investigate
potential security incidents and protect organizational communications.
