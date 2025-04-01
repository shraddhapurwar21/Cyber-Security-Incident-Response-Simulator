## 🚀 Setting Up Grafana 
Grafana will help visualize real-time logs from CloudWatch for monitoring threats and generating alerts for suspicious activities.


**1️⃣ Install Grafana on AWS EC2**

Step 1: Update & Install Grafana
Run the following commands (Amazon Linux 2023):

    sudo dnf update -y
    
    sudo tee /etc/yum.repos.d/grafana.repo <<EOF
    [grafana]
    name=Grafana Repository
    baseurl=https://packages.grafana.com/oss/rpm
    repo_gpgcheck=1
    enabled=1
    gpgcheck=1
    gpgkey=https://packages.grafana.com/gpg.key
    EOF
    
    sudo dnf install -y grafana
**2️⃣ Start & Enable Grafana**

Step 2: Start Grafana Service
Run:

    sudo systemctl start grafana-server
    sudo systemctl enable grafana-server
Check status:

    sudo systemctl status grafana-server
**3️⃣ Allow Grafana in AWS Security Groups**

Step 3: Open Port 3000 in AWS Security Group

1. Go to AWS Console → EC2 → Security Groups
2. Select your instance's security group
3. Click Inbound Rules → Edit
4. Add a new rule:
   - Type: Custom TCP
   - Port: 3000
   - Source: 0.0.0.0/0 (or restrict to your IP)
  
6. Click Save Rules

**4️⃣ Access Grafana Web UI**

Step 4: Open Grafana in Browser
1. Open Grafana in the browser
   
       http://<EC2-Public-IP>:3000
3. Login with default credentials:
   - Username: admin
   - Password: admin (change it after first login)

**5️⃣ Connect CloudWatch to Grafana**

Step 5: Add CloudWatch as a Data Source

1. Open Grafana Dashboard
2. Go to Configuration → Data Sources
3. Click "Add data source" → Select CloudWatch
4. Under Auth Provider, select AWS SDK Default (since we are using an IAM role)
5. Click Save & Test

    If successful, your Grafana is now connected to CloudWatch logs!

**6️⃣ Create Dashboard**

Step 6: Create a Grafana Dashboard

1. Go to Dashboards → Add Visualisations
2. 

** Import a Pre-Built Dashboard (Optional)**

1. Go to Dashboards → Manage → Import
2. Click Upload JSON File
3. Select the JSON file
4. Choose CloudWatch as the Data Source
5. Click Import

**7️⃣ Verify Logs in Grafana**

Step 7: Check If Logs Are Flowing

1. Go to Explore → Select CloudWatch
2. Run a query:


        fields @timestamp, @message |
        sort @timestamp desc |
        limit 50

3. Check if logs are visible

____
Grafana Setup Complete!

🔹 Now, Grafana fetches logs from CloudWatch for real-time monitoring.

🔹 You can create alerts, detect threats, and take action from the dashboard.
