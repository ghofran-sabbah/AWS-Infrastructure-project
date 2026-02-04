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
![9160a9bc-9467-49cb-9d1f-d45a24478bb9](https://github.com/user-attachments/assets/b7404ada-6c21-4686-a119-d16c8502a707)



