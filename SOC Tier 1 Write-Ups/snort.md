Network Security Monitoring – Snort

TryHackMe Path: SOC Level 1
Lab Topic: Snort
Date Completed: 02/05/2026

-

Executive Summary

> This lab provided hands-on experience using Snort as a network-based intrusion detection system (IDS). The exercises focused on detecting real-time threats, analyzing recorded 
traffic through PCAP files, and identifying anomalous network behavior. Through live traffic monitoring, offline packet inspection, and custom rule creation, I developed practical 
skills directly aligned with SOC Tier 1 responsibilities such as alert triage, traffic validation, and investigation documentation. Overall, this lab bridged the gap between 
theoretical knowledge and real-world network security monitoring.

-

Objectives (Completed)

> Understand IDS vs IPS concepts

> Gain familiarity with Snort operation modes

> Write and test custom IDS rules

> Detect and investigate network activity using Snort

-

Tools Used

- TryHackMe AttackBox

- Snort

- Linux Terminal

-

Analysis & Investigation

-

*** Interactive Material and VM ***
Objective

> Verify access to the virtual environment and confirm correct execution of provided scripts.

Methodology

> The easy.sh script was executed from the Task-Exercise directory to validate environment readiness.

Findings

> Script execution returned the output: “Too Easy!”

Verdict

> Successful environment validation.
No security concerns identified.

-

*** First Interaction with Snort ***
Objective

> Verify Snort installation, versioning, and rule availability.

Methodology

> Snort was executed in version-check mode and tested using two different configuration files.

Findings

> Snort build version: Build 149

> Rules loaded using snort.conf: 4,151 rules

> Rules loaded using snortv2.conf: 1 rule

Interpretation

> The significant difference in rule counts highlights how configuration files directly impact detection coverage and alert generation.

Verdict

> Expected behavior.
This confirms proper Snort installation and configuration parsing.

-

*** Operation Mode 2: Packet Logger Mode ***
Objective

> Analyze packet-level details from captured traffic to validate network behavior.

Data Source

> Snort packet logs from TASK-6 exercise

Methodology

> Snort was run in packet logger mode to capture traffic, followed by manual inspection of generated logs.

Findings

> DNS source port used to connect to port 53: 3009

> IP ID of the 10th packet: 49313

> HTTP referrer in the 4th packet:
http://www.ethereal.com/development.html

> ACK number of the 8th packet: 0x38AFFFF3

> TCP packets communicating over port 80: 41

Interpretation

> The traffic exhibited normal client-server communication patterns, including ephemeral source ports and standard TCP acknowledgment behavior.

Verdict

> Benign traffic.
No escalation required.

-

*** Operation Mode 3: IDS / IPS ***
Objective

> Detect HTTP GET requests using Snort’s IDS capabilities.

Methodology

> Traffic was generated using the default Snort configuration and analyzed through alert output.

Findings

> Detected HTTP GET methods: 2

Interpretation

> The detected requests align with expected lab-generated HTTP traffic.

Verdict

> Benign activity.

-

*** Operation Mode 4: PCAP Investigation ***
Objective

> Analyze PCAP files to evaluate alert volume and protocol behavior under different configurations.

Data Sources

> mx-1.pcap

> mx-2.pcap

> mx-3.pcap

Findings

> mx-1.pcap (default config):

Total alerts: 170

TCP segments queued: 18

HTTP response headers extracted: 3

> mx-1.pcap (snortv2.conf):

Total alerts: 68

> mx-2.pcap (default config):

Total alerts: 340

Detected TCP packets: 82

> mx-2.pcap + mx-3.pcap (combined):

Total alerts: 1,020

Interpretation

> Alert volume varied significantly depending on configuration file and traffic set, demonstrating the importance of rule tuning to balance detection coverage and noise reduction.

Verdict

> Expected detection behavior.
Highlights the operational impact of IDS configuration choices.

-

*** Snort Rule Structure and Custom Detection ***
Objective

> Create and test custom Snort rules to detect specific packet attributes.

Custom Rule Investigations

ICMP IP ID Detection

> Filtered IP ID: 35369

> Detected request type: TIMESTAMP REQUEST

TCP SYN Flag Detection

> Detected packets: 1

TCP PSH-ACK Flag Detection

> Detected packets: 218

UDP Same Source/Destination IP Detection

> Detected packets: 7

Interpretation

> Custom rules successfully identified targeted packet characteristics, demonstrating effective rule syntax usage and validation through PCAP testing.

Verdict

> Successful rule creation and validation.

-

SOC Level 1 Skills Demonstrated

> IDS/IPS monitoring and alert interpretation

> Network traffic analysis using PCAP files

> Custom Snort rule development and testing

> Packet-level inspection (TCP flags, headers, IP IDs)

> Alert validation and basic triage decision-making

> Clear technical documentation and evidence collection

- 

Reflection

> This lab strengthened my ability to operate Snort as a network-based detection tool within a SOC context. I gained hands-on experience with live traffic monitoring, offline PCAP 
analysis, and custom rule development, while also learning how configuration differences impact alert generation. These skills directly translate to SOC Tier 1 responsibilities 
such as alert triage, investigation, and documentation, and provide a strong foundation for more advanced threat-hunting and incident-response work.
