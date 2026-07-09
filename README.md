#  Cloud-Native Re-Architecture of the vProfile Application on AWS

A production-style modernization of the **vProfile multi-tier Java application**, transforming a traditional VM-based deployment into a cloud-native architecture using AWS managed services (PaaS).

This project demonstrates the evolution of the application through three deployment stages:

- Traditional Virtual Machines
- AWS Lift & Shift Migration
- Cloud-Native AWS Architecture (Current)

---

# 📖 Overview

After successfully migrating the vProfile application to AWS using a Lift & Shift strategy, I further modernized the application by replacing self-managed infrastructure with AWS managed services.

The objective was to improve:

- Scalability
- Availability
- Operational efficiency
- Reliability
- Infrastructure management

The application was redesigned to leverage Platform as a Service (PaaS) offerings while preserving the original business functionality.

---

# 🏗️ Architecture

<p align="center">
<img src="docs/architecture.png" width="1000">
</p>

---

# ☁️ AWS Services Used

- Amazon Route 53
- Amazon CloudFront *(Configuration in Progress)*
- AWS Elastic Beanstalk
- Amazon EC2
- Elastic Load Balancer
- Amazon RDS (MySQL)
- Amazon MQ (RabbitMQ)
- Amazon ElastiCache (Memcached)
- Amazon S3
- Amazon CloudWatch
- IAM

---

# ⚙️ Technology Stack

| Category | Technologies |
|-----------|--------------|
| Cloud | AWS |
| Compute | Amazon EC2 |
| PaaS | AWS Elastic Beanstalk |
| Load Balancing | Elastic Load Balancer |
| Database | Amazon RDS MySQL |
| Messaging | Amazon MQ (RabbitMQ) |
| Caching | Amazon ElastiCache (Memcached) |
| Storage | Amazon S3 |
| Monitoring | Amazon CloudWatch |
| DNS | Amazon Route 53 |
| CDN | Amazon CloudFront |
| Web Server | Apache Tomcat |
| Language | Java |

---

# 🏛️ Architecture Components

## 🌐 DNS & Content Delivery

- Amazon Route 53 manages public DNS.
- Amazon CloudFront is introduced as the CDN layer (under implementation).
- Requests are forwarded to Elastic Load Balancer.

---

## 🚀 Application Layer

The application is deployed using **AWS Elastic Beanstalk**, which automatically provisions and manages:

- EC2 Instances
- Elastic Load Balancer
- Auto Scaling Group
- Health Monitoring

Application artifacts are stored in Amazon S3 and deployed through Elastic Beanstalk.

---

## ⚖️ Load Balancing & Auto Scaling

Elastic Beanstalk automatically configures

- Elastic Load Balancer
- Auto Scaling Group

Current scaling configuration

- Minimum Instances : 1
- Maximum Instances : 2

---

## 🗄️ Data Layer

Application data is stored in

- Amazon RDS (MySQL)

Benefits

- Automated backups
- Managed database administration
- Improved availability
- Reduced maintenance

---

## 📨 Messaging Layer

RabbitMQ is migrated from self-managed EC2 instances to

- Amazon MQ

Benefits

- Managed broker service
- Simplified maintenance
- Improved reliability

---

## ⚡ Caching Layer

Application caching is provided using

- Amazon ElastiCache (Memcached)

This improves response time while reducing database load.

---

## 📦 Storage

Amazon S3 stores

- Application deployment artifacts
- Elastic Beanstalk application versions

---

## 📊 Monitoring

Amazon CloudWatch provides

- Instance monitoring
- Elastic Beanstalk health monitoring
- Performance metrics
- Application logs

---

# 🔄 Deployment Workflow

```
Users
   │
   ▼
Route 53
   │
   ▼
CloudFront
   │
   ▼
Elastic Load Balancer
   │
   ▼
Elastic Beanstalk
   │
   ▼
Auto Scaling EC2 Instances
   │
   ├──────────────┐
   ▼              ▼
Amazon MQ     Amazon ElastiCache
   │              │
   └──────┬───────┘
          ▼
     Amazon RDS
          ▲
          │
      Amazon S3
(Application Artifacts)

CloudWatch
      │
Monitors Entire Stack
```

---

# 🚀 Key Improvements

- Migrated from self-managed infrastructure to AWS managed services
- Implemented Platform as a Service (PaaS) architecture
- Automated application deployment using Elastic Beanstalk
- Configured Auto Scaling and Load Balancing
- Migrated MySQL to Amazon RDS
- Migrated RabbitMQ to Amazon MQ
- Integrated Amazon CloudWatch monitoring
- Reduced operational overhead
- Improved scalability and fault tolerance

---

# 🧠 Challenges Faced

- IAM Role and Instance Profile configuration
- Elastic Beanstalk environment debugging
- RabbitMQ connectivity issues
- Application startup failures
- Load Balancer health check troubleshooting
- CloudFront integration limitations (AWS Free Tier)
- Cloud environment configuration adjustments

---

# 📚 Key Learnings

- Lift & Shift vs Cloud-Native Architecture
- AWS Elastic Beanstalk internals
- Managed database services
- Managed messaging services
- Auto Scaling strategies
- CloudWatch monitoring
- Cloud-native application deployment
- Distributed system troubleshooting

---

# 📁 Repository Structure

```
vprofile-cloud-native/
│
├── docs/
│   ├── architecture.png
│   └── screenshots/
├── deployment/
├── scripts/
├── README.md
└── LICENSE
```

---

# 🔮 Future Improvements

- Complete CloudFront integration
- HTTPS using ACM
- CI/CD with GitHub Actions
- Infrastructure as Code using Terraform
- Amazon EKS migration
- GitOps with Argo CD
- Prometheus & Grafana monitoring

---

# 👨‍💻 Author

**Eranga Kavishanka**

- AWS Certified Cloud Practitioner (AWS CCP)
- Kubernetes and Cloud Native Associate (KCNA)
- Software Engineering Undergraduate
- DevOps | Cloud | Site Reliability Engineering (SRE)

---

⭐ If you found this project useful, consider giving it a Star!
