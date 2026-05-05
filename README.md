# ICS-344: Information Security — DVSA Course Project
### King Fahd University of Petroleum and Minerals (KFUPM)
**Course:** ICS-344 — Term 252  
**Project:** DVSA Vulnerability Discovery and Remediation  
**AWS Region:** us-east-1 (N. Virginia)

---

## 📋 Project Overview

This repository contains the full vulnerability analysis, exploitation demonstrations, fixes, and verification for the **OWASP Damn Vulnerable Serverless Application (DVSA)** deployed on AWS. The project covers all 10 official vulnerability lessons, including reproduction steps, proof of exploit, code/config changes, and post-fix verification.

> ⚠️ **Warning:** DVSA is intentionally vulnerable. It must only be deployed in a **non-production** AWS account. This project is for educational purposes only within the ICS-344 course.

---

## 👥 Team Members

| Name | Student ID | Lesson |
|------|-----------|--------|
| Eyad Shahat | s202250640 | 5,8,9 |
| Faisal Baeshen | 202261280 | 4,7 |
| Faisal Bayounis | 202267880 | 1,2,6 |
| Turki Alyamani | 202162910 | 3,10 |

---

## 🏗️ Architecture

DVSA runs entirely on AWS using a serverless architecture:

```
Browser → S3 (Frontend) → API Gateway → Lambda Functions → DynamoDB
                                      ↕
                               Amazon Cognito (Auth)
```

| Component | Service |
|-----------|---------|
| Frontend | Amazon S3 (static website) |
| API | Amazon API Gateway |
| Backend | AWS Lambda |
| Database | Amazon DynamoDB |
| Auth | Amazon Cognito |
| Email | Amazon SES |

---

## 🔐 10 Official Vulnerability Lessons

| # | Vulnerability | Status | Fix Applied |
|---|--------------|--------|-------------|
| 1 | Event Injection | ✅ Done | Removed unsafe deserialization |
| 2 | Broken Authentication | ✅ Done | JWT signature verification |
| 3 | Sensitive Data Exposure | ✅ Done | Restricted S3 signed URLs |
| 4 | Insecure Cloud Configuration | ✅ Done | Hardened S3 bucket policy |
| 5 | Broken Access Control | ✅ Done | DynamoDB ConditionExpression |
| 6 | Denial of Service | ✅ Done | Rate limiting + throttling |
| 7 | Over-Privileged Functions | ✅ Done | IAM least privilege |
| 8 | Logic Vulnerabilities | ✅ Done | Atomic ConditionExpression lock |
| 9 | Vulnerable Dependencies | ✅ Done | Replaced node-serialize |
| 10 | Unhandled Exceptions | ✅ Done | Centralized error handling |

---

## 📁 Repository Structure

```

├── Demos
├── DVSA_Security_Presentation
├── lesson-01
│   
├── lesson-02 
│   
├── lesson-03
│    
├── lesson-04
│    
├── lesson-05
│                   
├── lesson-06
│     
├── lesson-07
│           
├── lesson-08
│            
├── lesson-09
│      
├── lesson-10
│
├── README.md

---

## 🚀 Quick Start

### Prerequisites
- AWS Account (non-production)
- AWS CLI v2 installed
- Node.js (for Claude Code)
- curl, python3, jq

### Deploy DVSA
```bash
# 1. Open AWS Console → Serverless Application Repository
# 2. Search for "OWASP DVSA"
# 3. Check "Show apps that create custom IAM roles"
# 4. Fill in AdminEmail and WebsiteBucketPrefix
# 5. Deploy and copy WebsiteURL from CloudFormation Outputs
```

### Setup Environment
```bash
export API="https://<api-id>.execute-api.us-east-1.amazonaws.com/dvsa/order"
export USER_ID="<your-cognito-user-id>"
export TOKEN="<your-jwt-token>"
```

---



## 🛡️ Security Principles Applied

| Principle | Applied In |
|-----------|-----------|
| **Defense in Depth** | All lessons — controls at every layer |
| **Least Privilege** | Lesson 7 — IAM role restrictions |
| **Atomicity** | Lessons 5 & 8 — DynamoDB ConditionExpression |
| **Input Validation** | Lessons 1, 9, 10 |
| **Secure Authentication** | Lesson 2 — JWT signature verification |
| **Fail Secure** | Lesson 10 — Generic error messages |

---

## 📚 Resources

- [OWASP DVSA GitHub](https://github.com/OWASP/DVSA)
- [OWASP DVSA Project](https://owasp.org/www-project-dvsa/)
- [AWS Lambda Docs](https://docs.aws.amazon.com/lambda/)
- [Amazon DynamoDB Docs](https://docs.aws.amazon.com/dynamodb/)

---

## ⚖️ Legal Notice

This project and its techniques are the intellectual property of KFUPM/Course Instructors — Semester 252 and are intended solely for educational purposes within ICS-344: Information Security. Any unauthorized use outside this course context is strictly prohibited.

> DVSA is intentionally vulnerable. Do not deploy on production accounts. Do not use maliciously.
