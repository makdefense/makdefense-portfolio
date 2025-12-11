# [Core SOC Solutions]

**TryHackMe Path**: [SOC Level 1]  
**Lab Topic**: [Elastic Stack: The Basics]  
**Date Completed**: [12/11/2025]

---

## 🧠 Summary

> In this lab, I learned about the importance of understanding

---

## 🎯 Objectives
- [ ] Understand the components of ELK and their use in SOC
- [ ] Explore the different features of ELK
- [ ] Learn to search and filter data in ELK
- [ ] Investigate VPN logs to identify anomalies
- [ ] Familiarize with creating visualizations and dashboards in ELK

---

## 🧰 Tools Used
- THM AttackBox
- THM ELK Instance
- THM Mozilla FireFox
  
---

## 📊 Analysis & Screenshots

*** Lab Connection ***

> For this room, i had to learn how to use the Elastic Stack for log investigations. I had to first set up the lab connection by launching the target machibe then launching the
THM AttackBox, launching Mozilla FireFox, then inputting the link "http://10.67.157.183" within the input field to access the ELK Instance. After pressing "Enter" i was brought
to the login screen for the ELK Instance. I then used the credentials "Analyst" and "analyst123" to login.
>
> <img width="723" height="678" alt="elas1" src="https://github.com/user-attachments/assets/c464f033-6bc7-458a-b5a8-f84bb58822ab" />

*** Discover Tab ***

> After reading through this section, i was given my first question which was to figure out how many hits were returned after selecting the "vpn_connections" and filter from
31st December 2021 to 2nd Feb 2022. To figure this out i first selected the index "vpn_connections," then navigated to the top right hand corner of the Instance, selected
the dates "31st December 2021 to 2nd Feb 2022" under "Absolute" mode, then pressed "Update" which returned "2861" hits.
>
> <img width="736" height="609" alt="elas2" src="https://github.com/user-attachments/assets/fdebde9e-4552-416a-a80d-29b5b73f1fca" />
> <img width="593" height="427" alt="elas3" src="https://github.com/user-attachments/assets/d0c8636a-a33f-42e0-b529-5bb5b2346587" />

> Moving onto the next question i had to figure out which IP address had the maximum connections. To figure this out i navigated to the left handed side of the Instance under
"Filter by type," and "Available fields," selected "Source_ip," and saw that the IP address of "238.163.231.224" had the maximum connections.
>
> <img width="634" height="440" alt="elas4" src="https://github.com/user-attachments/assets/4bfbdc37-174e-4cb6-8f32-22cfbe1f0369" />

> Next question i had to figure out which user was responsible for the overall maximum traffic. To figure this out i navigated to the left handed side of the Instance, selected
both "Source_ip" and "UserName," then hovered over the filter "UserName" and saw that the UserName "James" was responsible for the overall maximum traffic.
>
> <img width="611" height="785" alt="elas5" src="https://github.com/user-attachments/assets/61dc5114-ca38-4804-962a-c4c9ad741e53" />

> Next question i had to figure out which "SourceIP" had max hits under the UserName "Emanda." To figure this out i simply navigated to the left under "Filter by type," hovered
over "UserName" selected "Emanda," then hovered over "Source_ip," and saw that the IP with the max hits were "107.14.1.247."
>
> <img width="645" height="790" alt="elas6" src="https://github.com/user-attachments/assets/6de73718-c8d0-48a1-af78-7ca48a45b978" />

> Moving on to the next question i had to figure out which IP caused a spike observed in the time chart on Jan 11th. To figure this out I navigated to the left on the Instance
selected "Source_Ip" and saw that the IP address was "172.201.60.191."
>
> <img width="1591" height="720" alt="elas7" src="https://github.com/user-attachments/assets/0e477aa7-0ba5-403d-bc08-7432a815291f" />

> I then had to figure out how many connections were observed from the IP "238.163.231.224," excluding New York state. To figure this out i navigated to the left of the Instance,
added "source_state," along with "Source_Ip," and "UserName" under the "Selected Fields" under "Filter by type." I then navigated to the middle of the instance and under
"source_state" i clicked the "filter out value" icon for new york and the returned connections was 48.
>
> <img width="956" height="693" alt="elas8" src="https://github.com/user-attachments/assets/0d185903-e7ec-4176-ac79-bb58af1a17ce" />
> <img width="816" height="574" alt="elas10" src="https://github.com/user-attachments/assets/c7b7a019-7734-4983-8b00-9afe40b98bdd" />

For the last question for this section i had to create a table with the fields "IP," "UserName," "Source_Country." To do so i 

*** KQL Overview ***

> For the first question for this section i had to figure out many records were returned after creating a search query to filter the logs where "Source_Country" is the United
States and show logs from User James or Albert. To figure this out i first navigated to the top and selected "Add Filter," then added the "Source Country" as" "United States"
for one of the filter option. I then went to the top of the input field and added "James" or "Albert," clicked "Update," and retrieved the total number of hits to be "161."
>
> <img width="830" height="353" alt="elas11" src="https://github.com/user-attachments/assets/134cab3b-883f-40e7-b1c9-9539329f69c0" />
> <img width="851" height="563" alt="elas12" src="https://github.com/user-attachments/assets/7c17228c-ec41-4c04-b1cb-d1c9287a7d70" />

*** Create Visualization ***

> For the two questions of this section i had to figure out which user was observed with the greatest number of login attempts and how many wrong VPN connection attempts were
observed in january. To figure this out i navigated to the left of the Instance, selected "Visualize Library," then "create visualization," then selected "Lens," then "add
filter." I added the following information to the filter settings: action = failed, then clicked saved, then from the filter type fields i dragged the filter "UserName" into the
visualization, and selected to view the results in table format. This then returned the UserName of "Simon," and the wrong VPN connection attempts to be 274 in January.
>
> <img width="1343" height="292" alt="elas13" src="https://github.com/user-attachments/assets/27fb0473-1458-4f72-88fc-f3bfc3815f6f" />
> <img width="504" height="322" alt="elas14" src="https://github.com/user-attachments/assets/4c4335cc-4b62-447c-b2c1-89550bf23101" />
> <img width="1034" height="558" alt="elas15" src="https://github.com/user-attachments/assets/18bc99d8-11fa-4fc4-a125-f03efd9ea0f4" />
> <img width="1075" height="438" alt="elas16" src="https://github.com/user-attachments/assets/df8f9dbf-fa64-48f1-a9e8-702bf55216a9" />
---

## Reflection

> This lab provided me with knowledge about how SOC analysts use the Elastic Stack (ELK) for log investigations.
