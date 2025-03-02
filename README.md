# My Home Lab - SIEM Lab with Microsoft Sentinel on Azure
Project Overview: In this project, I set up a comprehensive cybersecurity lab on the Azure cloud platform. I created a vulnerable Windows virtual machine (VM) to simulate unauthorized login attempts. The logs from the VM were forwarded to a central Log Analytics Workspace (LAW), which was then connected to Microsoft Sentinel (SIEM). I enriched the logs with geographic data and created an attack map to visualize where the attacks were originating from.

This project serves as an excellent opportunity for anyone looking to learn cybersecurity, SIEM (Security Information and Event Management), and log analysis using freely available cloud resources. It demonstrates how to build a home lab on Microsoft Azure by deploying a vulnerable Windows virtual machine (VM), capturing security logs, and analyzing potential threats with Microsoft Sentinel.

# Step 1: Set Up Azure FREE Subscription
Azure Free Subscription: I started by creating a free Azure subscription. It's simple to obtain a free 30-day subscription with valuable features. However, be sure to cancel the subscription and remove virtual machines and resources once your project or work is complete. Otherwise, you may incur charges if the resources remain active or if the free subscription period is extended.
![1](https://github.com/user-attachments/assets/9a468458-45bc-48bc-9f06-78e9e1c0fce6)

# Step 2: Create Resource Group and Network Infrastructure
Resource Group: I created a resource group to organize all resources for the project in a centralized location on Azure.
A Resource Group is a container that holds related resources for an Azure solution, helping in resource management and access control.
Virtual Network & Subnet: I created a virtual network (VNet) with a connected subnet to provide secure communication between the virtual machine and other resources in the project.
![2](https://github.com/user-attachments/assets/8ec83477-e126-49a5-ab38-ffca82a7bbe7)
![3](https://github.com/user-attachments/assets/6eb9f128-94e1-448b-86a0-d91f8cfff407)
![4](https://github.com/user-attachments/assets/6b904fbe-ece9-43eb-8037-043a283b773c)
![5](https://github.com/user-attachments/assets/7da11edf-3619-4940-832b-677a034bf1ed)
![6](https://github.com/user-attachments/assets/b0a23d19-cb3c-4388-8316-96a5a1df184b)
![7](https://github.com/user-attachments/assets/9ffc37f1-d0f6-4fdf-9ef2-443d535d8bc2)

# Step 3: Create a Vulnerable Windows Virtual Machine (VM)
![8](https://github.com/user-attachments/assets/08048d0c-33e7-453c-b0de-d230b1fdd6a2)
![9](https://github.com/user-attachments/assets/488138a7-0264-43d1-b2f9-a1e1a1ee8a93)
![10](https://github.com/user-attachments/assets/de674f95-9ba6-49c6-9949-c1cbb71272a9)
![11](https://github.com/user-attachments/assets/6a44f398-62bd-4b7f-bcc3-0b7423d3c784)
![12](https://github.com/user-attachments/assets/f568ff0e-f8cd-4bd0-be30-83c896a1422a)

The virtual machine that was intentionally made vulnerable.
![13](https://github.com/user-attachments/assets/85aec9bb-aac5-43f4-9fce-63f7c69de63f)
![14](https://github.com/user-attachments/assets/ea0a1f55-1f4a-42c9-9976-c77789adfe66)

Logging to virtual machine 
![15](https://github.com/user-attachments/assets/5bdabd2a-e2d4-4f38-ab23-c3fb3f14dca7)

Turn off the firewall security settings  to make the machine vulnerable for lab purpose. 
![16](https://github.com/user-attachments/assets/76864706-ea39-4930-baa3-da7537fa79b4)

Unauthorized login attempts made on the machine, which will later be analyzed in the lab.
![17](https://github.com/user-attachments/assets/09c87ad8-9ec1-4ce0-992a-7f894ef05837)
![18](https://github.com/user-attachments/assets/f85c65c3-a8f6-4705-bafb-dba486dfe40d)

Unauthorized or unsuccessful login attempts recorded in the Event Viewer with event ID 4625. 
![19](https://github.com/user-attachments/assets/769d9440-62b5-425e-8c2f-541c5cba053c)

# Step 4: Set Up Log Analytics Workspace (LAW)
Log Analytics Workspace: I created a Log Analytics Workspace (LAW) to act as the central log repository.
The LAW stores and queries logs from various resources, acting as the central point for log collection.
Log Forwarding: I configured the Windows VM to forward its logs (e.g., failed login attempts) to the LAW, which would store them for analysis.
![20](https://github.com/user-attachments/assets/6bc24555-5809-4eef-a26d-9dbb0a543470)

# Step 5: Connect Microsoft Sentinel to Log Analytics Workspace (SIEM Setup)
Microsoft Sentinel: I deployed Microsoft Sentinel, which is a Security Information and Event Management (SIEM) solution, to monitor and analyze the forwarded logs from the VM.
SIEM: A SIEM platform collects and analyzes data from various sources to detect potential threats and security breaches.
Sentinel Integration: I connected Microsoft Sentinel to the LAW, so Sentinel could access the logs and provide insights into potential security threats.
![21](https://github.com/user-attachments/assets/dfad7102-8156-49cc-8b0c-8113eb950aad)
![22](https://github.com/user-attachments/assets/49bcd1f3-2bb3-4e4b-8236-e0311baed7b5)
![23](https://github.com/user-attachments/assets/4a0f3e7f-8070-4fe8-88d3-32eba0ecc053)
![24](https://github.com/user-attachments/assets/caca32a7-8710-45f6-8e98-7c8786eed141)
![25](https://github.com/user-attachments/assets/c8599cdf-cc04-400b-9b03-5ebe7c0d201b)
![26](https://github.com/user-attachments/assets/d5d1c487-3cea-4aec-9074-cf8eccadbb75)
![27](https://github.com/user-attachments/assets/8bc9ce78-a59f-459c-b7c2-ed5f29e23a33)
![28](https://github.com/user-attachments/assets/07eda9c2-1867-486d-8f3d-e0503bec13af)

# Step 6: Query Logs and Monitor Unauthorized Access Attempts
![29](https://github.com/user-attachments/assets/b72c8c54-a707-4a24-a943-b76092793a72)
![30](https://github.com/user-attachments/assets/1a1dbcdd-a46c-489b-9c27-2f6fafd7752b)

Log Analysis with KQL (Kusto Query Language): Using Sentinel’s query capabilities, I analyzed the logs for failed login attempts. I wrote a simple KQL query to find events related to unauthorized access:
 SecurityEvent | where EventId == 4625  // Event ID 4625 corresponds to failed login attempts
Detecting Attacks: I observed the logs that indicated failed login attempts (Event ID 4625), confirming unauthorized access attempts to the vulnerable VM.
![31](https://github.com/user-attachments/assets/4ec593d0-a398-4765-a559-e0cd314b6f3b)

# Step 7: Create and Upload Watchlist with Geolocation Data
GeoIP Watchlist: I uploaded a watchlist containing geographic data (GeoIP) that matched IP addresses to locations (e.g., country, city).
A Watchlist is a collection of data (such as IP addresses) that can be referenced during queries to enrich the logs with additional context.
![32](https://github.com/user-attachments/assets/6d5191b4-4233-4f4e-a3d5-16976b1a07d7)
![33](https://github.com/user-attachments/assets/c68ce106-43c9-4c85-98d0-6a2e09813e0c)
![34](https://github.com/user-attachments/assets/2aa6cf82-a41b-4bb9-99b3-fc67ca394dab)
![35](https://github.com/user-attachments/assets/14da68e9-949f-4857-b77f-fa10d2b6b3a8)
![36](https://github.com/user-attachments/assets/7049c167-4e0a-43d7-9904-8094892bb64e)
![37](https://github.com/user-attachments/assets/c0deb020-e233-4f3f-892e-99bf81a7c1ec)

Geo-enrichment: With this watchlist, Sentinel enriched the logs, allowing me to trace where the attacks were coming from (e.g., specific countries or regions).
![38](https://github.com/user-attachments/assets/422de643-59e2-437a-aa8b-88e28e6ff5fc)

# Why This Project?
Hands-On Learning: Ideal for exploring cloud security, SIEM, and threat intelligence.
Freely Available Resources: Built using Azure’s free-tier services, making it accessible for learners.
Practical Security Experience: Simulates real-world attack scenarios and teaches log analysis with KQL (Kusto Query Language).
Resume & Portfolio Boost: A valuable project for cybersecurity students, job seekers, and security enthusiasts.
A special thanks to Josh Madakor for providing such an incredible learning opportunity. His content continues to inspire and guide aspiring cybersecurity professionals in their journey. 

