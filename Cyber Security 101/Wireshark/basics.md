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
> [Wireshark Exercise.pcapng file packet 38 "markup language"] "https://github.com/makdefense/makdefense-portfolio/blob/main/images/wireshark%20file%20markup%20language.png"
> [Wireshark packet 38 "arrival date"] "https://github.com/makdefense/makdefense-portfolio/blob/main/images/wireshark%20packet%2038%20arrival%20date.png"
> [Wireshark packet 38 "TTL value"] "https://github.com/makdefense/makdefense-portfolio/blob/main/images/wireshark%20packet%2038%20TTL.png"
> [Wireshark packet 38 TCP payload size] "https://github.com/makdefense/makdefense-portfolio/blob/main/images/wireshark%20packet%2038%20TCP%20payload%20size.png"
> [Wireshark packet 38 "e-tag value"] "https://github.com/makdefense/makdefense-portfolio/blob/main/images/wireshark%20packet%2038%20e-tag%20value.png"
> [Wireshark "artist 1" name] "https://github.com/makdefense/makdefense-portfolio/blob/main/images/wireshark%20string%20r4w%20artist%201%20name.png"
> [Wireshark searching for packet 12] "https://github.com/makdefense/makdefense-portfolio/blob/main/images/wireshark%20searching%20for%20packet%2012.png"
> [Wireshark acquiring MD5 Hash by checking packet's comment] "https://github.com/makdefense/makdefense-portfolio/blob/main/images/wireshark%20beginning%20process%20of%20getting%20MD5%20hash.png"
> [Wireshark navigating to packet 39765] "https://github.com/makdefense/makdefense-portfolio/blob/main/images/wireshark%20sleecting%20packet%2039765.png"
> [Wireshark navigating to the properties of downloaded file from packet 39765] "https://github.com/makdefense/makdefense-portfolio/blob/main/images/wireshark%20properties%20of%20answer%20file%20to%20locate%20MD5%20hash.png"
> [Wireshark acquiring MD5 hash value] "https://github.com/makdefense/makdefense-portfolio/blob/main/images/wireshark%20acquiring%20MD5%20hash.png"
> [Wireshark number of warnings for exercise.pcapng file] "https://github.com/makdefense/makdefense-portfolio/blob/main/images/wireshark%20acquiring%20number%20of%20warning%20for%20http.png"
> [Wireshark total number of warnings] "https://github.com/makdefense/makdefense-portfolio/blob/main/images/wireshark%20total%20number%20of%20warnings.png"
> [Wireshark acquiring alien's name by exporting] "https://github.com/makdefense/makdefense-portfolio/blob/main/images/wireshark%20getting%20alien%20name%20by%20exporting%20.png"
> [Wireshark getting note.txt alien file] "https://github.com/makdefense/makdefense-portfolio/blob/main/images/wireshark%20saving%20alien%20note_txt%20file.png"
> [Wireshark saving alien note_txt file to Desktop] "https://github.com/makdefense/makdefense-portfolio/blob/main/images/wireshark%20saving%20alien%20file%20to%20desktop.png"
> [Wireshark opening alien note.txt file to get alien's name] "https://github.com/makdefense/makdefense-portfolio/blob/main/images/wireshark%20aliens%20name.png"


---

## 📊 Analysis

> After launching AttackBox, i then was given a practical to figure out some details for a "pcapng" file. The file name given was "Exercise.pcapng," i had to figure out the file's comments, the total number of
packets, and the SHA256 hash value. To do this i first launch Wireshark, then clicked on the "File" tab on top, then "Open," then selected the "Exercise.pcapng" file, then pressed the "Open" button again.
After opening the file, i then clicked the "Statistics" tab at the top, then pressed "Capture File Properties," this opened up the file's properties which included everything from file details to comments.
I then scrolled down within the "Capture file comments" box to find the hidden flag which was "TryHackMe_Wireshark_Demo," i then scrolled within the "Details" box to find the the total packets captured for
the pcapng file which was under the "Statistics" header. The total packet amount given was "58620," i then had to find the value for SHA256 hash, i did this by scrolling up within the "Details" box and
finding it under the "File" header. The value given was "f446de335565fb0b0ee5e5a3266703c778b2f3dfad7efeaeccb2da5641a6d6eb." Next i had to carry out a packet dissection, by investigating packet 38 of the
"exercise.pcapng file" for specific details. I first had to figure out the type of "markup language" that was used under the HTTP protocol, i did this by first selecting packet number 38, then going to the
left bottom box for "packet details" and saw the type of markup language wasd "eXtensible Markup Language." Next i looked for the arrival date of the packet, i did this by clicking the dropdown of
"HyperText Transfer Protocol" within the packet details box and saw the arrival date was "Thu, 13 May 2004." I then looked for the "TTL value" which is worded out as "Time to live," i did this by clicking
the dropdown of "Internet Protocols Version 4" within the packet details box and saw the "TTL value" was "47." Following i had to find the TCP payload size of the packet, i did this by clicking the dropdown
of the "Transmission Control Protocol" within the packet details box and saw the payload size was "424." Then figuring out the "e-tag value," i had to click again the dropdown of the "HyperText Transfer Protocol"
within the packet detail box and saw the value was "9a01a-4696-7e354b00."
> I was then given another practical to find the name of "artist 1" within a packet's details. To do this i first search for "r4w" string, by clicking the "edit" tab at the top of screen, the selecting "find
packet," and in the searchbar selecting "string" as the search option then inputting the "r4w" value. I then went to the bottom left box to search through the html code to find the artist 1 name which was "r4w8173."
Next, i had to get the MD5 hash for packet 12, i did this by clicking the "Go" at the top of the application, then "Go to Packet," then search for packet "12." I then selected "packet comment" that was in the detail
box in the botton left, then saw i had to go to packet "39765" to get the MD5 hash, so i clicked the "Go" at the top again, then the dropdown "Go to Packet," and inputted "39765," i then right-clicked on
"JPEG File Interchange Format," then clicked on "Export Packet Bytes," and save the file as "answer." I then right clicked on the "answer" file which was saved on the desktop and click on "properties," then
left clicked all the way to "digests," selected "MD5," clicked "hash" button and got the value of "911cd574a42865a956ccde2d04495ebf." Next, i had to find an alien's name within the capture file, to do this i
clicked "Flie" at the top, then "Export Objects," then sleected "HTTP," then within the "Text Filter" bar i inputted "txt" to narrow the files down to txt files. I then selected the "txt" file and saved it to
the Desktop, i then open the "note.txt" file and scrolled to find the alien's name which was "packetmaster." I then had to find the number of warning for the capture file, to do this i clicked the "Analyze" at
the top, then clicked "Expert Information," and saw that the total warning labelled in yellow were "1636."
> 
 ---

## Reflection

> This lab provided me with knowledge about 
