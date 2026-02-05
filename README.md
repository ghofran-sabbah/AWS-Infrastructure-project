# AWS-Infrastructure-project
​# AWS Scalable Web Infrastructure Project

​## Task 1: Networking - VPC Setup
**Description:** I built a custom Virtual Private Cloud (VPC) to provide a secure and isolated network environment for the cloud resources

* **VPC Configuration:** CIDR block 10.0.0.0/16
* **Subnets:** Created public and private subnets across different Availability Zones for high availability
* **Internet Gateway:** Attached an IGW to enable communication between the VPC and the internet
* VPC Resourses Map:
* ![88df9da2-9752-44f9-82ee-40bf99d7cea8](https://github.com/user-attachments/assets/b3b0bb3b-14e9-49de-a931-a15777f1bb69)
---
## Task 2: High Availability - NAT Gateways Setup
**Description:** I implemented redundant NAT Gateways to provide secure outbound internet connectivity for resources located in private subnets.

* **NAT Gateway Deployment:** Created two public NAT Gateways named `NAT Gateway A` (in `us-east-1a`) and `NAT Gateway B` (in `us-east-1b`).
* **Elastic IP Allocation:** Allocated and assigned a static Elastic IP address to each NAT Gateway during creation.
* **Route Table Configuration:** Created two private route tables, `Private_RT_1` and `Private_RT_2`, and added a default route (`0.0.0.0/0`) pointing to the respective NAT Gateways.

### NAT Gateways Status:
![9160a9bc-9467-49cb-9d1f-d45a24478bb9](https://github.com/user-attachments/assets/86424da0-3ac2-48a4-95a0-ad4fdb464c26)

### Private Route Table Configuration:
![f1ab2244-894e-44ae-9eb1-3a41dab3b69e](https://github.com/user-attachments/assets/558354d7-7a1f-48e4-879b-f5776dc8667e)

---

## Task 3: Running the Servers & Verification
**Description:** In this step, I started the web servers and made sure everything was working correctly through the terminal.

* **Secure Access:** I used the `ec2tossm` role to log into the servers safely without needing a password or SSH key.
* **Auto-Setup:** I used a script (User Data) to automatically install the Web Server (Apache) as soon as the servers started.
* **Fixing Connections:** I updated the Network settings (Route Table) to make sure the servers could reach the internet to download the necessary files.
* **Final Check:** I used the terminal to confirm that the web service is **Active** and the website is running perfectly.

### System Verification :
![836de79b-b8ef-42bd-8764-131ed6a395a0](https://github.com/user-attachments/assets/4adee029-02a2-4c1d-96c9-7cda6eecdb58)

### IAM Role & EC2 Status:
![2054e589-8001-48c4-873d-847f42c61b88](https://github.com/user-attachments/assets/246be054-371c-46f6-863b-1b369cf10447)
![e6d96d28-aebb-4930-8ab1-2dda9664b35d](https://github.com/user-attachments/assets/63792632-e854-4d3f-b112-8b73c42b7759)

---

## Task 4: High Availability & Load Balancing
**​Description:** In this step, I configured the infrastructure to handle high traffic and ensure constant availability using an Application Load Balancer.

* **​Target Group:** I created the WebTG group, registered both web instances, and optimized health check settings for immediate issue detection.
  ![5dcc74d9-5ea2-4487-9f3e-7b0e76fbb4c9](https://github.com/user-attachments/assets/251c89cb-04b3-4c19-9f4d-62746a6e76a5)

​* **Security Group:** I established the ALBSG to allow public HTTP traffic on Port 80 while maintaining backend isolation.
![5e1af774-07c2-43df-ab32-894d64c73061](https://github.com/user-attachments/assets/fbd6eaa8-bdb5-4adc-aaf0-41326bd5b08d)

* **​Load Balancer:** I configured the WebALB to distribute traffic across public subnets, ensuring high availability for the application.
  ![1b51ba43-561e-4386-93d3-dbbbbc6514e6](https://github.com/user-attachments/assets/11987a4f-d653-4522-8de7-1182f4d9cbdf)
 * **Note:** I completed all configurations, but final provisioning is pending AWS account verification, as shown in the error log above.

   ---
   
## Task 5: Final AWS Project Summary
​This task demonstrates a fully automated and secured cloud infrastructure using AWS Auto Scaling and Security Best Practices.
​1. Fleet Automation (Instances)
![dc6efa1a-3c04-456a-848d-5362436893fd](https://github.com/user-attachments/assets/9f5de9a7-8bc3-41cc-ae01-978178cc493f)

​What it shows: The system automatically launched 4 running instances.
​High Availability: These servers are split between two locations (AZ 1a & 1b) to ensure the site never goes down.
​Cleanup: Old manual servers were successfully Terminated.
​2. Scaling Logic (ASG)
​![49fbb955-1359-4546-8e4d-4f01af3414ed](https://github.com/user-attachments/assets/bbb4d081-0dba-4b0c-bc99-aec20d7f8602)

​What it shows: I configured the Auto Scaling Group to keep 4 servers active, with the ability to scale between 2 and 6 depending on traffic.
​3. Security Lockdown (WebSG)
![2bb58f23-e1c6-4bf6-be81-bdac8c231f2f](https://github.com/user-attachments/assets/fde82608-5844-457c-b9e3-3e8885c86c7d)

​What it shows: I locked the servers so they only accept traffic from the Load Balancer (ALBSG).
​Benefit: This protects the servers from direct attacks from the internet.
​4. Load Balancer Integration (Target Group)
![b1767629-12c8-4ae0-9297-6ea8a43353dc](https://github.com/user-attachments/assets/927e41fd-6b35-45e3-be70-066b99d31f51)

​What it shows: All 4 servers are successfully linked to the Target Group.
## ​Note : The status appears as 'Unused' because the Load Balancer is undergoing final activation by AWS. However, the technical link is correctly configured.



