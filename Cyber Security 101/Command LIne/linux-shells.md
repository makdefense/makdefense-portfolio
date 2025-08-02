# [Command Line]

**TryHackMe Path**: [Cyber Security 101]  
**Lab Topic**: [Linux Shells]  
**Date Completed**: [07//2025]

---

## 🧠 Summary

> In this lab, I learned about the importance of 

---

## 🎯 Objectives
- [ ] Launch THM AttackBox
- [ ] Learn how to interact with a Shell
- [ ] Learn about the type of Linux Shells
- [ ] Learn about Shell scripting and Components
- [ ] 


---

## 🧰 Tools Used
- THM AttackBox
- THM Linux
  
---

## 📸 Screenshots

> [Linux pwd] "https://github.com/makdefense/makdefense-portfolio/blob/main/images/linux%20pwd.png"
> [Linux ls for "/home/user" directory] "https://github.com/makdefense/makdefense-portfolio/blob/main/images/linux%20ls%20contents%20of%20the%20directory.png"
> [Linux cat to display File's contents] "https://github.com/makdefense/makdefense-portfolio/blob/main/images/linux%20cat%20to%20display%20file%20contents.png"
> [Linux display the type of Shell being used in the OS] "https://github.com/makdefense/makdefense-portfolio/blob/main/images/linux%20see%20type%20of%20shell%20used.png"
> [Linux "cat" to display all available Shells] "https://github.com/makdefense/makdefense-portfolio/blob/main/images/linux%20cat%20display%20all%20frei%20Shells.png"
> [Linux command "zsh" to switch between Shells] "https://github.com/makdefense/makdefense-portfolio/blob/main/images/linux%20zsh%20switching%20Shells.png"
> [Linux creating and saving new Script File] "https://github.com/makdefense/makdefense-portfolio/blob/main/images/linux%20saving%20modified%20script.png"
> [Linux running the modified script] "https://github.com/makdefense/makdefense-portfolio/blob/main/images/linux%20running%20the%20modified%20script.png"
> [Linux creating a Loop file] "https://github.com/makdefense/makdefense-portfolio/blob/main/images/linux%20creating%20loop%20file.png"
> [Linux creating and saving new Loop Script File] "https://github.com/makdefense/makdefense-portfolio/blob/main/images/linux%20modifying%20and%20saving%20loop%20script.png"
> [Linux running the modified script] "https://github.com/makdefense/makdefense-portfolio/blob/main/images/linux%20running%20modified%20loop%20file.png"


---

## 📊 Analysis

> After launching AttackBox, I then launched Linux's terminal and i logged in to the interface using SSH with the credentials "user" for the Username, "user@Tryhackme" for the password,
and the IP address "10.201.40.223." I then inputted command "pwd," then "enter" button to check what was the working directory which then displayed "/home/user." I then inputted command
"ls" then "enter" button to list the contents of that working directory and displayed "flag_hunt.sh." I then inputted "cat flag_hunt.sh" and then enter button to display the contents of the file.
> 
> Next i decided the run a new command that displays the type of Shell that is currently being used for operating system, so i inputted "echo $SHELL," then "enter" button and "/bin/bash" was displayed
afterwards. I then wanted to figure out the list of all available Shells that were in the system, so i inputted "cat/etc/shells," then "enter" and the list of every Shell in the Linux OS was displayed.
I then inputted command "zsh," then enter to switch to the "zsh" Shell in the OS.
> 
> Following i then created a Script file within the bash Shell using the command "nano" then "first_script.sh" for name of the script file. Next within the script flie i inputted "!#/bin/bash" which is
known as shebang to start writing my script within the Script file. I then inputted a set of variables and commands for the script which included "echo 'Hey, what's your name'?," followed by "read name,"
and finally "echo 'Welcome, $name." What this script does is that it displays on the screen "Hey, what's your name?" first then it then takes input from the user using the "read" command where "name" is where
the variable will be stored, then finally "echo" executes "Welcome" and the name that the user provided at the "read" command. I then then pressed "control+X" to exit and "Y," then pressed enter button to save the
command. Next i decided to give the Script file a go by inputting "chmod +x first_script.sh," then pressing "enter" button to give execution permission to the script and then unputting "./first_script.sh" to execute.
>
> Afterwards i then created a loop file by inputting "nano loop_script.sh," then pressing the "enter" button. Next i inputted "#!/bin/bash" to start the script, then "enter" button, then "for i in {1..10}" to set the "i"
variable to iterate the numbers 1 through 10 when the script is executed, then "do" to indicate the start of the loop script, then "echo $i" to display the variables value for every iteration, then finally "done" which
will indicate the end of the loop script. I then saved the loop script by pressing "control+X" and then "Y," and finally pressing enter button. Afterwards i gave the script a go by inputting "chmod +x loop_script.sh,"
then pressing "enter" button, then "./loop_script.sh," then "pressing "button" which iterated the numbers 1 through 10.


---

## Reflection

> This lab provided me with knowledge about 
