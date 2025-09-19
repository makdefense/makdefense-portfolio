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

*** Vulnerable and Outdated Components *** 

> After going through the readings of Vulnerable and Outdated Components i waas given a lab where i had to go to a website and exploit it to capture a flag. I first had to navigate to
"http://10.201.6.90:84" by searching it in Mozilla FireFox.

> <img width="926" height="705" alt="owasp29" src="https://github.com/user-attachments/assets/f598d150-e62e-4d86-a2bd-b5890fdf01ae" />

> After launching the website i had to go online to "exploit.db" to find specific code to exploit the "CSE online bookstore" site. I did this by just googling "cse bookstore exploit," then clicked the
first result to retrieve the code for the exploit.

> <img width="697" height="258" alt="owasp30" src="https://github.com/user-attachments/assets/81a2021f-290a-4cb0-b52e-92cefc0db12f" />
> <img width="1623" height="297" alt="owasp31" src="https://github.com/user-attachments/assets/4a3ed80c-12a3-4295-acdb-c552c718ec02" />
> <img width="1853" height="899" alt="owasp32" src="https://github.com/user-attachments/assets/7fe6e573-ceda-4254-a7f9-882e4ea43b5b" />

> To carry out the exploit i went back to my Linux terminal and inputted the command "nano exploit.py" to add the exploit code to the "exploit.py" file.

> <img width="770" height="518" alt="owasp33" src="https://github.com/user-attachments/assets/016b100f-77bb-44ec-834c-2b157ec9a9d3" />

> After saving the code within the "exploit.py" file and exiting nano i then gave the file permission by inputting the command "chmod +x exploit.py," then "enter," then retrieved the shell by
inputting the command "python3 exploit.py http://10.201.6.90:84/," then "enter," then "y" to launch the shell.

> <img width="725" height="210" alt="owasp34" src="https://github.com/user-attachments/assets/5a65bab3-efef-4284-8938-09d5b533a91f" />

> To then capture the flag i had to input the command "cat /opt/flag.txt," then "enter," which retrieved the flag "THM{But_1ts_n0t_my_f4ult!}."

> <img width="345" height="95" alt="owasp35" src="https://github.com/user-attachments/assets/86ba08d8-81f1-44b3-becd-be34ff6924f4" />

*** Identification and Authentication Failures ***

> For the next section "Identification and Authentication Failures" after reading through the info i was given a practical to go to website "http://10.201.6.90:8088" to retrieve flags from two users
"darren" & "arthur" by re-creating their accounts starting with an additional space. Firstly, i navigated to the website "http://10.201.6.90:8088" on Mozilla FireFox.

> <img width="1096" height="638" alt="owasp36" src="https://github.com/user-attachments/assets/1fb15e03-5552-4a88-a79a-54684990caa0" />

> After trying to register "darren" without the additional space at the beginning i ran into an issue.

> <img width="873" height="742" alt="owasp37" src="https://github.com/user-attachments/assets/48581206-283d-44c9-a9c7-c3aff7602caa" />
> <img width="954" height="405" alt="owasp38" src="https://github.com/user-attachments/assets/d7aa659b-f258-4dac-ba17-84950c4f01da" />

> I then tried re-registering "darren" with the additional space at the beginning and was successful.

> <img width="716" height="660" alt="owasp39" src="https://github.com/user-attachments/assets/3e3c3598-da21-4f15-ab49-e5149c3ee05d" />

> After using the credentials i used to re-create the "darren" account and logged in, i retrieved the first flag which was "fe86079416a21a3c99937fea8874b667"

> <img width="603" height="333" alt="owasp40" src="https://github.com/user-attachments/assets/9b84d0d8-5f70-4386-992b-65d8e8c6e89f" />

> I repeated the same actions for the user account "arthur."

> <img width="892" height="341" alt="owasp41" src="https://github.com/user-attachments/assets/0581f9fa-6909-489a-ad48-3e55417fa967" />

