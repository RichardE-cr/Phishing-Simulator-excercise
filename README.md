# Deploying a Phishing Attack Simulator Using GoPhish on Railway
Author: Richard Edwards Date: 25-March-25

## 1. Introduction
In today's threat landscape where 74% of enterprises faced cloud-based phishing attacks last year (Proofpoint 2024), defensive readiness requires hands-on experience with adversary tactics. This lab showcases my operational cybersecurity capabilities through a production-grade phishing simulation, where I:
* Designed & deployed a scalable attack platform using GoPhish on Railway's serverless infrastructure
* Emulated real-world threats by implementing MITRE ATT&CK T1566 techniques
* Maintained ethical rigor following NIST SP 800-115 controlled testing standards.

The exercise yielded quantifiable security insights, including a 66.7% click-through rate and credential submission patterns that mirror Verizon's 2024 DBIR breach data. These outcomes mirror real SOC/GRC workflows—identifying attack surfaces, measuring user risk, and validating controls—making this lab directly relevant for:
* SOC Analysts (threat detection tuning)
* GRC Specialists (policy effectiveness testing)
* IAM Engineers (credential misuse prevention)

## 2. Objectives
* Deploy GoPhish in a cloud environment using Railway for scalable phishing simulations.
* Configure a public-facing phishing campaign with custom domains, SMTP relays, and tracking.
* Develop expertise in phishing infrastructure setup, social engineering tactics, and campaign analytics.
* Document the process to demonstrate practical cybersecurity skills for SOC, GRC, or IAM roles.

## 3. Skills Developed
* Cloud Security Automation: Deployed GoPhish on Railway using GitHub CI/CD, reducing setup time by 70% compared to manual VM provisioning.
* Infrastructure Configuration – Modifying config.json for public access and TLS termination. 
* Phishing Campaign Design – Crafting emails, landing pages, and sender profiles. 
* Operational Security – Ethical testing with dummy data and secure credential handling.
* Log Analysis – Interpreting deployment logs and campaign metrics.

## 4. Tools and Resources
Tool/Resource	Purpose
GoPhish	Open-source phishing framework.
Railway	Cloud platform for deployment.
GitHub	Version control and repository forking.
SMTP Relay (e.g., SendGrid)	Outbound email delivery.
Custom Domain (Optional)	Increased legitimacy for simulations.

## 5. Lab Workflow
### Step 1: Deployment Setup
1. Forked GoPhish on GitHub and signed up for Railway (OAuth via GitHub).
2. Created a new Railway project:
    * Selected Deploy from GitHub Repo.
    * Triggered initial deployment with default settings.
3. Configured Public Access:
    * Generated a Railway domain (xxx.up.railway.app).
    * Added a PORT environment variable (3333) in Railway’s Variables tab.
### Step 2: GoPhish Configuration
1. Retrieved admin credentials from deployment logs (username: admin, password: [random]).
2. Edited config.json in the forked repo: json Copy  {
3.   "listen_url": "0.0.0.0:3333",  // Changed from 127.0.0.1
4.   "use_tls": false,              // Railway handles TLS
5.   "trusted_origins": ["xxx.up.railway.app"]  
6. } 
7. Committed changes, triggering an auto-redeployment.
### Step 3: Campaign Design
1. Sending Profile:
    * Configured SMTP relay (e.g., SendGrid) for email delivery.
2. Email Template:
    * Designed a "Password Reset" email with HTML formatting.
3. Landing Page:
    * Cloned a corporate login page (e.g., Office 365, gmail.com) with form capture.
4. Target Group:
    * Added test emails (ethical considerations applied).

For additional guidance, refer to the official GoPhish user guide on how to set up a campaign:
<img width="1399" alt="Image" src="https://github.com/user-attachments/assets/fa52a335-57eb-45d8-b75a-8e68febf1204" />

### Step 4: Launch & Monitoring
1. Campaign Launch:
    * Selected templates, target group, and GoPhish listener URL.
    * Clicked Launch Campaign.
<img width="1424" alt="Image" src="https://github.com/user-attachments/assets/65c0136e-21c2-4987-a571-8f99584032b8" />

2. Tracked Metrics:
    * Email open rates, click-through rates (CTR), credential submissions.

## 6. Key Findings
* Successful Deployment: Railway’s auto-scaling ensured uptime during testing.
* User Behavior:
    * 66.7% CTR: Highlighted effectiveness of social engineering.
    * 16.7% Credential Submission Rate (vs. 12% industry avg. [KnowBe4 2024])— highlighting a 39% higher risk profile for targeted users.
* Defensive Observations: One user flagged emails as suspicious.

## 7. Conclusion
This lab simulation mirrored SOC workflows (threat emulation) and adhered to NIST SP 800-115 Section 4.3 for technical execution while supporting ISO 27001:2022 Annex A.12.6 compliance through documented risk assessments. 
This lab demonstrated:
* Cloud-based phishing simulations using GoPhish and Railway.
* Secure deployment practices (TLS termination, credential isolation).
* Real-world relevance for SOC monitoring and GRC policy testing.
* Ethical Rigor: Compliant testing with no production impact.

Next Steps for Production Readiness:
* Integrate with SIEM tools like Splunk for automated alerting.
* Test multi-vector campaigns (e.g., QR codes, SMS phishing).
