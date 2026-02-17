# AWS-Cross-Region-VPC-Peering-Project

🌐 AWS Cross-Region VPC Peering Project (Virginia ↔ Ohio)
📌 Project Description

This project demonstrates how to create a Cross-Region VPC Peering connection in AWS and enable private communication between EC2 instances located in different AWS regions.

The connection is established between:

N. Virginia (us-east-1) → Public Subnet EC2

Ohio (us-east-2) → Private Subnet EC2

Communication is tested using ICMP (Ping) over private IP addresses.

🎯 Objective

To allow EC2 instances in different AWS regions to communicate securely using private IP addresses without using the internet.

🛠 Services Used

* Amazon VPC

* Amazon EC2

* VPC Peering

* Route Tables

* Security Groups

⚙ Implementation Steps

Step 1: Create Virginia VPC

Region: us-east-1

CIDR: 10.0.0.0/16

Create Public Subnet

Launch EC2 instance

Example Private IP:

10.0.0.70

Step 2: Create Ohio VPC

Region: us-east-2

CIDR: 192.0.0.0/16

Create Private Subnet

Launch EC2 instance

Example Private IP:

192.0.0.249

Step 3: Create VPC Peering Connection

Go to:

VPC Dashboard
→ Peering Connections
→ Create Peering Connection


Select:

Requester VPC → Virginia

Accepter VPC → Ohio

Step 4: Accept Peering Request

Switch to Ohio Region

Click:

Accept Peering Connection


Status becomes:

Active

Step 5: Update Route Tables

Virginia Route Table:

Destination: 192.0.0.0/16
Target: VPC Peering Connection


Ohio Route Table:

Destination: 10.0.0.0/16
Target: VPC Peering Connection

Step 6: Update Security Groups

Allow ICMP traffic

Virginia EC2 Security Group:

Type: All ICMP
Source: 192.0.0.0/16


Ohio EC2 Security Group:

Type: All ICMP
Source: 10.0.0.0/16

Step 7: Test Connection

SSH into Virginia EC2

Run:

ping 192.0.0.249

✅ Output

Ping Successful

Example:

64 bytes from 192.0.0.249: icmp_seq=1 ttl=64 time=11 ms

📊 Result

* Cross-Region communication established

* Private communication successful

* No internet used

💡 Key Learnings

* VPC Peering

* Cross-Region Networking

* Route Table Configuration

* Security Group Configuration

* AWS Network Troubleshooting

🌍 Real-World Use Case

*** Application Server → Virginia

*** Database Server → Ohio

Secure private communication without internet exposure
