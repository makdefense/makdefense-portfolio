# [Microsoft 365 for SOC]

**TryHackMe Path**: [SOC Level 2]  
**Lab Topic**: [Entra ID Monitoring]  
**Date Completed**: [10/29/2026]

**Lab Link**: [https://tryhackme.com/room/entraidmonitoring]

---

## 🧠 Summary

> In this lab, I learned about the main security threats and defensive measures within Microsoft Entra ID environments, focusing on how security analysts detect, investigate, and respond
to identity-based attacks. I explored common threats such as password spraying, brute-force attacks, credential theft, account compromise, and privilege escalation. I also gained a
better understanding of how attackers exploit authentication mechanisms, misconfigured permissions, and identity management weaknesses to gain unauthorized access. Additionally, I
learned how to analyze Entra ID sign-in logs, audit logs, and other security events to identify suspicious activities and potential indicators of compromise.

---

## 🎯 Objectives

- [ ] Understand common attack techniques targeting Entra ID identities.
- [ ] Understand how Entra ID security features can help prevent or detect these attacks.
- [ ] Learn how to use Sign-in and Audit logs to detect each technique.

---


## 🧰 Tools Used
- THM AttackBox
- Splunk

---

## 📊 Analysis & Screenshots

*** Password-Based Attacks ***

> For this section, I had to investigate Splunk logs containing evidence of brute-force and password-spraying attacks, then answer a series of questions related to the investigation. For
the first question, I had to determine which IP address was responsible for performing the password-spraying attack. Upon further investigation, I was able to identify the IP address
associated with this suspicious activity as:

94.20.222.248
>
> <img width="825" height="483" alt="1" src="https://github.com/user-attachments/assets/b1498b44-3164-4144-a416-487e8db05c85" />
> <img width="1253" height="632" alt="2" src="https://github.com/user-attachments/assets/58e267c5-fefe-44f5-a2cb-01c165bd887c" />

> For the next question, I had to identify the IP address responsible for performing a throttled brute-force attack. Upon further investigation, I was able to determine that the IP
address associated with this suspicious activity was:

38.165.231.218
>
> <img width="1492" height="578" alt="3" src="https://github.com/user-attachments/assets/91153edc-5834-44da-9c41-c85a33ef4749" />

> For the final question in this section, I had to identify the email address associated with the user account that was compromised during the attack. Upon further investigation, I was
able to determine that the compromised account's email address was:

amanda.costa@finegalo.thm
>
> <img width="1446" height="1159" alt="4" src="https://github.com/user-attachments/assets/21464513-aa32-4d27-9789-8cbcc440e77a" />
> <img width="900" height="545" alt="5" src="https://github.com/user-attachments/assets/75e9b88d-92d7-464f-9b33-a000962d1855" />


*** Conditional Access Policies & Identity Protection ***

> Moving on to this section, I was tasked with investigating Splunk logs to assess the risks associated with suspicious sign-in attempts and user accounts. Following the investigation, I
had to answer a series of questions related to my findings. For the first question, I had to identify the email address associated with the user account flagged as risky within the
tenant. Upon further investigation, I was able to identify the email address as allan.senna@finegalo.thm. Additionally, I determined that the most recent risky sign-in attempt associated
with this account occurred on March 3, 2026, at 13:51. Finally, by analyzing the risk detection logs, I identified the risk type as anonymizedIPAddress, indicating that the sign-in
attempt originated from an anonymized IP address, which could suggest an attempt to conceal the user's actual location or identity.
>
> <img width="2560" height="764" alt="6" src="https://github.com/user-attachments/assets/9bcdc809-16ae-40b0-804b-9c818174785f" />

> For the next question, I had to identify the name of the Conditional Access Policy (CAP) that was enforced to block suspicious sign-in attempts associated with the risky user account.
Upon further investigation, I determined that the policy responsible for blocking these attempts was "Block Suspicious Countries." Additionally, I analyzed the sign-in logs to identify
the IP address associated with the blocked authentication attempt. I was able to determine that the IP address was 94.20.222.251, indicating that the Conditional Access Policy
successfully prevented a potentially unauthorized sign-in attempt from this address.
> <img width="2560" height="851" alt="7" src="https://github.com/user-attachments/assets/0d653dbd-6aca-42db-9637-b39f93783c55" />


*** MFA Bypass Techniques ***

> For this section, I was tasked with investigating an attempted Multi-Factor Authentication (MFA) bypass attack by analyzing Splunk logs and answering a series of questions related to
the investigation. For the first question, I had to identify the user account targeted by an MFA fatigue attack. Upon further investigation, I was able to determine that the targeted
account was igor.bicalho@finegalo.thm. Additionally, I analyzed the authentication logs and identified the error code associated with the failed MFA prompts as 500121, indicating that
the MFA authentication requests were unsuccessful. Finally, I examined the user's previous sign-in activity to determine the country from which the user typically authenticated before
the attack. I identified the country code as DK (Denmark), establishing a baseline for the user's normal sign-in location and helping distinguish legitimate authentication activity from
potentially malicious attempts.
>
> <img width="1891" height="683" alt="8" src="https://github.com/user-attachments/assets/ad0f1c25-a966-4c79-811c-8e7fb9c882dc" />

> For the next question, I had to determine the approximate date and time when the attacker successfully authenticated to the targeted user account following the MFA fatigue attack. Upon
further investigation of the Splunk authentication logs, I was able to identify that the attacker successfully signed in to the compromised account on March 4, 2026, at approximately
13:26. This finding indicated that the attacker had successfully bypassed the MFA protection and gained unauthorized access to the user's account.
>
> <img width="448" height="296" alt="9" src="https://github.com/user-attachments/assets/1f9dd4b4-dca4-4b3e-9e26-1fa03078b0ef" />

*** Privilege Escalation & Persistence ***

> For this section, I was tasked with continuing my investigation from the previous section by analyzing Splunk logs to identify post-compromise activity associated with the compromised
user account. Following the investigation, I had to answer a series of questions related to my findings. For the first question, I had to determine the email address of the new user
account created by the attacker. Upon further investigation, I was able to identify the newly created account as rafael.maciel@finegalo.thm. Additionally, I examined the account's
assigned permissions and discovered that it had been granted the Global Administrator role. This finding indicated that the attacker had created a highly privileged account, potentially
establishing persistence and maintaining administrative control over the compromised Microsoft Entra ID environment.
>
> <img width="2512" height="565" alt="10" src="https://github.com/user-attachments/assets/ca9099c3-6a79-400e-a62d-39a0013ef1b2" />

> For the next question, I had to determine the approximate date and time when the attacker registered a new Multi-Factor Authentication (MFA) device on the compromised account. Upon
further investigation of the Splunk logs, I was able to identify that the attacker added a new MFA device on March 4, 2026, at approximately 13:36. This activity suggested that the
attacker was attempting to establish persistence by registering an additional authentication method, potentially allowing continued unauthorized access to the compromised account.
>
> <img width="1601" height="631" alt="11" src="https://github.com/user-attachments/assets/7dd1b143-393c-4a3c-a6ca-335e60504761" />

*** OAuth Application Abuse ***

> For this final section, I was tasked with reviewing the provided reading materials and answering a series of questions related to application permissions within Microsoft Entra ID. For
the first question, I had to identify the permission that allows an application to read all mailboxes within a tenant. Upon reviewing the material, I was able to determine that the
permission was Mail.Read.All, which can grant an application access to read email messages across user mailboxes when configured with application-level permissions and the required
administrative consent. This permission is particularly sensitive because, if misused or granted to a malicious application, it could expose confidential email communications and
sensitive organizational information.
>
> <img width="614" height="220" alt="12" src="https://github.com/user-attachments/assets/773d6c2e-d240-4af3-a420-3cf1a1ce4bd8" />

> For the next question, I had to identify the activityDisplayName value used to track application consent grants within Microsoft Entra ID audit logs. Upon reviewing the provided
material, I was able to determine that the value was "Consent to application." This audit event allows security analysts to monitor consent granted to applications, identify potentially
suspicious permission requests, and investigate unauthorized application access. Understanding how to track these events is essential for detecting malicious OAuth applications and
preventing attackers from gaining unauthorized access to sensitive organizational data.

---

## Reflection

> This lab strengthened my understanding of identity security, threat detection, and the importance of implementing effective defensive measures to protect cloud-based environments from
unauthorized access and malicious activity.
