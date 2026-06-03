# [Advanced Splunk]

**TryHackMe Path**: [SOC Level 2]  
**Lab Topic**: [Splunk: Data Manipulation]  
**Date Completed**: [06//2026]

---

## 🧠 Summary

> In this lab, 

---

## 🎯 Objectives
- [ ]
---

## 🧰 Tools Used
- THM AttackBox
- Splunk

---

## 📊 Analysis & Screenshots

*** Creating a Splunk App ***

> In this section, I had to launched Splunk then create an app within the interface titled "DataApp." I then had to answer a few questions related to this section. The first one
was to figure out how many default applications were available within the Splunk interface using Commnad Line. Upon further investigation i was able to retrieve 25 apps.
>
> <img width="608" height="851" alt="1" src="https://github.com/user-attachments/assets/9fe1bea1-603a-42e4-8b2a-33340585d321" />
> <img width="549" height="89" alt="2" src="https://github.com/user-attachments/assets/0fc8a991-27df-4c14-ad7d-4693cd941d77" />
> <img width="652" height="462" alt="3" src="https://github.com/user-attachments/assets/471a6beb-c32a-479f-ba17-77be5caf5e38" />
> <img width="603" height="265" alt="4" src="https://github.com/user-attachments/assets/c425ff7e-a882-4eaf-a8b2-89fe4f80b875" />
> <img width="550" height="213" alt="5" src="https://github.com/user-attachments/assets/99ee8f1b-ff49-46d0-80bc-5bb350b37cde" />
> <img width="1487" height="970" alt="6" src="https://github.com/user-attachments/assets/a9c771e9-d093-475d-844b-b6d21fe4e173" />
> <img width="636" height="349" alt="7" src="https://github.com/user-attachments/assets/b31b3e80-9616-48c9-8915-005043fc46a8" />
> <img width="1443" height="341" alt="8" src="https://github.com/user-attachments/assets/cd43d381-debd-421f-b961-11cc5036cb28" />

> Moving on i then had to figure out the full path to my newly created application directory. Upon further investigation within Command Line i was able to discover the full path
to be:
/opt/splunk/etc/apps/DataApp
>
> <img width="776" height="163" alt="9" src="https://github.com/user-attachments/assets/5302ec80-ddc1-4ed9-8b3e-98eabeef9869" />
> <img width="1503" height="167" alt="10" src="https://github.com/user-attachments/assets/71cb5cbd-0b17-4674-bf68-d116352e3249" />
> <img width="768" height="74" alt="11" src="https://github.com/user-attachments/assets/bbfb488c-a5ad-4a8c-bc30-9a8d54f3d048" />

*** Configuring Event Boundaries ***

> Moving onto this section, starting off i ingested VPN logs into Splunk by instructing Splunk to run the script every five seconds and ingest them into the "main" index,
specifiying the sourcetype and host.
>
> <img width="783" height="220" alt="12" src="https://github.com/user-attachments/assets/4caff119-4f5e-4cd2-aac0-301bca5cf9b7" />
> <img width="1167" height="705" alt="13" src="https://github.com/user-attachments/assets/8f4a96de-cd40-46fd-be18-fe429850ff4a" />

> I then fixed event boundaries by creating a props.conf configuration file used the following entry:
[vpn_logs]
SHOULD_LINEMERGE = false
MUST_BREAK_AFTER = (CONNECT|DISCONNECT)
which basically is telling Splunk to use the vpn_logs source type, not to merge log lines since each line represents a singular event, and to recognize the beginning of a new event
after CONNECT and DISCONNECT. I then verified the changes by running the query:
index = main sourcetype = vpn_logs
>
> <img width="671" height="109" alt="14" src="https://github.com/user-attachments/assets/2f2c6603-222b-43a9-a95c-f86e909a131f" />
> <img width="590" height="267" alt="15" src="https://github.com/user-attachments/assets/5541f7cd-cf65-4992-8733-78f240e70178" />
> <img width="608" height="230" alt="16" src="https://github.com/user-attachments/assets/ee1c9aa7-f22e-457b-b0a7-1ddf81ff19a5" />
> <img width="1063" height="75" alt="17" src="https://github.com/user-attachments/assets/ba4668fe-c5a5-4dac-8aa8-678555da0e60" />
> <img width="1247" height="655" alt="18" src="https://github.com/user-attachments/assets/dfae5f63-f3a1-4677-9909-51285fc51e02" />

*** Parsing Multi-Line Events ***

> Moving on, i then copied the "authentication_logs" executable into my app's /bin directory using the command syntax:
cp /home/ubuntu/Downloads/scripts/authentication_logs /opt/splunk/etc/apps/DataApp/bin/
then ran it using the command:
/opt/splunk/etc/apps/DataApp/bin/authentication_logs
this then returned an authentication event with in-depth details.
>
> <img width="1337" height="149" alt="19" src="https://github.com/user-attachments/assets/a1a5ecc9-f318-43bc-a1ee-581e27aa9320" />
> <img width="981" height="100" alt="20" src="https://github.com/user-attachments/assets/0aa38a08-c1b9-41a1-a7ab-cce07f6969ef" />

> I then ingested the authentication logs to my Splunk app by altering the "inputs.conf" file in the "/local" directory of my app by using the following entry:
[script:///opt/splunk/etc/apps/DataApp/bin/authentication_logs]
index = main
sourcetype = auth_logs
host = auth_server
interval = 5
i then restarted Splunk, then verified that the logs were ingested using the following query within m Splunk instance:
index = main sourcetype = auth_logs
>
> <img width="667" height="164" alt="21" src="https://github.com/user-attachments/assets/ebd0b43e-819f-44db-981f-0814d71b6371" />
> <img width="872" height="432" alt="22" src="https://github.com/user-attachments/assets/299f140c-d28f-45c4-8119-41ef5ced68b7" />
> <img width="928" height="113" alt="23" src="https://github.com/user-attachments/assets/18a6d4f3-2bd9-4c97-9bff-0ae94c0c158d" />
> <img width="1305" height="596" alt="24" src="https://github.com/user-attachments/assets/836e758d-d83a-4e73-917e-fd356050a78a" />

> Then to fix the event boundaries for my authentication logs, i added the following stanza to my props.conf configuration file:
[auth_logs]
SHOULD_LINEMERGE = true
BREAK_ONLY_BEFORE = \[Authentication\]
so this entry basically used the term "[Authentication]" to create a regex pattern and instruct Splunk on how to split the events.
I then verified the changes using the query:
index = main sourcetype = auth_logs
>
> <img width="803" height="76" alt="25" src="https://github.com/user-attachments/assets/7702bc4c-c2e5-4b4f-910d-4a171497cb74" />
> <img width="644" height="317" alt="26" src="https://github.com/user-attachments/assets/7c202b64-8818-4a46-a3b4-7fb7a0d7dcf3" />
> <img width="1222" height="578" alt="27" src="https://github.com/user-attachments/assets/e5eb1bb4-e5a5-486e-90d9-c7e7dea95c05" />

*** Masking Sensitive Data ***

> Moving on, i then copied over the purchase logs into my DataApp /bin directory by using the command:
cp /home/ubuntu/Downloads/scripts/purchase-details /opt/splunk/etc/apps/DataApp/bin/
then displayed the logs using the command:
/opt/splunk/etc/apps/DataApp/bin/purchase-details
>
> <img width="1117" height="180" alt="28" src="https://github.com/user-attachments/assets/435b9294-85b2-416e-8b32-ccbcd16d0a49" />

> I then ingested the purchase logs into Splunk by altering my inputs.conf file by adding the following stanza:
[script:///opt/splunk/etc/apps/DataApp/bin/purchase-details]
index = main
sourcetype = purchase_logs
host = order_server
interval = 5
then setup event boundaries using the regex of:
\d{4}\. within the following added stanza:
[purchase_logs]
SHOULD_LINEMERGE = true
MUST_BREAK_AFTER = \d{4}\.
to my props.conf configuration file. I then verified the changes by restarting Splunk within Command Line then in my Splunk instance using the query:
index = main sourcetype = purchase_logs
>
> <img width="719" height="592" alt="29" src="https://github.com/user-attachments/assets/b8ab0a5f-7de9-418c-8eae-a8ce72967547" />
> <img width="723" height="57" alt="30" src="https://github.com/user-attachments/assets/c895a602-67d6-4970-bd42-bec2b198327a" />
> <img width="578" height="448" alt="31" src="https://github.com/user-attachments/assets/40c93575-d5d7-40d9-a1bb-2af2ab05f49e" />
> <img width="956" height="90" alt="32" src="https://github.com/user-attachments/assets/bd56dfef-b0ec-4dcf-b84c-9a18c60103ba" />
> <img width="1209" height="606" alt="33" src="https://github.com/user-attachments/assets/8ce7d473-2216-494c-adc5-90ecd5b7e7d2" />

> To mask all credit card information within Splunk, i then used the altered stanza:
[purchase_logs]
SHOULD_LINEMERGE = true
MUST_BREAK_AFTER = \d{4}\.
SEDCMD-cc = s/-\d{4}-\d{4}-\d{4}/-XXXX-XXXX-XXXX/g
within my props.conf file. TO verifiy the changes i restarted Splunk using Command Line then in my Splunk instace searched the query:
index = main sourcetype = purchase_logs
which displayed all credit card information masked.
>
> <img width="741" height="102" alt="34" src="https://github.com/user-attachments/assets/d7d6adef-f51e-43ee-bbc6-11c07e2313f8" />
> <img width="610" height="358" alt="35" src="https://github.com/user-attachments/assets/20802b88-c145-4f01-94d8-fc02af7b32f3" />
> <img width="1295" height="604" alt="36" src="https://github.com/user-attachments/assets/e622195d-2fb2-484e-a225-1793f25903c4" />

*** Extracting Custom Fields ***

> For this section, i had to extract custom fields through creating a regex pattern. I used the following regex pattern:
User:\s(.+?),\sServer:\s(.+?),\sAction:\s(\w+)
and the test string:
User: John Doe, Server: Server B, Action: DISCONNECT
User: Bob Johnson, Server: Server A, Action: CONNECT
User: John Doe, Server: Server D, Action: CONNECT
User: Emily Davis, Server: Server C, Action: CONNECT
User: Bob Johnson, Server: Server B, Action: CONNECT
User: Alice Smith, Server: Server C, Action: DISCONNECT
User: John Doe, Server: Server D, Action: CONNECT
User: Alice Smith, Server: Server C, Action: CONNECT
User: Michael Brown, Server: Server B, Action: DISCONNECT
into regex101 which captured all three fields and organized them into groups.


> I then configured a transformation by creating a transforms.conf file within the /local directory of my app and then entered the following stanza:[vpn_custom_fields]
REGEX = User:\s(.+?),\sServer:\s(.+?),\sAction:\s(\w+)
FORMAT = User::$1 Server::$2 Action::$3
WRITE_META = true
this assigns a name to my field extraction which is:
vpn_custom_fields
it also specifies the regex pattern, and provides the format so my Splunk instance knows how to name the extracted fields.
>
> <img width="584" height="87" alt="37" src="https://github.com/user-attachments/assets/a285e33d-8996-42c5-b70f-4c6329a23cd6" />
> <img width="638" height="283" alt="38" src="https://github.com/user-attachments/assets/229047e7-8d35-4b95-a8fb-53189018b28d" />













 















 














--- 

## Reflection

> This lab strengthened my ability to 