> After logging into the "arthur" account with the credentials i used to re-register the account i retrieved the flag "d9ac0f7db4fda460ac3edeb75d75e16e"

> <img width="660" height="326" alt="owasp42" src="https://github.com/user-attachments/assets/55bb1ead-903f-4e20-8884-d704a747f206" />

*** Software and Data Integrity Failure ***

> For the next section "Software and Data Integrity Failure" after reading through the info i was given a practical under "Software Integrity Failures" to go to figure out the SHA-256 hash of
"https://code.jquery.com/jquery-1.12.4.min.js." To do this i went on a SRI Hash Generator website and inputted the website "https://code.jquery.com/jquery-1.12.4.min.js" into the text field, selected SHA-
256, and clicked "Hash!" This retrieved the SHA-256 hash value of "sha256-ZosEbRLbNQzLpnKIkEdrPv7lOy9C27hHQ+Xp8a4MxAQ="

> <img width="1248" height="392" alt="owasp43" src="https://github.com/user-attachments/assets/49532f14-090a-43d3-bd88-bc8224dffe89" />
> <img width="1316" height="534" alt="owasp44" src="https://github.com/user-attachments/assets/434c13eb-74b1-4007-bc2e-6c9afe2d95fb" />

> Moving on to the practical given under "Data Integrity Failures," i had to retrieve a flag from a website by modifying the JWT Token so the site thinks im the user "admin." So first i navigated to
the website "http://10.201.6.90:8089/," tried to log in as a guest first but was given a prompt to use "guest" for the password after entering no password.

> <img width="530" height="665" alt="owasp45" src="https://github.com/user-attachments/assets/991c035b-b108-45c4-8e08-04cbbfab2fee" />

> After entering the credentials "guest" for the username and "guest" for the password, i was able to log into the guest user but was given another prompt in terms of retrieving the flag.

> <img width="700" height="272" alt="owasp46" src="https://github.com/user-attachments/assets/9bca7e1c-bef7-49ec-a532-0c5c20995663" />

> So my next step to try and retrieve the flag was to right-click on the website and click "inspect," then select the "cookies" tab to then get the JWT that was stored as a cookie in my browser.

> <img width="866" height="477" alt="owasp47" src="https://github.com/user-attachments/assets/85a70dea-9394-4a27-b060-1a4be292a12e" />

> After retrieving the JWT i went to an online JWT encoder, copied and pasted the token into the text field to retrieve the "header" and "payload."

> <img width="1037" height="720" alt="owasp48" src="https://github.com/user-attachments/assets/d5b0a005-42ca-4b25-90f3-afd7a440ce90" />

> After retrieving this i then went to the "header" box and changed the "alg" value to "none" so i could be able to delete the JWT's signature. I then also changed the "username" value from "guest"
to "admin" so that the JWT could change to reflect that i am an admin user when i go back to the cookies4all site and replace the JWT.

> <img width="1021" height="702" alt="owasp49" src="https://github.com/user-attachments/assets/e397a705-d59e-44b1-b326-21daa9fbd096" />

> After switching the JWT to "eyJ0eXAiOiJKV1QiLCJhbGciOiJub25lIn0.eyJ1c2VybmFtZSI6ImFkbWluIiwiZXhwIjoxNzU4Mjk5NTE2fQ." within the JWT-session in the website i refreshed the page and retrieved
the flag "THM{Dont_take_cookies_from_strangers}"

> <img width="1584" height="689" alt="owasp50" src="https://github.com/user-attachments/assets/cfb1944c-1a86-4749-b927-254319800c55" />

*** Security Logging and Monitoring Failures ***

> After going through the information within "Security Logging and Monitoring Failures" section i had to analyze a provided sample log file. I had t first figure out the IP address of the attacker.
To figure this out i first downloaded the log file onto my computer, then opened it. After examining the log file i saw the attacker's IP address to be "49.99.13.16" because the attacker tried to
login as  the admin and was flagged as unauthorized.

