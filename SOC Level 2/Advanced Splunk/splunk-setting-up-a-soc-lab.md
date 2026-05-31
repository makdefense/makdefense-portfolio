# [Advanced Splunk]

**TryHackMe Path**: [SOC Level 2]  
**Lab Topic**: [Splunk: Setting up a SOC Lab]  
**Date Completed**: [05/31/2026]

---

## 🧠 Summary

> In this lab, I learned how to install and configure Splunk along with the Universal Forwarder on a Linux host to enable log collection and forwarding. I explored Splunk
configuration through the command line, gaining hands-on experience modifying configuration files and managing inputs. Additionally, I developed an understanding of how to ingest
both Linux system logs and web server logs into Splunk, allowing for centralized monitoring and analysis.

---

## 🎯 Objectives
- [ ] Learn how to install Splunk and the Universal Forwarder on a Linux host
- [ ] Explore Splunk configuration via the command line
- [ ] Understand how to ingest Linux and Web logs into Splunk

---

## 🧰 Tools Used
- THM AttackBox
- Splunk
- Mozilla FireFox

---

## 📊 Analysis & Screenshots

*** Linux Deployment ***

> In this section, I was given specific instructions to set up my first SOC lab. After following the instructions, I was able to access my Splunk SOC lab using the link:
http://coffely:8000
>
> <img width="1111" height="558" alt="1" src="https://github.com/user-attachments/assets/82fe5df3-e65b-479c-b4d2-3356a2e1f60b" />
> <img width="929" height="324" alt="2" src="https://github.com/user-attachments/assets/aaac8080-fdb5-492a-9ee3-f1756effe670" />

*** Splunk Universal Forwarder ***

> In this section, I set up a forwarder for my SOC lab. To do this, I navigated to the /home/ubuntu/Downloads/splunk directory and entered the following command:
tar xvzf splunkforwarder.tgz -C /opt
>
> <img width="1364" height="313" alt="3" src="https://github.com/user-attachments/assets/8b57d9cc-3362-46f9-aba6-c98e0456e48a" />

> After extracting the forwarder, I started it using the command:
./splunk start --accept-license
>
> <img width="877" height="132" alt="4" src="https://github.com/user-attachments/assets/0132f52b-d743-476c-9e11-da7702249599" />

> I then changed the default management port from 8089 to 8090 so that both the SOC lab and the forwarder could run simultaneously.
>
> <img width="1024" height="604" alt="5" src="https://github.com/user-attachments/assets/42b10157-bc50-4efd-beb7-4dee1774fc02" />

*** Configuring the Forwarder ***

> In this section, I configured Splunk by setting the receiving port to 9997.
>
> <img width="747" height="395" alt="6" src="https://github.com/user-attachments/assets/ceed98ea-5c6c-4f04-81df-321335cb8dce" />
> <img width="1402" height="531" alt="7" src="https://github.com/user-attachments/assets/32a8d92c-f511-46b7-9d46-e0145d5a655e" />

> I then created an index called "linux_host".
>
> <img width="741" height="608" alt="8" src="https://github.com/user-attachments/assets/e7ee70c5-4f4a-402c-9249-c77a005db069" />
> <img width="436" height="275" alt="9" src="https://github.com/user-attachments/assets/6ae15e9f-539b-42e2-b9c5-5446a8a75c00" />
> <img width="1121" height="993" alt="10" src="https://github.com/user-attachments/assets/a6805a38-0001-4029-b6d0-a874f5bb381c" />

> Next, I configured the forwarder to send data to the correct destination using the command:
./splunk add forward-server 10.67.188.176:9997
This directed log forwarding to the specified IP address and port.
>
> <img width="1005" height="188" alt="11" src="https://github.com/user-attachments/assets/c2e712a5-e61c-4827-966e-0be61a57bad2" />

> I then ingested the syslog file into Splunk using the command:
./splunk add monitor /var/log/syslog -index linux_host

I used the logger utility to generate a log entry labeled:
"coffely-has-the-best-coffee-in-town"

