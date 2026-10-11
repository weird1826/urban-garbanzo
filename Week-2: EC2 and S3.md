# Getting hands on with EC2

EC stands for Elastic Cloud Computing. It is a part of AWS's core IaaS cloud computing infrastructure which provides virtual computing services with high elasticity.

From the Console home page, search EC2 and head over to EC2 page.

<img width="1902" height="807" alt="image" src="https://github.com/user-attachments/assets/df656266-7bd9-4b7a-b3f8-60ab0bd78867" />

On the EC2 dashboard, open the left-hand menu, and head over to the "Instances" section. It will display, in listing, all the EC2 instances that we have running. Currently, there are none. We can create one by pressing the "Launch Instances" button as shown in the image.

<img width="1912" height="867" alt="image" src="https://github.com/user-attachments/assets/12f425b1-6e7d-4e38-8b0b-53832a319bdb" />

On the setup page, give your instance any name:

<img width="1906" height="822" alt="image" src="https://github.com/user-attachments/assets/798ccece-c85d-45c7-830b-e0d46b272793" />

You can also add more tags to the instance to identify it better incase you have multiple instances running for different purposes.

The next section is about selecting application & OS images. For that, make sure you are on "Quick Start" tab. "Recent" will show the most recent OS images you might have configured before, but it is empty in our case since this is our first time. The AMIs (Amazon Machine Images) listed are Amazon Linux, MacOS, Windows, Ubuntu, Red Hat, SUSE Linux and Debian. However, apart from that, Amazon has lots and lots of different OS images which one can choose from based on their needs. To explore the images, click on "Browse more AMI options". For our task, we will stick to **Amazon Linux**. Keep the machine image selection as it is, i.e., the latest one, unless you want to go for historical images. For the architecture, one can go for x86 or ARM. We will keep it at x86.

<img width="1902" height="826" alt="image" src="https://github.com/user-attachments/assets/0d669601-8c44-4f86-82fa-2b737d755f8d" />

For the instance type next, we will keep it at, in our case, is `t3.micro`, you should keep whatever you have at your setup time. There are also many other instance types which are free, and some are paid. You can expand the dropdown to select the one if you have it in mind. Next, it is important to configure key pair for login purposes, otherwise you can't land into the machine in the first place. Select "Create new key pair".

<img width="1892" height="827" alt="image" src="https://github.com/user-attachments/assets/f3f978ab-9f62-4b54-b7dd-dc2147683672" />

Give the key pair any name you'd like. Select "RSA" for key pair type (more cryptographically resilient), and select the file format. If you are planning to connect to the VM from Linux, choose .pem, or if Windows, choose .ppk. Click on create key pair button, and the key will be downloaded to your machine.

<img width="677" height="642" alt="image" src="https://github.com/user-attachments/assets/ba7048e2-7fbe-48aa-a3af-508a6c78cb18" />

Next, for the network setup, keep the VPC to the default value. VPC stands for Virtual private Cloud. 

<img width="804" height="139" alt="image" src="https://github.com/user-attachments/assets/e4b195bc-0e43-4345-af11-1be5c82a2da1" />

The subnet dropdown might contain many options. For the sake of this activity, we can choose. You can either go for No Preference, or we can select one using the remaining options. Options have many information such as CIDR and Availability Zone (AZ). In a professional setting, choose the reliable one as per your organization's requirements. You can also create a new subnet from the Create New Subnet option. For now, we can select any one of the available ones.

<img width="1006" height="330" alt="image" src="https://github.com/user-attachments/assets/89637e7b-a40b-4f27-a27f-692d11e6a25d" />

Keep Auto-Assign Public IP to enabled. For the firewall configuration, create a new security group, give it a name, and a description. Security groups act like allow-list and deny-list for network connections. Note that in an organization settings, these fields must be descriptive for the team to assess what's actually being setup. For inbound security group rules, set type to SSH, Source type from Anywhere (which is very broad and not at all recommended for certain environments) and a description.

<img width="1006" height="567" alt="image" src="https://github.com/user-attachments/assets/da5707ed-3c6c-47f5-b5e0-0bcf51489314" />

Under storage configuration, keep the default options (which is 1 volume of 8 GiB, gp3) which typically cover free tier.

<img width="1907" height="836" alt="image" src="https://github.com/user-attachments/assets/d0337a7e-e65b-4bd0-ad90-b06d561822c1" />

Refer to the summary panel on the right side to see the overall configuration of the VM.

<img width="1897" height="826" alt="image" src="https://github.com/user-attachments/assets/62d10643-92e2-4c18-9c24-843ea0e42415" />

------

### Ext: Console-to-Code

You can perform the same steps with AWS Command Line Interface. To get an idea of what a configuration setup with CLI looks like, click on "Preview Code" button in summary.

<img width="1911" height="864" alt="image" src="https://github.com/user-attachments/assets/283f40c6-983c-41a3-a61a-93eccc2e0daa" />

If you want to integrate this creation process in an application, you can select the Format dropdown and see the available options for different languages like Python and Java.

------

Click on the Launch Instance button to deploy the instance.

<img width="1911" height="837" alt="image" src="https://github.com/user-attachments/assets/2953be01-459b-4841-9327-6cde142f0b6e" />

You can see the new instance running on the instances section.

<img width="1591" height="712" alt="image" src="https://github.com/user-attachments/assets/83bce31b-006b-4d58-abe5-c63996a30b25" />
