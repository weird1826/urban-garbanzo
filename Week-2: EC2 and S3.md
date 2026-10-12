<img width="1542" height="815" alt="image" src="https://github.com/user-attachments/assets/eeac64c0-05b3-413d-b0a3-3654407dcaa1" /># Getting hands on with EC2

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

### Enable Auto Scaling

Auto scaling helps the server to scale up its resources during heavy uptime. To configure, select "Launch templates" from the left pane in the EC2 dashboard and go on to create launch template.

<img width="1912" height="831" alt="image" src="https://github.com/user-attachments/assets/d751a64d-229b-4240-b966-73fc2f66c796" />

Give the launch template a name and any description:

<img width="1915" height="857" alt="image" src="https://github.com/user-attachments/assets/1df00077-54d5-4b06-af02-d14350406368" />

For the rest of the options, it is important that **they should all match the configuration of your EC2 instance** which we created above. Once done, read the summary, and Create the template:

<img width="643" height="406" alt="image" src="https://github.com/user-attachments/assets/847084ec-dffa-4bbf-b929-058b0c2da24b" />

Following up, we have to create an auto-scaling group from the left hand pane:

<img width="1912" height="832" alt="image" src="https://github.com/user-attachments/assets/79e72b0f-2e63-4d91-ad2d-98297f1cae83" />

In the first step, give the auto-scaling group a name, and select the template that we just created:

<img width="1377" height="770" alt="image" src="https://github.com/user-attachments/assets/04e03175-67b7-4626-8e29-cd2b73018f27" />

In the next step, for the networking, make sure a VPC is selected, and for Availability Zones, it is recommended to use two zones because technically that is how elasticity works at its best.

<img width="1142" height="571" alt="image" src="https://github.com/user-attachments/assets/828aae83-e060-4c8e-9d8b-e77b7c005faf" />

Step 3 is about attaching load balancers, but we do not need them for this activity. Head over to step 4 to configure group size and scaling. Set the max desired capacity as 2 for now. And we need to have a tracking policy (a trigger as when to scale). Set the metric type to CPU utilization and set target value to 50.

<img width="1077" height="737" alt="image" src="https://github.com/user-attachments/assets/d5e0890b-2361-4a41-9254-76d24c33c1ea" />

Head over to the review step and create the auto-scaling group. After a minute or so, go to Instances dashboard and there you will now see two instances running, and one of them, is from our ASG.

<img width="1905" height="897" alt="image" src="https://github.com/user-attachments/assets/9ad95e95-3aab-47ad-88ef-b4c82343eac1" />

We will connect to that instance from the browser just like we did for the previous one. Run these commands to generate CPU load:

```bash
sudo amazon-linux-extras install epel -y
sudo yum install -y stress
stress --cpu 2 --timeout 300
```

# Hands on S3 and Securing S3 bucket

AWS S3 provides cloud storage service. It is very important to secure it if an organization uses it to store crucial data. We will setup access policies, encryption at rest, and access logging. Go to S3 console.

<img width="892" height="642" alt="image" src="https://github.com/user-attachments/assets/443b6e0c-125f-4238-8e57-351c2626312c" />

From the console, click create bucket:

<img width="1897" height="542" alt="image" src="https://github.com/user-attachments/assets/07bb6b22-ad60-4142-9d36-dc97829161a1" />

On that page, simply name the bucket, and review that these settings are at default. This bucket will be used for logging purposes:

<img width="1542" height="815" alt="image" src="https://github.com/user-attachments/assets/3785ba7a-2175-4232-93d6-dd9a90cee8bf" />
<img width="1907" height="815" alt="image" src="https://github.com/user-attachments/assets/54a2afb9-621a-4b14-8d4e-b83e3410042d" />

Once again, head over to the bucket creation form. Name it something like a main bucket, indicating a distinction between the logging and main buckets. Keep all the settings the default. In the encryption settings notice this:

<img width="1573" height="366" alt="image" src="https://github.com/user-attachments/assets/a4d33d37-5f71-481b-a8c4-6269d55d1500" />

Encryption is always turned on by default. For stronger control, you may instead choose SSE-KMS and select a customer managed key. Create the bucket. For the main bucket, head over to the properties tab:

<img width="1905" height="827" alt="image" src="https://github.com/user-attachments/assets/1e2ef9fa-ebaa-4612-a3ff-a718ebb163b8" />

Scroll down to server access logs, and click "Edit":

<img width="1902" height="182" alt="image" src="https://github.com/user-attachments/assets/5be2c1b1-41b1-4e61-b9db-806f2c3e4538" />

In the edit, click on browse to select the log bucket location, and choose the one we created earlier. Save changes after:

<img width="1907" height="821" alt="image" src="https://github.com/user-attachments/assets/67b25844-602b-4403-a4f0-7d588095f882" />

Now, we will apply the principle of least privileges to the main bucket. Go to its permissions tab, and edit the bucket policy.

<img width="1901" height="835" alt="image" src="https://github.com/user-attachments/assets/d9eb7c4d-41e1-4ddc-a3fe-4fbb453ddc0c" />

Fill in these details:

<img width="1412" height="824" alt="image" src="https://github.com/user-attachments/assets/eedd84b1-b9ba-477b-ac1e-349380d7a7ff" />

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "AllowOwnerOnly",
      "Effect": "Allow",
      "Principal": { "AWS": "arn:aws:iam::<account id>:user/<iam user>" },
      "Action": ["s3:GetObject", "s3:PutObject"],
      "Resource": "arn:aws:s3:::securecc-lab2-s3-mainbuck/*"
    }
  ]
}
```

Save changes.

Test the settings by going to Objects and uploading a simple text file. You should be able to do it. 

<img width="1486" height="782" alt="image" src="https://github.com/user-attachments/assets/b5ca5773-ed3a-484c-a6f6-79f6c087c85f" />

For that same file, select it, and copy its URL:

<img width="1487" height="635" alt="image" src="https://github.com/user-attachments/assets/f8b3d1cb-bad1-4e6b-8cc2-755097b695fe" />

Use that URL in a private window, and you will get an Access Denied XML error.

<img width="1917" height="457" alt="image" src="https://github.com/user-attachments/assets/f8a8c9a7-576d-4195-91e6-d04e97c43274" />

------

That was pretty much it. Thanks!