To confirm ingestion, I ran the search:
index=linux_host "coffely-has-the-best-coffee-in-town"
>
> <img width="1119" height="176" alt="12" src="https://github.com/user-attachments/assets/19decc16-1419-465a-ba7b-78d283737ae8" />
> <img width="1205" height="619" alt="13" src="https://github.com/user-attachments/assets/ecf3e567-4069-43a3-a70d-03f9a2449ba2" />

> I then ingested /var/log/auth.log into the same index and identified the sourcetype field value as:
auth
>
> <img width="1242" height="407" alt="14" src="https://github.com/user-attachments/assets/96f4e87b-60e9-464c-8e00-4f0e08ec57ff" />
> <img width="1067" height="760" alt="15" src="https://github.com/user-attachments/assets/c79f8e3e-ba60-4796-ba6c-05e08728b169" />

> For the final task in this section, I created a new user named analyst using the command:
adduser analyst

I then reviewed the syslog events in Splunk related to this activity and identified the process field value as:
adduser
>
> <img width="726" height="815" alt="16" src="https://github.com/user-attachments/assets/0ad1cc10-c684-42b7-9e3e-e60718cd2e9d" />
> <img width="1061" height="513" alt="17" src="https://github.com/user-attachments/assets/b370b5a6-69de-465a-9528-a0c70d04a516" />
> <img width="1210" height="786" alt="18" src="https://github.com/user-attachments/assets/07a9f09a-dcae-4679-9512-41f62c82dcdb" />

*** Ingesting Web Logs ***

> In this section, I added a file to be monitored in my Splunk SOC lab:
/var/log/apache2/access.log

I set the sourcetype to access_combined, assigned the host field value as coffelyweb, and created a new index called "web", then submitted the configuration.
>
> <img width="1309" height="666" alt="19" src="https://github.com/user-attachments/assets/de76e14a-6752-4bf6-a9fc-352d8e67c38a" />
> <img width="1393" height="439" alt="20" src="https://github.com/user-attachments/assets/b469463b-dc69-4aa4-9ce9-052d77dde8d0" />
> <img width="934" height="953" alt="21" src="https://github.com/user-attachments/assets/db02050e-2928-46b2-a457-eddc8b14b472" />
> <img width="1044" height="963" alt="22" src="https://github.com/user-attachments/assets/35d20dfd-3ca5-4ec8-ba68-32fcf148171b" />
> <img width="1170" height="739" alt="23" src="https://github.com/user-attachments/assets/972c703b-d102-40f5-be8a-6433e0b39cc4" />
> <img width="1310" height="678" alt="24" src="https://github.com/user-attachments/assets/d7dbf5c6-836b-4ad4-814c-3e82de822f07" />

> I identified the correct sourcetype for parsing Apache access logs as:
access_combined
>
> <img width="1049" height="778" alt="25" src="https://github.com/user-attachments/assets/6c5c25fe-51f7-454a-b142-094708bb85f3" />

> I then determined that the root field value with the highest count was:
images
>
> <img width="1108" height="409" alt="26" src="https://github.com/user-attachments/assets/29d92fbf-8eeb-4ed0-b3ee-56077bf484f3" />

> I identified the full uri_path value for cappuchino.png as:
/images/coffeerecipes/cappuchino.png, using the query:
index=web cappuchino
>
> <img width="1169" height="580" alt="27" src="https://github.com/user-attachments/assets/313d56a0-b422-4835-8524-bc8c9d803902" />

> Finally, I discovered a hidden flag:
THM{best_coffee_in_town!}
by navigating to:
http://coffely.thm:8080/secret-flag.html
>
> <img width="1238" height="483" alt="28" src="https://github.com/user-attachments/assets/93e7d5dd-0c75-4f42-9f19-dd84990d1c9e" />

--- 

## Reflection

> This lab strengthened my ability to set up and configure a functional SOC lab environment, including installing Splunk, configuring forwarders, and ingesting multiple log
sources. It reinforced my understanding of log pipelines and how data flows from endpoints into a SIEM for centralized monitoring and analysis, which is essential for real-world
security operations.
