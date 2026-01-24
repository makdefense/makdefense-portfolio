# [Network Traffic Analysis]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [NetworkMiner]  
**Date Completed**: [01/24/2026]

---

## 🧠 Summary

> In this lab, I learned the importance of using NetworkMiner to analyze recorded traffic files and practice network forensic activities. This process teaches you how attacks
typically unfold on a network, prepares you for real incident response scenarios, and helps build the investigative mindset required of effective cybersecurity professionals.

---

## 🎯 Objectives
- [ ] Discover what NetworkMiner is
- [ ] Learn the basics of NetworkMiner
- [ ] Explore the different information tabs and extract information efficiently

---

## 🧰 Tools Used
- THM AttackBox
- THM Network Miner

---

## 📊 Analysis & Screenshots

*** Exercises ***

> For this room, I learned about NetworkMiner by reading through all the sections and then applying that knowledge in practice. I opened the ~/Desktop/Exercise Files/case1.pcap
file and investigated it to answer the first five questions.

> <img width="331" height="239" alt="1" src="https://github.com/user-attachments/assets/0afbc81d-2d8d-4866-8b82-6b8433c61051" />
> <img width="635" height="224" alt="2" src="https://github.com/user-attachments/assets/42d3ad62-7566-4ed3-8a05-b72fee272442" />
> <img width="498" height="257" alt="3" src="https://github.com/user-attachments/assets/c7e3d4ec-3932-4c9f-a550-d5d708a2bf5e" />
> <img width="641" height="463" alt="4" src="https://github.com/user-attachments/assets/45c6fca1-7317-46c3-8acc-e6905a018228" />

> For the first question, I had to determine the operating system of the host 131.151.37.122. To do this, after launching the file, I navigated to the Hosts tab, located the host
131.151.37.122, and expanded its drop-down menu. I then expanded the OS: Windows section, which revealed the operating system as Windows – Windows NT 4.

> <img width="595" height="227" alt="5" src="https://github.com/user-attachments/assets/7ba32750-b4e9-44df-b7a4-dcd31df42333" />

> For the second question, I had to investigate the hosts 131.151.37.122 and 131.151.32.91 and determine how many bytes were received from host 131.151.32.91 to host
131.151.37.122 through port 1065. To do this, I navigated further down the host details, expanded the Incoming sessions: 2 drop-down menu, and observed that the total number of
bytes received was 192.

> <img width="799" height="94" alt="6" src="https://github.com/user-attachments/assets/5448a402-e531-4ca1-a0f1-caa56597cf15" />

> Moving on to the third question, I investigated the hosts 131.151.37.122 and 131.151.32.21 to determine how many bytes were sent from host 131.151.37.122 to host 131.151.32.21
through port 143. To do this, I navigated to the Hosts tab, expanded the drop-down menu for 131.151.32.21, and then expanded the Outgoing sessions: 1 section, where I observed
that the total number of bytes sent was 20,769.

> <img width="646" height="263" alt="7" src="https://github.com/user-attachments/assets/21f6f8d9-931f-43f7-a020-4ca66741ff2a" />

> Moving on to the fourth question, I had to determine the sequence number of frame 9. To do this, I returned to the desktop, launched NetworkMiner version 1.6.1, and opened the
same ~/Desktop/Exercise Files/case1.pcap file. I then navigated to the Frames tab, expanded the drop-down menu for Frame 9, and selected TCP, which revealed the sequence number
2AD77400.

> <img width="709" height="183" alt="8" src="https://github.com/user-attachments/assets/164dcb28-a81a-453e-9df8-37e6ac91fed6" />
> <img width="469" height="161" alt="9" src="https://github.com/user-attachments/assets/f80de387-b477-4f74-8e76-dbf9b7fe151c" />
> <img width="448" height="208" alt="10" src="https://github.com/user-attachments/assets/49c20051-1fdb-4ced-b050-9955ef65018e" />
> <img width="407" height="373" alt="11" src="https://github.com/user-attachments/assets/27dfc117-d002-4b3e-9c8a-5c3fd06c8e5a" />

> Moving on to the final question for this file, I had to determine the number of detected content types. To do this, I navigated to the Files tab and, within the filter area on
the right side of the application, selected Details. I then scrolled down to the results section, where I observed that the total number of detected content types was 2.

> <img width="272" height="204" alt="12" src="https://github.com/user-attachments/assets/84db5384-6718-4273-ad77-d8069f7d04c9" />
> <img width="348" height="84" alt="13" src="https://github.com/user-attachments/assets/8f0d6a5e-2642-41d0-b042-08c31f723c6e" />

> Moving on to the next set of questions, I used the ~/Desktop/Exercise Files/case2.pcap file to answer them.

> <img width="404" height="185" alt="14" src="https://github.com/user-attachments/assets/33b8ea0c-991c-4c74-921c-e8c311b87900" />
> <img width="715" height="537" alt="15" src="https://github.com/user-attachments/assets/9218e4d0-3d01-4df4-91fa-4ef925819103" />

> For the first question, I had to determine the USB product’s brand name. To do this, I navigated to the Files tab, investigated the results, and identified the USB product’s
brand name as ASIX.

> <img width="798" height="131" alt="16" src="https://github.com/user-attachments/assets/b8e21b6d-7272-409a-bf30-a57c9279b255" />

> For the next question related to this file, I had to determine the phone model name. To do this, I navigated to the Images tab and reviewed the available images. I identified an
image that appeared to depict a cell phone, right-clicked on it, and selected Open Image, which revealed the phone model as Lumia 535.

> <img width="474" height="269" alt="17" src="https://github.com/user-attachments/assets/976bbd4f-86c6-4d15-8731-cb2f7c1c8cec" />
> <img width="594" height="329" alt="18" src="https://github.com/user-attachments/assets/c92bbf9b-e43b-482d-8120-a971c87be2cd" />

> For the next question, I had to determine the source IP address of the fish image. To do this, I navigated through the Images tab, located the image depicting a fish, selected
it, and identified the source IP address as 50.22.95.9.

> <img width="1190" height="196" alt="19" src="https://github.com/user-attachments/assets/353dd8ca-9aaa-478b-92cf-f67f26fbac9b" />

> Moving on to the second-to-last question for this file, I had to determine the password for homer.pwned.se@gmx.com. To do this, I navigated to the Credentials tab, reviewed the
results, and identified the password as spring2015.

> <img width="851" height="291" alt="20" src="https://github.com/user-attachments/assets/d88e7d10-d524-4ba6-88a2-4824f6cb5da4" />

> For the final question, I had to determine the DNS query of frame 62001. To do this, I navigated to the DNS tab, entered 62001 into the filter input field, selected Frame nr. as
the search criterion, and observed that the DNS query was pop.gmx.com.

> <img width="1190" height="115" alt="21" src="https://github.com/user-attachments/assets/faf67a26-5029-4cd4-aad4-064125fc9549" />
> <img width="573" height="188" alt="22" src="https://github.com/user-attachments/assets/01d729c4-8290-4950-b577-b2c6af031c12" />

---

## Reflection

> This lab provided me with knowledge on how to use NetworkMiner to analyze recorded traffic files, and practice network forensic activities.
