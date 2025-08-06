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
> [] ""
> [] ""
> [] ""
> [] ""
>

---

## 📊 Analysis

> After launching AttackBox, I then launched Linux's terminal and i logged in to the interface using SSH with the credentials "user" for the Username, "user@Tryhackme" for the password,
and the IP address "10.201.40.223." I then inputted command "pwd," then "enter" button to check what was the working directory which then displayed "/home/user." I then inputted command
"ls" then "enter" button to list the contents of that working directory and displayed "flag_hunt.sh." I then inputted "cat flag_hunt.sh" and then enter button to display the contents of the file.
> 
> Next i decided the run a new command that displays the type of Shell that is currently being used for operating system, so i inputted "echo $SHELL," then "enter" button and "/bin/bash" was displayed
afterwards. I then wanted to figure out the list of all available Shells that were in the system, so i inputted "cat /etc/shells," then "enter" and the list of every Shell in the Linux OS was displayed.
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
then pressing "enter" button, then "./loop_script.sh," then "pressing "button" which iterated the numbers 1 through 10. Next i implemented conditional statements by first creating a new file called "conditional_script.sh"
by inputting "nano conditional_script.sh," then pressing the "enter" button. Then within the script file i inputted "#!/bin/bash," then pressed "enter" button to start writting script that took a user's name and stored it
into a variable. So on first line of the script i inputted 'echo "Please enter your name first:'," then "read name" on the second line, then "if [ "$name" = "Makonenn" ]; then" on the third, then on the fourth line "echo
'Welcome Makonenn! Here is the secret: THM_Script'," then "else" on the fifth, then on the sixth line "echo 'Sorry! You are not authorized to access the secret.'," and finally "fi" on the last line of the script. To save and
close out the script i pressed "control+X," then Y to save the script. Next i inputted "chmod +x conditional_script.sh," then pressed "enter" button to implement execution permissions to the conditional statment. Then gave the
script a go by inputting "./conditional_script.sh," then pressing "enter" button. I then added comments into the script of the conditional statement by inputting "nano conditional_script.sh," entered the comments so that the
code can be comprehended by others easily since the code is lengthy.
> 
> After performing various Shell Scripting, I then created a "Locker Script" which will be used to secure the locker for a bank which will only open after a user has verified themselves. I inputted "nano locker_script.sh,"
to create the file, then pressed "enter." Next to start writing the script i inputted "!#/bin/bash," then code that defines the variables, defines the loop, defines the conditional statements, finally code that checks if the
user entered the correct details. To exit and saved the script for the script file i pressed "control+x," and then pressed "Y." I then gave the locker script a go by first executing the permissions to run it by inputting
"chmod +x locker_script.sh," then pressed "enter" button, then "./loop_script.sh," then pressed "enter" button, and finally inputted the variables the generate the pin for the locker.
> 
> Lastly, I completed a practical exersise which was to make changes to the code inside of a given script file called "flag_hunt.sh," to then find a specific file that has the ".log" extension, and to find out where the cat was
sleeping. To do this i first had to become the root user by inputting "sudo su," then pressing "enter," then inputting the password "user@Tryhackme." Then I had to get into nano mode to edit the script file "flag_hunt.sh", so i
first inputted "nano flag_hunt.sh," then pressed "enter" button. What was displayed was the script but there were missing variables to some of the code. For the # defining the directory to search our flag code "directory=" i had to
fill in the variable as "/var/log/," for the # defining the flag to search code "flag," i had to fill in the variable as "thm-flag01-script," and for the # defining for loop to iterate over all the files with .log extension in
define directory code "for file in "" /*.log; do" i had to fill in the variable as "/var/log." After adjusting the code i saved and exited nano mode by inputting "control+x" and pressing "enter" button. I then gave permissions to
execute the script by typing "chmod +x flag_hunt.sh," then "enter" button. Then inputted "./flag_hunt.sh" to run the script, this then search the "/var/log" directory for the ".log" file that contained the flag. What was displayed
was "Flag found in: authentication.log," I then pressed "enter" then changed the directory by inputting "cd /var/log," then "ls" to list the contents of the directory, and found the "authentication.log" file within the directory.
To then find out where the cat was sleeping i inputted "cat /var/log/authentication.log," then "enter," what was then displayed was "the cat is sleeping under the table."


---

## Reflection

> This lab provided me with knowledge about 
