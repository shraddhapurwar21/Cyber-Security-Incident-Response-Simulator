## 🚀 Hosting a Website on AWS EC2 (Amazon Linux)
This guide will walk you through deploying a website on an AWS EC2 instance using Apache.


**1️⃣ Launch an AWS EC2 Instance**

Step 1: Create & Configure EC2

1. Go to AWS Console → EC2 → Launch Instance
2. Choose Amazon Machine Image (AMI):
3. Select Amazon Linux 2 AMI
4. Choose Instance Type: 
   - t2.micro (Free Tier Eligible)
6. Configure Security Group:
   - Allow HTTP (Port 80) and SSH (Port 22)
7. Create & Download a Key Pair for SSH access
8. Click Launch Instance


**2️⃣ Connect to EC2 via SSH**

Step 2: SSH into Your Instance
Run:

    ssh -i "your-key.pem" ec2-user@your-ec2-public-ip


**3️⃣ Install & Start Apache Web Server**

Step 3: Install Apache
Run the following commands to install Apache:

    sudo yum update -y
    sudo yum install -y httpd

Start and enable the Apache service:

    sudo systemctl start httpd
    sudo systemctl enable httpd
    
Check if Apache is running:

    sudo systemctl status httpd


**4️⃣ Allow HTTP Traffic in Security Group**

Step 4: Update AWS Security Group

1. Go to AWS Console → EC2 → Security Groups
2. Select your instance’s Security Group
3. Click Inbound Rules → Edit
4. Add a new rule:
   - Type: HTTP
   - Protocol: TCP
   - Port: 80
   - Source: 0.0.0.0/0 (for public access)
6. Click Save Rules


**5️⃣ Deploy Your Website**

Step 5: Upload Website Files
Move to the web directory:

    cd /var/www/html
Add your webpage



**6️⃣ Restart Apache & Verify Website**

Step 6: Restart Apache
Run:

    sudo systemctl restart httpd
Now, open your browser and visit:

    http://your-ec2-public-ip

___

✅ Website Hosting Complete!
- Your website is now hosted on AWS EC2.
-  You can now enable logging and integrate it with CloudWatch & Grafana.

