## 🚀 Setting Up AWS CloudWatch Logs

CloudWatch will collect and store logs from your web server (Apache/Nginx) running on AWS EC2. Follow these steps to enable log monitoring.

**1️⃣ Enable CloudWatch Logs on EC2**

   Step 1: Install the CloudWatch Agent
   Run the following commands on your EC2 instance (Amazon Linux):

    sudo yum update -y

    sudo yum install -y amazon-cloudwatch-agent

**2️⃣ Configure CloudWatch Agent**

  Step 2: Create a CloudWatch Agent Config File
  Create a configuration file for the CloudWatch Agent:

    sudo nano /opt/aws/amazon-cloudwatch-agent/etc/cloudwatch-config.json

Paste the following (modify as needed):

    {
    "agent": {
      "metrics_collection_interval": 60
    },
    "logs": {
      "logs_collected": {
        "files": {
          "collect_list": [
            {
              "file_path": "/var/log/httpd/access_log",
              "log_group_name": "ApacheAccessLogs",
              "log_stream_name": "{instance_id}"
            },
            {
              "file_path": "/var/log/httpd/error_log",
              "log_group_name": "ApacheAccessLogs",
              "log_stream_name": "{instance_id}"
            }
          ]
        }
      }
    }
    }
Save and exit (CTRL + X, then Y, then ENTER).


**3️⃣ Start CloudWatch Agent**
 Step 3: Apply & Start the CloudWatch Agent
 Run:

    sudo systemctl start amazon-cloudwatch-agent
    sudo systemctl enable amazon-cloudwatch-agent
    
Check Status:
    
    sudo systemctl start amazon-cloudwatch-agent
**4️⃣ Verify Logs in AWS Console**

  Step 4: Check CloudWatch Logs
1. Go to AWS Console → CloudWatch → Logs
2. Open Log Groups
3. Look for "ApacheAccessLogs"
4. Click on the log stream to view live logs


✅ CloudWatch Setup Complete!

  Now, logs are streaming from EC2 to CloudWatch.