> <img width="618" height="284" alt="owasp51" src="https://github.com/user-attachments/assets/6c9ec143-721e-4397-9f16-dab5d9c91ff6" />

> After seeing numerous attempts to login to the system i came to the conclusion that the attacker used the "brute-force" method to attack the system.

*** Server-Side Request Forgery (SSRF) *** 

> For the final vulnerability in OWASP which was SSRF, after reading through the information i was given a practical to navigate to a website and answer a few questions. For the first question i had
to figure out the only host that was allowed to access the admin area. To do this i first opened Mozilla FireFox and navigated to the website "http://10.201.6.219:8087/"

> <img width="1156" height="726" alt="owasp52" src="https://github.com/user-attachments/assets/1fc89c9c-f47d-4726-9009-4111aea422b6" />

> I then navigated to the "admin" tab and clicked it and saw that only the "localhost" can access it.

> <img width="592" height="246" alt="owasp53" src="https://github.com/user-attachments/assets/0494d3fb-3d16-4776-9217-b72ec5371b58" />

> I then had to figure out where does the server parameter point to after checking the "Download Resume" button. After clicking the button i saw that it pointed to "secure-file-storage.com."

> <img width="992" height="593" alt="owasp54" src="https://github.com/user-attachments/assets/5b7887fd-9d63-4493-a0b0-5e28ac07bb82" />
> <img width="649" height="158" alt="owasp55" src="https://github.com/user-attachments/assets/222d0227-f529-494d-a203-7a96a70757c4" />

> Next i had to SSRF to get the application to send the request to my AttackBox Terminal instead of the "secure file storage" to see if there were any API keys in the intercepted request. To do this
i first had to open the terminal and input the command "nc -lvp 4444" to begin listening on porrt 4444 to recieve the request.

> <img width="553" height="222" alt="owasp56" src="https://github.com/user-attachments/assets/f70b7520-6465-4dc5-bafa-70b194c6f2c2" />

> I then opened another tab within the terminal and inputted the command "ip a," then "enter" to figure out my IP address for the AttackBox terminal. I saw that the IP address was "10.201.44.115"

> <img width="582" height="519" alt="owasp57" src="https://github.com/user-attachments/assets/9ad040c8-dc17-4fbb-a254-21343a8c72ab" />

> I then went back to Mozilla FireFox opened up the application and changed "secure-file-storage.com:8087" to "10.201.44.115:4444," pressed "enter," and went back to the AttackBox Terminal and saw that
the intercepted API key was "THM{Hello_Im_just_an_API_key}."

> <img width="1018" height="557" alt="owasp59" src="https://github.com/user-attachments/assets/4c1e3d80-15f1-4d30-89e7-708dce4053fc" />

> I then went ahead and completed the extra final task which was to use SSRF to gain access to the admin area. To do this i opened up a new tab on my AttackBox Terminal and inputted the command
"nc -lvp 4444," pressed "enter," and begain listening on port 4444.

> <img width="530" height="107" alt="owasp60" src="https://github.com/user-attachments/assets/f7c23ebb-ed98-417f-8634-a657e92a255b" />

> I then went back to Mozilla Fox, opened the application into the searchbar and changed "10.201.44.115:4444" to "localhost:8087/admin%23." The reason why i added "%23" at the end was because this is
the url encoding for the has symbol and it directs you to a specific portion of a webpage and in this case we needed to be redirected to the admin portion of the webpage.

> <img width="855" height="277" alt="owasp61" src="https://github.com/user-attachments/assets/fa57ea46-934b-45c7-8223-7eda2fd2aeee" />

> After pressing "enter" i retrieved the flag shown in the screenshot below.

> <img width="870" height="697" alt="owasp62" src="https://github.com/user-attachments/assets/4ab24ba4-3bb2-43d8-8bb1-83806f6b1cad" />
---


## Reflection

> This lab provided me with knowledge and hands-on experience with Burp Suite for web application pentesting.

