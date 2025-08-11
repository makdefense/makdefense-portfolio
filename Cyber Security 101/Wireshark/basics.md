# [Networking]

**TryHackMe Path**: [Cyber Security 101]  
**Lab Topic**: [Wireshark: The Basics]  
**Date Completed**: [08//2025]

---

## 🧠 Summary

> In this lab, I learned about the importance of understanding 


---

## 🎯 Objectives
- [ ] 
      

---

## 🧰 Tools Used
- THM AttackBox
- THM Wireshark
  
---

## 📸 Screenshots

> [Wireshark Launch] "https://github.com/makdefense/makdefense-portfolio/blob/main/images/wireshark%20launch.png"
> [Wireshark opening Exercise.pcapng file] "https://github.com/makdefense/makdefense-portfolio/blob/main/images/wireshark%20opening%20exercise%20file.png"
> [Wireshark opening Exercise.pcapng file properties] "https://github.com/makdefense/makdefense-portfolio/blob/main/images/wireshark%20opening%20file%20porperties.png"
> [Wireshark capturing flag within the file comments] "https://github.com/makdefense/makdefense-portfolio/blob/main/images/wireshark%20finding%20flag%20in%20file%20comments.png"
> [Wireshark figuring out file's packet amount] "https://github.com/makdefense/makdefense-portfolio/blob/main/images/wireshark%20exercise%20file%20packet%20amount.png"
> [Wireshark figuring out file's SHA256 hash value] "https://github.com/makdefense/makdefense-portfolio/blob/main/images/wireshark%20file%20SHA256%20hash%20value.png"


---

## 📊 Analysis

> After launching AttackBox, i then was given a practical to figure out some details for a "pcapng" file. The file name given was "Exercise.pcapng," i had to figure out the file's comments, the total number of
packets, and the SHA256 hash value. To do this i first launch Wireshark, then clicked on the "File" tab on top, then "Open," then selected the "Exercise.pcapng" file, then pressed the "Open" button again.
After opening the file, i then clicked the "Statistics" tab at the top, then pressed "Capture File Properties," this opened up the file's properties which included everything from file details to comments.
I then scrolled down within the "Capture file comments" box to find the hidden flag which was "TryHackMe_Wireshark_Demo," i then scrolled within the "Details" box to find the the total packets captured for
the pcapng file which was under the "Statistics" header. The total packet amount given was "58620," i then had to find the value for SHA256 hash, i did this by scrolling up within the "Details" box and
finding it under the "File" header. The value given was "f446de335565fb0b0ee5e5a3266703c778b2f3dfad7efeaeccb2da5641a6d6eb."
 
---

## Reflection

> This lab provided me with knowledge about 
