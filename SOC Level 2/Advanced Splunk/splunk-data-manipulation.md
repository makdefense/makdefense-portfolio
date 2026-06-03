# [Advanced Splunk]

**TryHackMe Path**: [SOC Level 2]  
**Lab Topic**: [Splunk: Data Manipulation]  
**Date Completed**: [06/03/2026]

---

## 🧠 Summary

> In this lab, I explored how Splunk ingests, parses, and normalizes machine data to make it searchable and actionable. I worked with core configuration files such as inputs.conf,
props.conf, and transforms.conf to control how data is collected, processed, and structured within the platform.

Additionally, I practiced extracting and normalizing key fields from raw log data while applying techniques to mask sensitive information. Finally, I applied data manipulation 
methods to ensure accurate and efficient search results, improving the reliability of queries used in security investigations.

---

## 🎯 Objectives
- [ ] Understand how Splunk ingests, parses, and normalizes machine data
- [ ] Create and manage core Splunk configuration files to control data
- [ ] Extract, normalize, and mask sensitive or custom fields
- [ ] Apply data manipulation techniques to build accurate search results 
  
---

## 🧰 Tools Used
- THM AttackBox
- Splunk
- Command Line

---

## 📊 Analysis & Screenshots

*** Creating a Splunk App ***

> In this section, I launched Splunk and created an app within the interface titled "DataApp." I then answered several questions related to this section. The first task was to
determine how many default applications were available within the Splunk interface using the command line. Upon further investigation, I was able to identify a total of 25 apps.
>
> <img width="608" height="851" alt="1" src="https://github.com/user-attachments/assets/9fe1bea1-603a-42e4-8b2a-33340585d321" />
> <img width="549" height="89" alt="2" src="https://github.com/user-attachments/assets/0fc8a991-27df-4c14-ad7d-4693cd941d77" />
> <img width="652" height="462" alt="3" src="https://github.com/user-attachments/assets/471a6beb-c32a-479f-ba17-77be5caf5e38" />
> <img width="603" height="265" alt="4" src="https://github.com/user-attachments/assets/c425ff7e-a882-4eaf-a8b2-89fe4f80b875" />
> <img width="550" height="213" alt="5" src="https://github.com/user-attachments/assets/99ee8f1b-ff49-46d0-80bc-5bb350b37cde" />
> <img width="1487" height="970" alt="6" src="https://github.com/user-attachments/assets/a9c771e9-d093-475d-844b-b6d21fe4e173" />
> <img width="636" height="349" alt="7" src="https://github.com/user-attachments/assets/b31b3e80-9616-48c9-8915-005043fc46a8" />
> <img width="1443" height="341" alt="8" src="https://github.com/user-attachments/assets/cd43d381-debd-421f-b961-11cc5036cb28" />

> Moving on, I then had to determine the full path to my newly created application directory. Using the command line, I discovered the full path to be:
/opt/splunk/etc/apps/DataApp
>
> <img width="776" height="163" alt="9" src="https://github.com/user-attachments/assets/5302ec80-ddc1-4ed9-8b3e-98eabeef9869" />
> <img width="1503" height="167" alt="10" src="https://github.com/user-attachments/assets/71cb5cbd-0b17-4674-bf68-d116352e3249" />
> <img width="768" height="74" alt="11" src="https://github.com/user-attachments/assets/bbfb488c-a5ad-4a8c-bc30-9a8d54f3d048" />

*** Configuring Event Boundaries ***

> In this section, I ingested VPN logs into Splunk by configuring a script to run every five seconds and send logs to the main index while specifying the sourcetype and host.
>
> <img width="783" height="220" alt="12" src="https://github.com/user-attachments/assets/4caff119-4f5e-4cd2-aac0-301bca5cf9b7" />
> <img width="1167" height="705" alt="13" src="https://github.com/user-attachments/assets/8f4a96de-cd40-46fd-be18-fe429850ff4a" />

> I then fixed event boundaries by creating a props.conf configuration file with the following entry:

[vpn_logs]
SHOULD_LINEMERGE = false
MUST_BREAK_AFTER = (CONNECT|DISCONNECT)
This configuration instructs Splunk to use the vpn_logs sourcetype, prevent line merging since each line represents a single event, and define new events after the keywords 
CONNECT or DISCONNECT.

