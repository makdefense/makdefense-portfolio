# [Defensive Security]

**TryHackMe Path**: [Cyber Security 101]  
**Lab Topic**: [Digital Forensics Fundamentals]  
**Date Completed**: [09/27/2025]

---

## 🧠 Summary

> In this lab, I learned about the importance of understanding the phases of digital forensics, which serve as a roadmap for reliable, legally defensible, and effective investigations. Learning them makes
sure you preserve evidence, prove what happened, act quickly during incidents, and produce reports that stand up to legal or regulatory scrutiny. Next, I learned about the importance of understanding the
types of digital forensics, which is that different incidents leave different kinds of evidence in different places - learning the types of digital forensics lets you pick the proper techniques, preserve
admissible evidence, and investigate effectively whether the target is a laptop, a smartphone, a cloud service, or a network stream. I then learned about the importance of understanding the procedure
of evidence acquisition, which is that evidence acquisition is the moment when an incident becomes provable. If you don't collect and preserve data correctly, you lose irreplaceable artifacts, break
legal admissibility, wreck timelines, and make investigation or remediation impossible. Knowing the proper procedure ensures that investigations are credible, repeatable, and effective. Finally, I learned
about the importance of understanding Windows forensics, which is that Windows is everywhere in enterprise environments and user endpoints, so learning Windows forensics gives you the skills to find,
preserve, and explain what happened in the vast majority of real-world incidents - from malware and data theft to insider misuse and compliance investigations.

---

## 🎯 Objectives
- [ ] Learn about Phases of digital forensics
- [ ] Learn about Types of digital forensics
- [ ] Learn about Procedure of evidence acquisition
- [ ] Learn about Windows forensics
      
---

## 🧰 Tools Used
- THM AttackBox
- Google Maps
  
---

## 📊 Analysis & Screenshots

*** Practical Example of Digital Forensics ***

> After reading through the Digital Forensics Fundamentals sections, I was given a practical to complete at the end. I had to first find out the name of the author of a PDF file within a directory
"/root/Rooms/introdigitalforensics." To do so, I first navigated to the directory by launching the terminal within THM AttackBox and inputting the command "cd /root/Rooms/introdigitalforensics."
Then, I pressed "enter."

> <img width="860" height="535" alt="df1" src="https://github.com/user-attachments/assets/c3ac88c7-0025-4f18-af8d-07710fb88a89" />

> Next, I input the command "pdfinfo ransom-letter.pdf" and then pressed "Enter," which gave me the author's name, "Ann Gree Shepherd."

> <img width="776" height="414" alt="df2" src="https://github.com/user-attachments/assets/cf5cf7cf-c971-40c5-b127-8c6b2948c05c" />

> For the next question, I had to determine where the kidnappers took the image they attached to the document, specifically the name of the street. To do this, I input the command
"exiftool letter-image.jpg," then "enter," which then gave me the GPS position of "51 deg 30' 51.90" N, 0 deg 5' 38.73" W," I then went to "Google Maps," entered "51° 30' 51.90" N, 0° 5' 38.73" W"
into the search bar and retrieved "Milk Street" for the street name.

> <img width="704" height="159" alt="df4" src="https://github.com/user-attachments/assets/9edb2c4f-2f15-4118-94e3-932e22988cd2" />
> <img width="409" height="503" alt="df5" src="https://github.com/user-attachments/assets/9844b143-1798-4460-8f5c-f87aa455715f" />

> For the last question, I had to figure out the model name of the camera used to take the photo. To do this, I went back to the Terminal in AttackBox and input the command
"exiftool letter-image.jpg | grep Camera," then "enter," this retrieved the Camera name "Canon EOS R6."

> <img width="922" height="166" alt="df6" src="https://github.com/user-attachments/assets/3bc2f992-3425-47bf-81cb-aafcddf41274" />

---

## Reflection

> This lab provided me with knowledge about digital forensics, related processes, and a practical example of digital forensics.
