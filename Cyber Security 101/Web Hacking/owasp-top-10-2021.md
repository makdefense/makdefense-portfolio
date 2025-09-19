# [Web Hacking]

**TryHackMe Path**: [Cyber Security 101]  
**Lab Topic**: [OWASP Top 10 - 2021]  
**Date Completed**: [09//2025]

---

## 🧠 Summary

> In this lab, I learned about the importance of understanding 

## 🎯 Objectives
- [ ] Learn about 
   
---

## 🧰 Tools Used
- THM Machine
- 

---

## 📊 Analysis & Screenshots

*** Broken Access Control (IDOR Challenge) ***

> After launching the THM Machine, I was given a task to do an IDOR challenge under the Broken Access Control section. I had to find a flag that was within the other users' notes. To do this i first
opened "Mozilla FireFox" and went to the website "http://10.201.106.172" and used the login credentials of the username "noot" and password "test1234."

> <img width="1036" height="738" alt="owasp1" src="https://github.com/user-attachments/assets/d631af1a-2057-42d9-adff-dbc54529b23a" />

> Then to find the flag i just went to the searchbar in Mozilla FireFox and changed the website from "http://10.201.106.172/note.php?note_id=1" to "http://10.201.106.172/note.php?note_id=0" and it
retrieved the flag of "flag{fivefourthree}"

>  <img width="1080" height="684" alt="owasp2" src="https://github.com/user-attachments/assets/0e213d12-fa97-4894-b305-1dc821ee6119" />

***  Cryptographic Failures (Challenge) ***

> After reading through the Cryptographic Failure section i was then given a challenge to connect to the web application at "http://10.201.48.55:81/" and answer some questions.

> <img width="1098" height="285" alt="owasp3" src="https://github.com/user-attachments/assets/139933b5-0054-44e4-9c00-ed445f973da5" />

> For the first question i had to figure out the name of a specific directory that contained sensitive data in which a developer indicated with a note. To do this i right-clicked on the website and
selected "View Page Source," clicked on "/login.php" and saw that the sensitve data was located within the directory called "/assets."

> <img width="932" height="624" alt="owasp4" src="https://github.com/user-attachments/assets/1b70b5ff-d5a0-48ad-a2cd-1f617eb53470" />

> Next i had to figure out which file that stood out within the directory that would likely contain sensitve information. So what i did was just went to the top of the searchbar and added
"/assets" to the website "http://10.201.48.55:81/," and saw the file that stood out to be called "webapp.db."

> <img width="551" height="443" alt="owasp5" src="https://github.com/user-attachments/assets/d8d9ebee-5b95-448f-951e-519f41df6f58" />

> I then had to use the same file to figure out the password hash of the admin user. To do this i first downloaded the file to the linux terminal by clicking on it in Mozilla FireFox, then went back
to the terminal and inputted the command "sqlite3 webapp.db" to access the sqlite database.

> <img width="787" height="183" alt="owasp6" src="https://github.com/user-attachments/assets/f87f3cde-42f4-48b8-93be-3f8c66649957" />

> I then inputted the command ".tables" to see all the tables within the "webapp.db" databse.

> <img width="171" height="41" alt="owasp7" src="https://github.com/user-attachments/assets/f2cb9894-f044-4e6d-afbe-744976ddd0c1" />

> Next i had to dump all the data from the "users" table by first inputting the command "PRAGMA table_info(users);" to see the information within the table.

> <img width="331" height="96" alt="owasp8" src="https://github.com/user-attachments/assets/c7d849db-7314-49be-b78e-b55d607ee247" />

> Then inputted the command "SELECT * FROM users;" then "enter" to dump the information from the table, and saw that the password hash for the user "admin" was "6eea9b7ef19179a06954edd0f6c05ceb."

> <img width="718" height="131" alt="owasp9" src="https://github.com/user-attachments/assets/9812b4c1-981f-4aca-a954-eccbc21f2bf0" />

> Following, i had to crack the password hash of the user "admin." To do this i just copied and pasted the hash into the free password hash cracker "CrackStation" and clicked submit and saw that the
plaintext password was "qwertyuiop"

> <img width="1128" height="442" alt="owasp10" src="https://github.com/user-attachments/assets/dc2c2070-7f6b-4a29-853d-add4c53974a5" />

> Finally, i had to find a flag within the website "http://10.201.48.55:81/" by using the log in credentials i retrieved for the user "admin."

> <img width="1015" height="410" alt="owasp11" src="https://github.com/user-attachments/assets/76467938-2c13-4012-ba7f-245ea588d777" />

> After inputting the login credentials and clicking login, i retrieved the flag "THM{Yzc2YjdkMjE5N2VjMzNhOTE3NjdiMjdl}."

> <img width="1002" height="407" alt="owasp12" src="https://github.com/user-attachments/assets/bc943869-e6b8-46fb-90c3-01c04c197a2d" />

*** Command Injection ***

> After reading through the Injecton section i was given a practical in the next section called Command Injection. I was tasked to go to the website "http://10.10.17.254:82/" and figure out the
strange text file in the website's root directory. To do this i open Mozilla FireFox and entered the website "http://10.10.17.254:82/" within the search bar and pressed "enter."

> <img width="891" height="551" alt="Screenshot 2025-09-18 at 11 58 13 PM" src="https://github.com/user-attachments/assets/895d650a-bf4f-44c3-9ce5-b7dcd497bab1" />

> Next i inputted the inline command "$(ls)" within the "Enter your inner cow's mooing" text field, clicked "submit," and retrieved the strange text file called "drpepper.txt."

> <img width="890" height="625" alt="owasp14" src="https://github.com/user-attachments/assets/d3c4c536-04c4-49a4-b394-c73fdf2e6460" />

> For the next question i had to figure out how many non-root/non-service/non-daemon users there were. To do this i inputted the inline command "$(cat /etc/passwd)," clicked "submit," and saw that
there were 0 users that were non-root/non-service/non-daemon. I determined this by looking at the end of each user's path and saw "nologin" at everyone of them.

> <img width="978" height="559" alt="owasp15" src="https://github.com/user-attachments/assets/5fb3495d-a6ea-43c8-b788-fad80ba314b0" />

> I then had to figure out which user the app was running as. To figure this out i just entered the inline command "$(whoami)," clicked "submit," and saw that the app was running in the user "apache."

> <img width="1060" height="802" alt="owasp16" src="https://github.com/user-attachments/assets/e2c0fe61-d3d0-4cf3-a3d5-275e363fa36f" />

> I then had to figure out what the user's shell was set as. To figure this out i just inputted the inline command "$(cat /etc/passwd)," clicked "submit," scrolled to the bottom and saw that the shell
set was "/sbin/nologin"

> <img width="847" height="199" alt="owasp17" src="https://github.com/user-attachments/assets/ac4092f3-56ec-47e2-bbe4-381358f59ca3" />

> For the final exercise for this section i had to fiugre out what version of Alpine Linux is running. To figure this out i just inputted the inline command "$(cat /etc/alpine-release)," clicked
"submit," and retrieved the version "3.16.0"

> <img width="925" height="489" alt="owasp18" src="https://github.com/user-attachments/assets/c3b5fec4-ed05-427a-826f-7de7699fb20f" />

*** Insecure Design ***

> Moving on to this section, after reading the material i was given an exercise where i had to reset the user "joseph" password and retrieve a flag after logging into his account. To first carry this
out i first went to website "http://10.10.17.254:85" in Mozilla FireFox.

> <img width="1083" height="746" alt="owasp19" src="https://github.com/user-attachments/assets/73553527-4775-42dc-95eb-d6df151cb775" />

> I then clicked on "I forgot my password...," then entered "joseph" within the username text field, clicked "submit," and then moved on to step 2 which was to select a security question to confirm
my identity.

> <img width="1023" height="635" alt="owasp20" src="https://github.com/user-attachments/assets/e62ae859-1b5a-43c8-a569-726666862cd5" />

> After using the brute-force method by entering every possible color as the answer to the question. I was able to get the password reset after entering the answer "green."

> <img width="1032" height="511" alt="owasp21" src="https://github.com/user-attachments/assets/0c542bed-6773-480f-b9dc-4d560569bb48" />

> Going back to the login area i used the new password to login to joseph's account and saw the "flag.txt" file that contained the flag.

> <img width="817" height="475" alt="owasp22" src="https://github.com/user-attachments/assets/8ab16120-6c9a-4d54-8e71-5025a48f59f5" />

> After opening the "flag.txt" file i ended up retrieving the flag "THM{Not_3ven_c4tz_c0uld_sav3_U!}."

*** Security Misconfiguration ***

> For this section, after reading through the info i was given an exercise where i had to go to a website and try to exploit the security misconfiguration to read the application's source code.
So firstly, i navigated to the website "http://10.10.17.254:86" by inputting it into Mozilla FireFox.

> <img width="795" height="475" alt="owasp24" src="https://github.com/user-attachments/assets/8e6dfbf5-86c8-47e8-a09d-6825e58a5e16" />

> Next, i had to access the Werkzeug console. To do this i just went to the search bar and added "/console" to the website "http://10.10.17.254:86."

> <img width="705" height="374" alt="owasp25" src="https://github.com/user-attachments/assets/b76388e3-a730-4d61-be38-368f24222b6a" />

> I then had to figure out the name of the database file name within the root directory. To do this, since i gained access to the Werkzeug console i inputted the command
"import os; print(os.popen("ls -l").read())," pressed "enter," and retrieved the database file name of "todo.db"

> <img width="801" height="395" alt="owasp26" src="https://github.com/user-attachments/assets/8902ba63-458e-43cc-9725-4b1a6a6b2323" />
> <img width="726" height="405" alt="owasp27" src="https://github.com/user-attachments/assets/3afd26f5-ca93-4b16-b9ae-568c7b8750ec" />

> Next i had to modify the same code to read the contents of the "app.py" file, which had the application's source code, and also contained the value of the "secret_flag" variable within the source code.
So i went ahead and just inputted the command "import os; print(os.popen("cat app.py").read()," pressed "enter," and retrieved the value of "THM{Just_a_tiny_misconfiguration}" for the secret_flag.

> <img width="747" height="224" alt="owasp28" src="https://github.com/user-attachments/assets/92f7f70d-a372-438f-b463-254abfbdb4bf" />

---


## Reflection

> This lab provided me with knowledge and hands-on experience with Burp Suite for web application pentesting.