I verified the changes by running the query:
index=main sourcetype=vpn_logs
>
> <img width="671" height="109" alt="14" src="https://github.com/user-attachments/assets/2f2c6603-222b-43a9-a95c-f86e909a131f" />
> <img width="590" height="267" alt="15" src="https://github.com/user-attachments/assets/5541f7cd-cf65-4992-8733-78f240e70178" />
> <img width="608" height="230" alt="16" src="https://github.com/user-attachments/assets/ee1c9aa7-f22e-457b-b0a7-1ddf81ff19a5" />
> <img width="1063" height="75" alt="17" src="https://github.com/user-attachments/assets/ba4668fe-c5a5-4dac-8aa8-678555da0e60" />
> <img width="1247" height="655" alt="18" src="https://github.com/user-attachments/assets/dfae5f63-f3a1-4677-9909-51285fc51e02" />

*** Parsing Multi-Line Events ***

> Next, I copied the authentication_logs executable into my app’s /bin directory using the following command:
cp /home/ubuntu/Downloads/scripts/authentication_logs /opt/splunk/etc/apps/DataApp/bin/
I then executed it using:
/opt/splunk/etc/apps/DataApp/bin/authentication_logs
This generated authentication events with detailed information.
>
> <img width="1337" height="149" alt="19" src="https://github.com/user-attachments/assets/a1a5ecc9-f318-43bc-a1ee-581e27aa9320" />
> <img width="981" height="100" alt="20" src="https://github.com/user-attachments/assets/0aa38a08-c1b9-41a1-a7ab-cce07f6969ef" />

