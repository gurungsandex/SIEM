# SIEM
SIEM Lab with Microsoft Sentinel 


My Home Lab - SIEM Lab with Microsoft Sentinel on Azure
Project Overview: In this project, I set up a comprehensive cybersecurity lab on the Azure cloud platform. I created a vulnerable Windows virtual machine (VM) to simulate unauthorized login attempts. The logs from the VM were forwarded to a central Log Analytics Workspace (LAW), which was then connected to Microsoft Sentinel (SIEM). I enriched the logs with geographic data and created an attack map to visualize where the attacks were originating from.
This project serves as an excellent opportunity for anyone looking to learn cybersecurity, SIEM (Security Information and Event Management), and log analysis using freely available cloud resources. It demonstrates how to build a home lab on Microsoft Azure by deploying a vulnerable Windows virtual machine (VM), capturing security logs, and analyzing potential threats with Microsoft Sentinel.

Step 1: Set Up Azure Subscription
Azure Free Subscription: I started by creating a free Azure subscription. It's simple to obtain a free 30-day subscription with valuable features. However, be sure to cancel the subscription and remove virtual machines and resources once your project or work is complete. Otherwise, you may incur charges if the resources remain active or if the free subscription period is extended.
Azure Free Subscription Link


Step 2: Create Resource Group and Network Infrastructure
Resource Group: I created a resource group to organize all resources for the project in a centralized location on Azure.
A Resource Group is a container that holds related resources for an Azure solution, helping in resource management and access control.
Virtual Network & Subnet: I created a virtual network (VNet) with a connected subnet to provide secure communication between the virtual machine and other resources in the project.







Step 3: Create a Vulnerable Windows Virtual Machine (VM)





The virtual machine that was intentionally made vulnerable.



Logging to virtual machine 

Turn off the firewall security settings  to make the machine vulnerable for lab purpose. 


Unauthorized login attempts made on the machine, which will later be analyzed in the lab.




Unauthorized or unsuccessful login attempts recorded in the Event Viewer with event ID 4625. 


Step 4: Set Up Log Analytics Workspace (LAW)
Log Analytics Workspace: I created a Log Analytics Workspace (LAW) to act as the central log repository.
The LAW stores and queries logs from various resources, acting as the central point for log collection.
Log Forwarding: I configured the Windows VM to forward its logs (e.g., failed login attempts) to the LAW, which would store them for analysis.

Step 5: Connect Microsoft Sentinel to Log Analytics Workspace (SIEM Setup)
Microsoft Sentinel: I deployed Microsoft Sentinel, which is a Security Information and Event Management (SIEM) solution, to monitor and analyze the forwarded logs from the VM.
SIEM: A SIEM platform collects and analyzes data from various sources to detect potential threats and security breaches.
Sentinel Integration: I connected Microsoft Sentinel to the LAW, so Sentinel could access the logs and provide insights into potential security threats.














Step 6: Query Logs and Monitor Unauthorized Access Attempts



Log Analysis with KQL (Kusto Query Language): Using Sentinel’s query capabilities, I analyzed the logs for failed login attempts. I wrote a simple KQL query to find events related to unauthorized access:

 SecurityEvent | where EventId == 4625  // Event ID 4625 corresponds to failed login attempts
Detecting Attacks: I observed the logs that indicated failed login attempts (Event ID 4625), confirming unauthorized access attempts to the vulnerable VM.

Step 7: Create and Upload Watchlist with Geolocation Data
GeoIP Watchlist: I uploaded a watchlist containing geographic data (GeoIP) that matched IP addresses to locations (e.g., country, city).
A Watchlist is a collection of data (such as IP addresses) that can be referenced during queries to enrich the logs with additional context.








Geo-enrichment: With this watchlist, Sentinel enriched the logs, allowing me to trace where the attacks were coming from (e.g., specific countries or regions).

Why This Project?
Hands-On Learning: Ideal for exploring cloud security, SIEM, and threat intelligence.
Freely Available Resources: Built using Azure’s free-tier services, making it accessible for learners.
Practical Security Experience: Simulates real-world attack scenarios and teaches log analysis with KQL (Kusto Query Language).
Resume & Portfolio Boost: A valuable project for cybersecurity students, job seekers, and security enthusiasts.
A special thanks to Josh Madakor for providing such an incredible learning opportunity. His content continues to inspire and guide aspiring cybersecurity professionals in their journey. 

