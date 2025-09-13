# [Web Hacking]

**TryHackMe Path**: [Cyber Security 101]  
**Lab Topic**: [SQL Fundamentals]  
**Date Completed**: [09/13/2025]

---

## 🧠 Summary

> In this lab, I learned about the importance of understanding 

---

## 🎯 Objectives
- [ ] Learn 
   
---

## 🧰 Tools Used
- THM Machine
- THM SQL

---

## 📊 Analysis & Screenshots

*** SQL ***

> After launching the THM Machine, I had to first set up My SQL, to do this i opened up the terminal app and inputted the command "mysql -u root -p," then pressed "enter."

> <img width="825" height="258" alt="sql1" src="https://github.com/user-attachments/assets/1905291c-81ba-4107-93b3-ed22f61f8f8f" />
> <img width="718" height="269" alt="sql2" src="https://github.com/user-attachments/assets/0123dbe2-6ccb-449d-a5e0-f8b01f07cfa6" />

*** Database and Table Statments ***

> I was then given a task to create a database called "thm_bookmarket_db" within SQL. To do this i had inputted the command "CREATE DATABASE thm_bookmarket_db;" and pressed "enter."

> <img width="441" height="55" alt="sql3" src="https://github.com/user-attachments/assets/45488bc1-01d3-4c29-84ea-4c26dc2bdd8a" />

> To confirm that the database was created in SQL i inputted the command "SHOW DATABASES;" and pressed "enter."

> <img width="462" height="362" alt="sql4" src="https://github.com/user-attachments/assets/00805f34-249f-45fa-9d51-2acb5829b936" />

> I then had to select the "thm_bookmarket_db" for interaction. To do this i inputted the command "USE thm_bookmarket_db;" and pressed "enter."

> <img width="302" height="37" alt="sql5" src="https://github.com/user-attachments/assets/1758e1c3-be9b-4961-9d03-32c2523077a0" />

> I then had to populate the "thm_bookmarket_db" with tables to do this i used the command "CREATE TABLE," along with three column names, and pressed "enter." This then created a table called
"book_inventory" and three columns called "book_id," "book_name," and "publication_date."

> <img width="490" height="125" alt="sql6" src="https://github.com/user-attachments/assets/e5ae8b7c-d77a-4755-87b2-4fee88fa5f01" />

> To confirm that the table was created within the "thm_bookmarket_db" i inputted the command "SHOW TABLES;" and pressed "enter."

> <img width="379" height="135" alt="sql7" src="https://github.com/user-attachments/assets/ca46a02a-9274-42ab-b574-d9502c5b0246" />

> To confirm that the columns were created within the tables i inputted the command "DESCRIBE book_inventory;" and pressed "enter."

> <img width="730" height="171" alt="sql8" src="https://github.com/user-attachments/assets/4eef7a8d-ecf0-4a88-8012-16e85199f3b1" />

> I then had to add a column called "page_count" to the "book_inventory" table using the "ALTER" statement. What i did was just inputted the command
"ALTER TABLE book_inventory
ADD page_count INT;" and pressed "enter."

> <img width="388" height="87" alt="sql9" src="https://github.com/user-attachments/assets/83a2752a-8bb3-409a-b3e5-a25296c03992" />

> After reading through the Database and Table Statements section, i was given a practical to find a flag within the databases. To do this i inputted the command "show databases;" and pressed "enter."
This then returned the flag "THM{575a947132312f97b30ee5aeebba629b723d30f9}."

> <img width="521" height="297" alt="sql10" src="https://github.com/user-attachments/assets/b3eaa443-3d28-42fe-b338-8260235108dc" />

> I was then given another practical to find a flag with the database "task_4_db." To do this i first had to switch to that databse by inputting the command "use task_4_db;" and pressing "enter."

> <img width="690" height="95" alt="sql11" src="https://github.com/user-attachments/assets/6b3c4bd4-99cf-4e82-9a81-d454e259c100" />

> I then inputted the command "SHOW TABLES;" then pressed "enter," and got the flag "THM{692aa7eaec2a2a827f4d1a8bed1f90e5e49d2410}."

> <img width="500" height="134" alt="sql12" src="https://github.com/user-attachments/assets/329c546a-d113-4a99-83e0-9c46f049b758" />

*** CRUD Operations ***

> After going through the CRUD operations sections i was then given a practical to figure out the name of the tool in the "hacking_tools" table that can be used to perform man-in-the-middle attacks
on wireless networks. To do this i had to first select "tools_db" by inputting the command "tools_db" and pressing "enter."

> <img width="647" height="97" alt="sql13" src="https://github.com/user-attachments/assets/d7d691ec-ea59-4b61-8003-37942dba6856" />

> To confirm that the "hacking_tools" table was in the database i inputted the command "SHOW TABLES;" and pressed "enter."

> <img width="328" height="139" alt="sql14" src="https://github.com/user-attachments/assets/5b9ff468-e24f-4281-9b49-56d8e2453574" />

> I then inputted the command "SELECT * FROM hacking_tools;" and pressed "enter" and saw the tool that can be used to perform man-in-the-middle attacks on wireless networks which was called
"Wi-Fi Pineapple."