> I ingested these logs into Splunk by modifying the inputs.conf file in the /local directory with the following entry:
[script:///opt/splunk/etc/apps/DataApp/bin/authentication_logs]
index = main
sourcetype = auth_logs
host = auth_server
interval = 5
After restarting Splunk, I verified ingestion using:
index=main sourcetype=auth_logs
>
> <img width="667" height="164" alt="21" src="https://github.com/user-attachments/assets/ebd0b43e-819f-44db-981f-0814d71b6371" />
> <img width="872" height="432" alt="22" src="https://github.com/user-attachments/assets/299f140c-d28f-45c4-8119-41ef5ced68b7" />
> <img width="928" height="113" alt="23" src="https://github.com/user-attachments/assets/18a6d4f3-2bd9-4c97-9bff-0ae94c0c158d" />
> <img width="1305" height="596" alt="24" src="https://github.com/user-attachments/assets/836e758d-d83a-4e73-917e-fd356050a78a" />

> To fix event boundaries, I added the following to props.conf:
[auth_logs]
SHOULD_LINEMERGE = true
BREAK_ONLY_BEFORE = \[Authentication\]
This configuration ensures events are split based on the [Authentication] pattern.

I verified the results using:
index=main sourcetype=auth_logs
>
> <img width="803" height="76" alt="25" src="https://github.com/user-attachments/assets/7702bc4c-c2e5-4b4f-910d-4a171497cb74" />
> <img width="644" height="317" alt="26" src="https://github.com/user-attachments/assets/7c202b64-8818-4a46-a3b4-7fb7a0d7dcf3" />
> <img width="1222" height="578" alt="27" src="https://github.com/user-attachments/assets/e5eb1bb4-e5a5-486e-90d9-c7e7dea95c05" />

*** Masking Sensitive Data ***

> In this section, I copied purchase logs into my app’s /bin directory:
cp /home/ubuntu/Downloads/scripts/purchase-details /opt/splunk/etc/apps/DataApp/bin/
Then displayed them using:
/opt/splunk/etc/apps/DataApp/bin/purchase-details
>
> <img width="1117" height="180" alt="28" src="https://github.com/user-attachments/assets/435b9294-85b2-416e-8b32-ccbcd16d0a49" />

> I ingested the logs by updating inputs.conf:
[script:///opt/splunk/etc/apps/DataApp/bin/purchase-details]
index = main
sourcetype = purchase_logs
host = order_server
interval = 5
I configured event boundaries in props.conf:
[purchase_logs]
SHOULD_LINEMERGE = true
MUST_BREAK_AFTER = \d{4}\.
After restarting Splunk, I verified ingestion using:
index = main sourcetype = purchase_logs
>
> <img width="719" height="592" alt="29" src="https://github.com/user-attachments/assets/b8ab0a5f-7de9-418c-8eae-a8ce72967547" />
> <img width="723" height="57" alt="30" src="https://github.com/user-attachments/assets/c895a602-67d6-4970-bd42-bec2b198327a" />
> <img width="578" height="448" alt="31" src="https://github.com/user-attachments/assets/40c93575-d5d7-40d9-a1bb-2af2ab05f49e" />
> <img width="956" height="90" alt="32" src="https://github.com/user-attachments/assets/bd56dfef-b0ec-4dcf-b84c-9a18c60103ba" />
> <img width="1209" height="606" alt="33" src="https://github.com/user-attachments/assets/8ce7d473-2216-494c-adc5-90ecd5b7e7d2" />

> To mask credit card data, I updated props.conf:
[purchase_logs]
SHOULD_LINEMERGE = true
MUST_BREAK_AFTER = \d{4}\.
SEDCMD-cc = s/-\d{4}-\d{4}-\d{4}/-XXXX-XXXX-XXXX/g
After restarting Splunk, I verified the masking using:
index=main sourcetype=purchase_logs
>
> <img width="741" height="102" alt="34" src="https://github.com/user-attachments/assets/d7d6adef-f51e-43ee-bbc6-11c07e2313f8" />
> <img width="610" height="358" alt="35" src="https://github.com/user-attachments/assets/20802b88-c145-4f01-94d8-fc02af7b32f3" />
> <img width="1295" height="604" alt="36" src="https://github.com/user-attachments/assets/e622195d-2fb2-484e-a225-1793f25903c4" />

*** Extracting Custom Fields ***

> In this section, I extracted custom fields using the following regex pattern:
User:\s(.+?),\sServer:\s(.+?),\sAction:\s(\w+)
This pattern successfully captured user, server, and action fields from the logs.

> I then created a transforms.conf file with the following configuration:
[vpn_custom_fields]
REGEX = User:\s(.+?),\sServer:\s(.+?),\sAction:\s(\w+)
FORMAT = User::$1 Server::$2 Action::$3
WRITE_META = true
>
> <img width="584" height="87" alt="37" src="https://github.com/user-attachments/assets/a285e33d-8996-42c5-b70f-4c6329a23cd6" />
> <img width="638" height="283" alt="38" src="https://github.com/user-attachments/assets/229047e7-8d35-4b95-a8fb-53189018b28d" />

> Next, I updated props.conf:
[vpn_logs]
SHOULD_LINEMERGE = false
MUST_BREAK_AFTER = (CONNECT|DISCONNECT)
TRANSFORM-vpn = vpn_custom_fields
I configured indexed fields in fields.conf:
[User]
INDEXED = true

[Server]
INDEXED = true

[Action]
INDEXED = true
After restarting Splunk, I verified extraction using:
index=main sourcetype=vpn_logs
>
> <img width="774" height="99" alt="39" src="https://github.com/user-attachments/assets/c6ef7cd8-a862-4761-a2da-a245d7a3f657" />
> <img width="542" height="341" alt="40" src="https://github.com/user-attachments/assets/b70a6cfd-24fb-48cf-a295-9f5155915241" />
> <img width="688" height="61" alt="41" src="https://github.com/user-attachments/assets/712347d5-f40d-454d-9731-80fef114f948" />
> <img width="346" height="378" alt="42" src="https://github.com/user-attachments/assets/41d6c688-6695-4bf0-b08b-2088171cc44e" />
> <img width="800" height="56" alt="43" src="https://github.com/user-attachments/assets/2056d40c-831c-494a-a003-84f425b488f8" />
> <img width="996" height="654" alt="44" src="https://github.com/user-attachments/assets/97d89aaf-1598-4b04-9c79-d4484469fe55" />

> I then configured additional field extraction for purchase logs using regex and verified results with:
index=main sourcetype="purchase_logs"
| table user_name credit_card _raw
>
> <img width="1271" height="396" alt="45" src="https://github.com/user-attachments/assets/4a415884-365d-410d-958b-b8cff7d13dd1" />
> <img width="705" height="84" alt="46" src="https://github.com/user-attachments/assets/bedc7b43-5fe8-4eb0-83a9-1339719c6c27" />
> <img width="762" height="482" alt="47" src="https://github.com/user-attachments/assets/435d8e1d-55e6-4284-aaf4-9b23310a4ea6" />
> <img width="614" height="526" alt="48" src="https://github.com/user-attachments/assets/2044a750-50ee-430c-aaf6-77308e48a97f" />
> <img width="1302" height="959" alt="49" src="https://github.com/user-attachments/assets/6590eab8-1194-4b5e-922d-be0e81d33c88" />

> Upon final analysis, I identified 14 user field values and 10 unique masked credit card values.

--- 

## Reflection

> This lab strengthened my ability to work with Splunk at a deeper, more technical level by understanding how raw machine data is ingested, parsed, and normalized into searchable
events. I developed hands-on experience configuring core files such as inputs.conf, props.conf, and transforms.conf, which improved my ability to control how data is collected and
structured.

I also enhanced my skills in extracting and normalizing fields from unstructured logs, allowing me to transform inconsistent data into a standardized format that supports 
efficient analysis. Additionally, I gained experience applying data masking techniques to protect sensitive information, reinforcing the importance of security and compliance in 
log management.

Overall, this lab improved my ability to manipulate and optimize data for accurate search results, strengthening my foundation in log analysis and preparing me for real-world SOC 
environments where data quality and reliability are critical for detecting and responding to security events.
