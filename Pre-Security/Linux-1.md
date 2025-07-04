# [How Website Work]

**TryHackMe Path**: [Pre-Security]  
**Lab Topic**: [Interacting With Linux-1]  
**Date Completed**: [07/04/2025]

---

## 🧠 Summary

> In this lab, I used TryHackMe to launch Ubuntu Linux and iteracted with it for the first time.

---

## 🎯 Objectives
- [ ] Run First New Commands
- [ ] Figure out the filesystem
- [ ] Change directory
- [ ] Output content of a file
- [ ] Find full path of folder that contains files
- [ ] Search for files
- [ ] Use Grep to find a flag
      
---

## 🧰 Tools Used
- THM
- Ubuntu Linux

---

## 📸 Screenshots

> [Launched Ubuntu Linux] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/Linux%20Launch.png)
> [Using "ls" command] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/Linux%20Listing%20files%20and%20Changing%20directory.png)
> [Using "cat" command] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/Linux%20Using%20CAT%20to%20output%20file.png)
> [Using "pwd" command] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/Linux%20Using%20PWD%20to%20find%20full%20path.png)
> [Using "Grep" command] (https://github.com/makdefense/makdefense-portfolio/blob/main/images/Linux%20Using%20Grep%20to%20find%20flag.png)

---

## 📊 Analysis

> Launch Ubuntu Linux for the first time, input two new commands within the OS "echo" and "whoami." i use used the command "whoami" to find out the username of who i was logged
in as. Afterwards i used the "ls" command to see all the files and folders that exist within the system. Then changed the directory to find which folder has a file by using the "cd" command. Found
that folder 4 contained a note.txt file. Afterward i used the command "cat" to output the contents of the exact note.txt file. Then used the "pwd" to find the full path of the
"folder4" folder. Finally i started searching for files using the "find" command, then specifically used the "Grep" command on the access.log to find a flag.

---

## Reflection

> This lab taught me an introduction on how to input basic commands, find files, change the directory, output contents of a file, find the full path to a folder on the OS, and
search for requested files in Ubuntu Linux.
