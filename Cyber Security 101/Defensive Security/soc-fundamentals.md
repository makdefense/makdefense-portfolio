# [Offensive Security Tooling]

**TryHackMe Path**: [Cyber Security 101]  
**Lab Topic**: [SOC Fundamentals]  
**Date Completed**: [09//2025]

---

## 🧠 Summary

> In this lab, I learned about the importance of understanding building a baseline for SOC, which is that it tells you what "normal" looks like, so you can reliably spot anomalies, reduce noise,
prioritize incidents, investigate faster, and prove whether something is malicious or expected. Next, I learned about the importance of understanding detection and response in SOC, which is how
organizations find attackers who bypass prevention and stop them before they cause significant damage. If you can't detect or respond effectively, branches linger, ramp up in impact, and cost far more to
contain. Finally, I learned about the importance of the roles of people, processes, and technology, which are the three pillars that make systems actually work (or fail). Learning how
each contributes - and how they must align - is essential to building secure, reliable, and resilient organizations.

---

## 🎯 Objectives
- [ ] Learn about Building a baseline for SOC (Security Operations Center)
- [ ] Learn about Detection and response in SOC
- [ ] Learn about The role of People, Processes, and Technology
      
---

## 🧰 Tools Used
- THM Site
  
---

## 📊 Analysis & Screenshots

*** Practical Exercise ***

> After reading through the SOC fundamentals sections, I was given a task at the end to do a practical exercise of SOC. I was given a scenario to take the role of a SOC Analyst Level 1 of an organization
to view the logs of a port scanning activity that has been observed on one of the hosts in the network, and to answer questions about the 5 Ws. First, I launched the site that contained the SIEM alerts
and saw the "Port Scanning Activity Detected from IP: 10.0.0.8," which was basically the answer to the first question: "What: Activity that triggered the alert?"
>
> <img width="831" height="385" alt="soc1" src="https://github.com/user-attachments/assets/cc0d6d02-24a6-4d11-81f3-6d74c2ae6dce" />

> For the next question, I had to figure out "When: Time of the activity?" Which was "Jun 12 2024 17:24"
> The next question was to determine "Where: Destination host IP?" Which was "10.0.0.3"
> Then had to figure out "Who: Source host name?" Which was "Nessus"
> I then had to figure out "Why: Reason for the activity? Intended/Malicious?" Which was considered "Intended."
>
> <img width="1100" height="522" alt="soc2" src="https://github.com/user-attachments/assets/c72e4c5d-a876-481b-bd07-3e86e57b3bb9" />
> <img width="667" height="583" alt="soc3" src="https://github.com/user-attachments/assets/547df50e-5549-4f76-8c4b-2e49ddca41fc" />

> After closing out the alert, I retrieved the flag "THM{000_INTRO_TO_SOC}."
>
> <img width="618" height="417" alt="soc4" src="https://github.com/user-attachments/assets/85938f73-c7f4-45b8-9c47-3d52fdd32f60" />

---

## Reflection

> This lab provided me with knowledge about the SOC team and their processes.
