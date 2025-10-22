# [Cyber Threat Intelligence]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [Yara]  
**Date Completed**: [10//2025]

---

## 🧠 Summary

> In this lab, I learned about the importance of understanding 

---

## 🎯 Objectives
- [ ] Learn about 

---

## 🧰 Tools Used
- THM AttackBox
- 
  
---

## 📊 Analysis & Screenshots

*** Using LOKI and its Yara rule set ***

> After reading the sections within the Yara THM room, I was given my first task within the "Using LOKI and its Yara rule set" section. For my first question, I had to play the role of a security analyst
for a mid-size law firm and scan suspicious files on a web server within my organization. I had to first scan "file1", which was located within the "suspicious-files" directory, and I had to figure out
if Loki detected the file as suspicious/malicious or benign. To do this, I first launched the Yara VM and waited for it to load up. After the VM loaded, I then navigated to the "suspicious-files"
directory by inputting the command "cd suspicious-files," then "enter," then "cd file1," then "enter." To run the scan, I entered the command syntax "python ../../tools/Loki/loki.py -p ." and then
pressed "Enter."

> <img width="974" height="135" alt="yara1" src="https://github.com/user-attachments/assets/c27a5cce-085e-4a00-8940-ee60beb2c69d" />

> After running the scan, the results from Loki indicated that the file was suspicious.

> <img width="794" height="93" alt="yara6" src="https://github.com/user-attachments/assets/7cc8a997-a48d-4bac-ac14-cc9a77c0a566" />

> I then had to determine the Yara rule that the file matched. To figure this out, I just navigated through the scan results and saw that it was matched on "webshell_metaslsoft."

> <img width="620" height="26" alt="yara8" src="https://github.com/user-attachments/assets/8504fc61-694a-43b2-b1d5-7ce56c1118af" />

> I then had to figure out the classification of the file by Loki. To determine this, I navigated through the scan results and found that it was classified as a "Web Shell."

> <img width="578" height="25" alt="yara7" src="https://github.com/user-attachments/assets/1e3a1135-ce15-4dd0-8ea0-a36a63ae2a71" />

> Next, I had to determine which string within the Yara rule the output matched. To figure this out, I reviewed the scanned output and saw that the string was "Str1."

> <img width="912" height="30" alt="yara9" src="https://github.com/user-attachments/assets/6da04ed7-3162-42cb-afb5-8971ffac03cc" />

> I then had to figure out the name and version of the hack tool. To figure this out, I looked through the scanned output and saw that the name and version were "b374k 2.2", which was stored within
"FIRST_BYTES."

> <img width="807" height="30" alt="yara10" src="https://github.com/user-attachments/assets/f46af42a-83aa-4932-a356-ded37211e9c8" />

> I then had to inspect the actual Yara file that flagged file one and determine how many strings were present to flag the file. After viewing the Yara file, I discovered that there was one string to flag
file 1.

> Next, I had to scan file 2, which was located within the same "suspicious-files" directory, and determine whether Loki classified the file as suspicious/malicious or benign. To figure this out, I 
input the command "cd files2," then "enter," then "python ../../tools/Loki/loki.py -p ." then "enter."

> <img width="875" height="137" alt="yara11" src="https://github.com/user-attachments/assets/3f7b1ba6-8302-4f18-a573-fa9f0c56d070" />

> After initiating the scan and completing it, the results showed that the file was OK.

> <img width="813" height="105" alt="yara12" src="https://github.com/user-attachments/assets/10b24d90-f3e9-41f1-aa49-6cc7765cc2ce" />

> For the last question of this practical, I had to inspect "file2" and figure out the name and version of the web shell. To go about this, I first inputted the command "cat 1ndex.php," then "enter,"
then "more cat 1ndex.php," then "enter." This then returned the name and version of the webshell to be "b374k 3.2.3."

> <img width="1098" height="329" alt="yara5" src="https://github.com/user-attachments/assets/a8faa245-9ac6-438a-a78a-fdcc352846b5" />

*** Creating Yara rules with yarGen *** 

> For my next task, I first had to generate a rule for "file2" that was in the "suspicious-files" directory. To do so, I had to first navigate to the directory "/tools/yarGen," then input the command
"python3_yarGen.py -m /home/cmnatic/suspicious-files/file2 --excludegood -o /home/cmnatic/suspicious-files/file2.yar," then "enter." 

> <img width="1108" height="51" alt="yara13" src="https://github.com/user-attachments/assets/f25bdade-d703-4223-95a0-502fa0724cd5" />

> This then created the rule for "file2."

> <img width="743" height="69" alt="yara14" src="https://github.com/user-attachments/assets/9dcae51f-52da-4452-9de7-0e092fa0f146" />

> Moving on to the first question of this practical, I had to determine which command to use to test Yara and my rule against file two from within the root of the suspicious files directory.
To carry out the test, I had to first navigate to the "suspicious-files" directory, then input the command syntax
"yara file2.yar file2/1ndex.php home_cmnatic_suspicious_files_file2_1ndex file2/1ndex. php," then "enter."

> <img width="778" height="65" alt="yara15" src="https://github.com/user-attachments/assets/03327b6c-04d7-46ef-ac59-c117736992ad" />

> I then had to copy the rule I created into the Loki signatures directory. To do so, I navigated back to the main root directory, then input the command
"mv /home/cmnatic/suspicious-files/files2.yar /home/cmnatic/tools/Loki/signature-base/yara/," then "enter."

> <img width="1213" height="62" alt="yara16" src="https://github.com/user-attachments/assets/31017356-ca74-413b-864f-1ce2ab1c225e" />

> I then had to test the rule with Loki to see if it flags file 2. After running the test, it was confirmed that it does flag file 2.

> <img width="1110" height="189" alt="yara17" src="https://github.com/user-attachments/assets/b5d0e2ef-0c17-46ba-8dcd-654dde1c86c1" />

> For the next question, I had to determine the name of the variable that matched the string. To figure this out, I scrolled down to the scan results and saw that the variable name
was "Zepto."

> <img width="895" height="179" alt="yara18" src="https://github.com/user-attachments/assets/5b08ea06-763d-4c11-b0ee-8b12c76e7e8c" />

> I then had to figure out how many strings were generated. To figure this out, I exited the Loki scan, then navigated to the directory "signature-base" that was in the "tools" directory, inputted the
command "nano file2.yar," then "enter."

> <img width="786" height="38" alt="yara19" src="https://github.com/user-attachments/assets/9c22d080-e40a-42b8-bccc-9075c64cf3ed" />

> After entering the nano editor for "file2.yar," it was discovered that there were a total of 20 strings.

> <img width="288" height="125" alt="yara20" src="https://github.com/user-attachments/assets/bc452d82-80c6-4d2f-9343-51146f9d4e5c" />

> For the final question of this practical, I had to determine one of the conditions to match on the Yara rule, specifically the file size. After scrolling through the nano editor for
"file2.yar", it was discovered that the file must be less than 700KB to match the YARA rule.

> <img width="519" height="70" alt="yara21" src="https://github.com/user-attachments/assets/219a7dac-5dab-409b-bfec-9e3a9f768ca3" />

*** Valhalla *** 

> For the final practical in this room, I had to use an online program called "Valhalla." For the first question, I had to figure out if "file 1" was attributed to an APT group by entering its SHA256
hash into "Valhalla." So I first ran a scan on "file 1" using the command syntax "python ../../tools/Loki/loki.py -p ." to grab the SHA256 hash value of
"5479f8cd1375364770df36e5a18262480a8f9d311e8eedb2c2390ecb233852ad."

> <img width="755" height="191" alt="v1" src="https://github.com/user-attachments/assets/80738e96-0421-476e-a3fa-b8058d219d6e" />

> After running the scan and retrieving the SHA256 hash value for "file 1," I then copied and pasted it into "Valhalla," clicked "search," and saw that, in fact, it is attributed to an APT group.

> <img width="1251" height="740" alt="v2" src="https://github.com/user-attachments/assets/d2823b1b-4388-4861-8eaf-54041563a3e5" />
> <img width="1159" height="682" alt="v3" src="https://github.com/user-attachments/assets/0f0b68f6-a89f-4c04-ba83-1f73bbf76f33" />

> For the next question, I had to determine the name of the first Yara rule that detects "file 2." To figure this out, I followed the same approach I used for "file 1." I retrieved the SHA256 hash value
of "53fe44b4753874f079a936325d1fdc9b1691956a29c3aaf8643cdbd49f5984bf."

> <img width="848" height="144" alt="v4" src="https://github.com/user-attachments/assets/58131d75-eb88-4a6d-a282-e9fb822242c5" />

> After retrieving the SHA256 hash value, I copied and pasted it into "Valhalla," clicked the search button, and retrieved the name of the first Yara rule, "Webshell_b374k_rule1."

> <img width="1189" height="655" alt="v5" src="https://github.com/user-attachments/assets/296d52fe-2e2d-4494-8eb4-b7c36182aa4d" />

> Moving on to the next question, I had to determine which scanner the Yara Signature Match was from by examining the information for "file 2" on VirusTotal. So after reviewing the information
on VirusTotal for "file 2," I saw the Yara Signature Match to be from "THOR APT Scanner."

> <img width="831" height="432" alt="v6" src="https://github.com/user-attachments/assets/6fbc45b6-bb39-4980-b493-fd9f6ac2975d" />

> I then had to see if every AV detected the SHA256 hash of "file 2" as malicious. After scanning the information, I noticed that not every AV detected the SHA256 hash of "file 2" as malicious.

> <img width="828" height="505" alt="v7" src="https://github.com/user-attachments/assets/d9314b96-51e6-4fdb-9cac-af2a4c87c293" />

> I then had to figure out what other extension was recorded for "file 2" other than ".PHP." To figure this out, I scanned through the information provided by Virus Total and saw that the other
the extension recorded was "EXE."

> <img width="612" height="75" alt="v8" src="https://github.com/user-attachments/assets/7fc40996-7b96-44a1-a0d4-b8c5a0d9d3d9" />

> Next, I had to figure out what JavaScript library was used by "file 2." To figure this out, I went back to the search results of "file 2" SHA256 hash value on "Valhalla" and saw
the first GitHub link, clicked it, scrolled through the info within the "index.php" file, and saw the library used by "file 2" to be Zepto.

> <img width="827" height="193" alt="v10" src="https://github.com/user-attachments/assets/9b509328-0ed1-4081-97d6-b3a2920b0726" />

---

## Reflection

> This lab provided me with knowledge about 