> <img width="1127" height="475" alt="sql15" src="https://github.com/user-attachments/assets/a7d96f40-7647-4a60-9016-7b1dcf19a197" />

> I then had to figure out the shared category for both USB Rubber Ducky and Bash Bunny. So i just looked within the "hacking_tools" table and saw them both under the category of "USB attacks."

> <img width="1132" height="471" alt="sql16" src="https://github.com/user-attachments/assets/a97ba157-207d-4085-8155-931f07f932b4" />

> *** Clauses ***

> After going through the reading of the "clauses" section i was then given my first practical to figure out the total number of distinct categories within the "hacking_tools" table. To do this i
first selected the "tools_db" database by inputting the command "use tools_db" and pressing "enter."

> <img width="676" height="71" alt="sql17" src="https://github.com/user-attachments/assets/2ef12985-35fe-4707-9bc8-b01270856e6a" />

> To list all distinct categories i inputted the command "SELECT DISTINCT category FROM hacking_tools;" and pressed "enter."

> <img width="514" height="223" alt="sql18" src="https://github.com/user-attachments/assets/1649fd70-be6b-4025-89a5-26d675711236" />

> I then had to figure out the name of the first tool in ascending order from the "hacking_tools" table. To do this i inputted the command
"SELECT *
FROM hacking_tools
ORDER by name ASC;" and pressed "enter." This gave me the first tool name of "Bash Bunny."

> <img width="1127" height="513" alt="sql19" src="https://github.com/user-attachments/assets/11f9a73b-cd75-4591-a559-68b60d11730b" />

> Next i had to figure out the name of the first tool in descending order from the hacking_tools table. To do this i inputted the command
"SELECT *
FROM hacking_tools
ORDER by name DESC;" and pressed "enter." This gave me the first tool name of "Wi-Fi Pineapple."

> <img width="1123" height="520" alt="sql20" src="https://github.com/user-attachments/assets/59f8f81b-e45f-4a67-b7c2-b26fbaa7266d" />

*** Operators *** 

> After going through the reading of the "operators" section i was then given a practical to figure out which tool falls under the Multi-Tool category and is useful for pentesters and geeks within the
"tools_db." To do this i had to first select the "tools_db" by inputting the "use tools_db," and pressing "enter."

> <img width="616" height="93" alt="Screenshot 2025-09-13 at 12 49 13 PM" src="https://github.com/user-attachments/assets/786e23fb-a012-4a86-995c-81663c856f46" />

> I then inputted the command
"SELECT *
FROM hacking_tools
WHERE description LIKE "%pentesters%" and description LIKE "%geeks%;" and pressed "enter." Which then retreived the result of "Flipper Zero."

> <img width="1044" height="173" alt="sql22" src="https://github.com/user-attachments/assets/43a09131-a55e-4663-b7f4-f609770aef49" />

> I then had to figure out the category of tools with an amount greater than or equal to "300" within the "hacking_tools" table in the "tools_db." To get this i inputted the command
"SELECT *
FROM hacking_tools
WHERE category >= "300";" and pressed "enter." This gave me the category of "RFID cloning."

> <img width="1126" height="508" alt="sql23" src="https://github.com/user-attachments/assets/39df1cb3-08fc-4086-abe3-98e327538bbe" />

> Finaly i had to within the "tools_db" database i had to figure out which tool falls under the "Network Intelligence" category with an amount less than "100." To get this i inputted the command
SELECT *
FROM hacking_tools
WHERE category LIKE "%Network INtelligence%" < "100";" and pressed "enter." This gave me the name of "Lan Turtle" which had an amount less than 100.

> <img width="1134" height="510" alt="sql24" src="https://github.com/user-attachments/assets/5c1578d9-4b1f-4932-ab22-b3743ceb0682" />

*** Functions ***

> After going through the reading of the "functions" section i was then given a practical to figure out the tool with the longest name based on character length within the "tools_db" database.
To do this i first selected the "tools_db" by inputting the command "use tools_db," and pressing "enter."

> Next, i inputted the statement "SELECT name FROM hacking_tools ORDER BY LENGTH(name) DESC LIMIT 1;" and pressed "enter." This then retrieved the name of "USB Rubber Ducky" as the tool with the
longest name based on character length.
>
> <img width="806" height="131" alt="sql25" src="https://github.com/user-attachments/assets/dcf60498-a0fb-4a1a-b6f4-e59d0c24f36c" />

> I then had to figure out the sum of all tools within the "tools_db" database. To do this i inputted the command "SELECT SUM(amount) AS total_amount from hacking_tools;" and pressed "enter." This
then returned the total amount of "1444."
>
> <img width="609" height="134" alt="sql26" src="https://github.com/user-attachments/assets/9664f653-19d6-46dd-8697-c615fab39c65" />

> Finally i had to figure out what are the tool names where the amount does not end in 0, and i had to also group the tool names concatenated by "&." To do this i inputted the command
"SELECT GROUP_CONCAT(name SEPARATOR' & ')
FROM hacking_tools
WHERE amount % 10 ! = 0;" and pressed "enter." This then returned the tool names of "Flipper Zero & iCopy-XS." 
---

## Reflection

> This lab provided me with knowledge about 
