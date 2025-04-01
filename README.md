Cybersecurity Incident Response Simulator


📌 Project Overview

The Cybersecurity Incident Response Simulator is designed to help organizations detect, analyze, and respond to cyber threats in real time. It integrates AWS CloudWatch, Grafana, and a custom web application to monitor logs, identify suspicious activities, and take necessary security actions.

Features

Live Log Monitoring – Captures logs from AWS-hosted websites using CloudWatch.

Rule-Based Threat Detection – Identifies failed logins, DDoS attempts, and suspicious traffic.

Grafana Dashboard – Visualizes security events and alerts in real-time.

Incident Response Actions – Block IPs, restart servers, and take necessary security steps via the web application.

Incident Playbooks – Documented response plans for various attack scenarios.

📊 How It Works

Website logs are collected via AWS CloudWatch.

Grafana fetches and visualizes real-time logs.

Logs are identified (failed logins, suspicious patterns).

Generate Alerts & Notify Admins (Real-time alerts on threats)

Admins take action (block IPs, isolate servers, analyze reports).
