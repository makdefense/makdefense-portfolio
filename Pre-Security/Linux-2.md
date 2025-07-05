# [Linux Fundamentals]

**TryHackMe Path**: [Pre-Security]  
**Lab Topic**: [Interacting With Linux-2]  
**Date Completed**: [07/04/2025]

---

## 🧠 Summary

> In this lab, I used TryHackMe to launch Ubuntu Linux and performed commands to explore man page, create files, distinguish a file's type, move a file to designated folder, figure out the
contents of a file, and learn permissions on the OS.

---

## 🎯 Objectives
- [ ] Access Linux Using SSH
- [ ] Launch and explore man page in terminal
- [ ] Create a file, figure out a file's type, move a file
- [ ] Figure out the contents of a file
- [ ] Learn Permissions on machine
      
---

## 🧰 Tools Used
- THM AttackBox
- Ubuntu Linux

---

## 📸 Screenshots

> [SSH login] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/Linux%20SSH%20sign%20in.png)
> [Display of different Commands] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/Linux%20display%20of%20commands.png)
> [Created file] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/Linux%20creating%20new%20file.png)
> [Determined file type] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/Linux%20determining%20file%20type.png)
> [Who Owns "Important"] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/Linux%20Owner%20of%20%22important%22.png)
> [Switch to user2] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/Linux%20switch%20to%20user2.png)
> [Displaying the Flag for "important"] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/Linux%20finding%20contents%20of%20%22important%22.png)

---

## 📊 Analysis

> Launched THM AttackBox, then signed into Linux Machine Terminal using SSH with an IP address of the remote machine and creditials of a dummy account provided by THM. The credentials used 
was "ssh tryhack@10.10.67.138" and the password was "tryhackme." After logging in i explored the man page using "man ls" command, then pressed "h" to display the different navigation
commands and navigated through the manual page, then figured out how to display the output in a "human-readable" way by using the command "-h." I then created a file in the terminal called
"newnote" using the command "touch newnote" then "ls." After I figured out what type of file is "unknown1" using the command "file unknown1" which displayed ASCII text type file. Following i moved the file
"myfile" to the directory "myfolder" using the command "mv myfile myfolder." I then figured out the contents of the file "myfile" using "cat myfile" command which then displayed the
flag "THM[FILESYSTEM]." Afterwards i figured out who was the owner of "important" by using the command "ls -lh," which was user2 then i used "su user2" command and input the password "user2" to switch
to user2 and then displayed the contents of the file "important" which was the flag THM[SU_USER2].
---

## Reflection

> This lab taught me a step up in commmands like how to move files, find out file types, create files, contents of file, and see which users own certain files on the OS. Took handwritten notes on commands to revise on my off time.
