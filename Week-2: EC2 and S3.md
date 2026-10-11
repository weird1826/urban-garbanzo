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

### Customizing Security Groups

Click on the instance ID and it will lead you to that instance's dashboard.

<img width="1591" height="712" alt="image" src="https://github.com/user-attachments/assets/83a3d74c-1781-4cea-aa6f-4d7a8fb68340" />

On the left-hand pane, scroll down to "Network & Security" and go to Security Groups page. Click on the ID of the security group we created during setup. That SG is attached to our instance.

<img width="1913" height="816" alt="image" src="https://github.com/user-attachments/assets/22860018-3481-4ecb-8e07-3b9999f2a905" />

On the details page, select "Edit inbound rules" (which will configure the rules for incoming connections):

<img width="1637" height="762" alt="image" src="https://github.com/user-attachments/assets/9c0e2622-6182-449e-9120-d15096118cce" />

Ensure that the existing configuration looks like this image below. If it does, click "Save rules" and go back.:

<img width="1555" height="402" alt="image" src="https://github.com/user-attachments/assets/52c27fb5-184e-4787-b3e0-f18ccf7213b7" />

You can try to create your custom rules by exploring available options, or can also create new security groups and assigning rules to them. When setting up access controls, always follow the principle of Least Privilege.

### Enabling CloudWatch Monitoring & Setting up alarm

Go the dashboard of our instance ID. Scroll down a little, and switch over to the monitoring tab. There you will see live graphs of instance health. This can be very important for scenarios involving high-workloads, and maximum uptime requirements.

<img width="1902" height="827" alt="image" src="https://github.com/user-attachments/assets/06c8825c-5b2a-43e1-8618-69e02e5e7654" />

Click on manage detailed monitoring, and enable it. This will update the graphs every minute.

<img width="1897" height="835" alt="image" src="https://github.com/user-attachments/assets/543487f4-0977-4694-83c8-6777e8811c11" />

Next, search for CloudWatch, and head over its console.

<img width="1905" height="846" alt="image" src="https://github.com/user-attachments/assets/fdc2faa9-0b94-4612-bd4b-2fd8a4b41301" />

On the left-hand pane, go to Alarms, and Create an alarm.

<img width="1901" height="772" alt="image" src="https://github.com/user-attachments/assets/1e6c27ce-5f6f-4e6b-abb8-a48b28e516a7" />

On the setup page, keep the existing options, and click on select a metric button.

<img width="1902" height="825" alt="image" src="https://github.com/user-attachments/assets/8f601871-47c1-4725-bcd5-7d7d68a0665e" />

Give your graph a name and Select EC2 metric:

<img width="1757" height="801" alt="image" src="https://github.com/user-attachments/assets/f5fa299c-7115-4f2c-916d-22fe911123e9" />

Next, select per-instance metric.

<img width="1757" height="290" alt="image" src="https://github.com/user-attachments/assets/ca9a2876-e8fc-4229-ac3d-99dfeae25985" />

On the final page, search for "CPU" and click on metric suggestion. And finally, select the appropriate EC2 instance ID and the graph will update above. Click on "Select Metric".

<img width="1762" height="405" alt="image" src="https://github.com/user-attachments/assets/e157787d-34e0-44ba-aed0-9fb11ad61fad" />

The page will be updated with your selected metric. Set the period to 5 minutes and the condition as when the "CPUUtilization gets greater than 70..."

<img width="1602" height="658" alt="image" src="https://github.com/user-attachments/assets/70b69b9d-eaba-4d62-b097-70b6b91d828e" />

Under additional configuration, set datapoints to alarm 5 out of 5 - this means that within 5 minutes, the data points must fire five times in order for the alarm to dispatch:

<img width="537" height="430" alt="image" src="https://github.com/user-attachments/assets/047c2b7b-0426-4814-98ee-e289bd125186" />

Click on Next. In the next step, you can create a new notification topic. Since, we do not have one, we have to create a new one like this:

<img width="1596" height="690" alt="image" src="https://github.com/user-attachments/assets/45c4ff82-142c-4db9-8b9f-01238746c985" />

The emails you specify will receive the alerts. If you press "Create Topic" your email will get a confirmation message sent. If you do not want to set it up for this lab, simply press "remove". Head over to the next page, give your alarm a name, add a markdown description, and some tags if you want. Click next to preview the settings.

<img width="1907" height="732" alt="image" src="https://github.com/user-attachments/assets/211e5ee7-12a5-4233-bb26-5b8f0cb57f06" />

On the final step, click the "Create alarm" button to finalize it.

### Setting up Instance Level Firewall

This can be very important defense-in-depth step as this will provide an extra layer of security in case the network-level firewall or security groups configurations are misconfigured. Head over to the instance home page.

<img width="1877" height="631" alt="image" src="https://github.com/user-attachments/assets/5f542720-cd08-4d07-9388-99963e560918" />

A new tab will open with connection details. Keep this pre-configured settings and click connect:

<img width="1857" height="776" alt="image" src="https://github.com/user-attachments/assets/9d912d2c-1a5d-4ee9-aba6-8fd668f5bb68" />

Once you see the terminal page, run these commands in order:

```bash
sudo dnf install -y firewalld
sudo systemctl start firewalld
sudo systemctl enable firewalld
sudo firewall-cmd --permanent --add-service=ssh
sudo firewall-cmd --reload
sudo firewall-cmd --list-all
```

The final command should show this output:

<img width="790" height="405" alt="image" src="https://github.com/user-attachments/assets/691e86a9-541b-4bf0-b1dc-c9aee13faa03" />

