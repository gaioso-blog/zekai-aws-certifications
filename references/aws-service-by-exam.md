# AWS Services by Exam

## Purpose

This file maps AWS certification exams to the main AWS service families, concepts, and exam-focus areas.

This file is a helper reference only.

The official AWS Exam Guide is always the primary source of truth.

Before generating final exam-specific questions, explanations, summaries, or study plans, validate the requested exam against the official AWS Certification Exam Guide.

Official exam guides:
https://docs.aws.amazon.com/aws-certification/latest/examguides/aws-certification-exam-guides.html

## Global rules

1. Do not claim that a service is in scope unless the official exam guide supports it.
2. Do not invent domains, task statements, or percentages.
3. If this file conflicts with the official exam guide, follow the official exam guide.
4. If the user provides a specific guide URL, use that guide over this reference.
5. Treat this file as a study map, not as an authoritative blueprint.
6. For each generated question, map the question to:
   - exam code
   - exam domain
   - task statement or objective when available
   - service or concept
   - difficulty level

---

# Foundational

## CLF-C02 — AWS Certified Cloud Practitioner

### Main focus

Foundational understanding of AWS Cloud, billing, security, support, shared responsibility, and core services.

### Common service families

- Compute:
  - Amazon EC2
  - AWS Lambda
  - AWS Elastic Beanstalk
  - Amazon ECS
  - Amazon EKS

- Storage:
  - Amazon S3
  - Amazon EBS
  - Amazon EFS
  - Amazon Glacier / S3 Glacier storage classes

- Databases:
  - Amazon RDS
  - Amazon DynamoDB
  - Amazon Aurora
  - Amazon Redshift

- Networking:
  - Amazon VPC
  - Security groups
  - Network ACLs
  - Amazon Route 53
  - Elastic Load Balancing
  - AWS Direct Connect
  - AWS VPN

- Security:
  - AWS IAM
  - AWS Organizations
  - AWS Control Tower
  - AWS CloudTrail
  - Amazon GuardDuty
  - AWS Shield
  - AWS WAF
  - AWS KMS
  - AWS Secrets Manager

- Monitoring and management:
  - Amazon CloudWatch
  - AWS Config
  - AWS Systems Manager
  - AWS Trusted Advisor
  - AWS Health Dashboard

- Billing and cost:
  - AWS Budgets
  - AWS Cost Explorer
  - AWS Pricing Calculator
  - Savings Plans
  - Reserved Instances

### Question style

Prefer conceptual questions about:
- shared responsibility model
- cloud value proposition
- pricing models
- support plans
- basic service selection
- high-level security and compliance

Avoid deep implementation details.

---

# Associate

## SAA-C03 — AWS Certified Solutions Architect - Associate

### Main focus

Designing secure, resilient, high-performing, and cost-optimized architectures on AWS.

### Common service families

- Compute:
  - Amazon EC2
  - Auto Scaling
  - AWS Lambda
  - Amazon ECS
  - Amazon EKS
  - AWS Batch

- Storage:
  - Amazon S3
  - S3 lifecycle policies
  - S3 storage classes
  - Amazon EBS
  - Amazon EFS
  - AWS Backup
  - AWS Storage Gateway

- Databases:
  - Amazon RDS
  - Amazon Aurora
  - Amazon DynamoDB
  - Amazon ElastiCache
  - Amazon Redshift

- Networking:
  - Amazon VPC
  - Public and private subnets
  - Route tables
  - NAT Gateway
  - Internet Gateway
  - VPC endpoints
  - VPC peering
  - Transit Gateway
  - Elastic Load Balancing
  - Amazon Route 53
  - AWS Direct Connect
  - Site-to-Site VPN
  - AWS Global Accelerator
  - Amazon CloudFront

- Security:
  - IAM
  - Resource policies
  - Security groups
  - Network ACLs
  - AWS KMS
  - AWS WAF
  - AWS Shield
  - Secrets Manager
  - ACM

- Messaging and integration:
  - Amazon SQS
  - Amazon SNS
  - Amazon EventBridge
  - AWS Step Functions

- Monitoring:
  - Amazon CloudWatch
  - AWS CloudTrail
  - AWS Config

### Question style

Prefer scenario questions involving:
- high availability
- disaster recovery
- multi-AZ vs multi-region
- decoupling
- caching
- cost optimization
- migration patterns
- least operational overhead
- secure private connectivity

### Common traps

- Choosing Multi-Region when Multi-AZ is enough
- Choosing EC2 when managed/serverless is more appropriate
- Ignoring operational overhead
- Confusing Security Groups and NACLs
- Confusing Gateway Endpoint and Interface Endpoint
- Choosing NAT Gateway for private access to S3 when Gateway Endpoint is better
- Choosing EBS for shared file storage instead of EFS
- Choosing RDS read replicas for HA instead of Multi-AZ

---

## DVA-C02 — AWS Certified Developer - Associate

### Main focus

Developing, deploying, securing, and troubleshooting applications on AWS.

### Common service families

- Compute:
  - AWS Lambda
  - Amazon EC2
  - Elastic Beanstalk
  - Amazon ECS

- Serverless and integration:
  - API Gateway
  - AWS Step Functions
  - Amazon EventBridge
  - Amazon SQS
  - Amazon SNS

- Databases:
  - Amazon DynamoDB
  - Amazon RDS
  - ElastiCache

- Storage:
  - Amazon S3
  - Presigned URLs
  - S3 event notifications

- Security:
  - IAM roles and policies
  - Cognito
  - KMS
  - Secrets Manager
  - Systems Manager Parameter Store

- CI/CD:
  - CodeCommit
  - CodeBuild
  - CodeDeploy
  - CodePipeline
  - SAM
  - CloudFormation
  - CDK

- Observability:
  - CloudWatch Logs
  - CloudWatch Metrics
  - X-Ray
  - Lambda Powertools

### Question style

Prefer questions involving:
- SDK usage
- Lambda configuration
- API Gateway integrations
- DynamoDB access patterns
- error handling
- retries and DLQs
- deployment strategies
- IAM permissions for applications
- observability and tracing

### Common traps

- Putting credentials in code instead of using IAM roles
- Using synchronous invocation when async/event-driven is better
- Missing idempotency
- Ignoring Lambda timeout, memory, and concurrency
- Confusing Parameter Store and Secrets Manager
- Confusing SQS visibility timeout with message retention
- Using scans in DynamoDB when query/index design is needed

---

## SOA-C02 — AWS Certified SysOps Administrator - Associate

### Main focus

Operations, monitoring, automation, deployment, networking, security, and cost control.

### Common service families

- Monitoring and operations:
  - CloudWatch
  - CloudWatch Alarms
  - CloudWatch Logs
  - EventBridge
  - CloudTrail
  - AWS Config
  - Systems Manager
  - Trusted Advisor
  - AWS Health

- Compute:
  - EC2
  - Auto Scaling
  - Elastic Load Balancing
  - AMIs
  - EBS

- Networking:
  - VPC
  - Route tables
  - NAT Gateway
  - Internet Gateway
  - Security Groups
  - NACLs
  - VPC Flow Logs
  - Route 53

- Security:
  - IAM
  - KMS
  - Secrets Manager
  - AWS Organizations
  - SCPs

- Backup and resilience:
  - AWS Backup
  - EBS snapshots
  - RDS snapshots
  - Multi-AZ

### Question style

Prefer operational troubleshooting:
- alarms
- metric interpretation
- failed deployments
- permissions
- networking reachability
- backup/restore
- patching
- automation with Systems Manager

---

# Professional

## SAP-C02 — AWS Certified Solutions Architect - Professional

### Main focus

Complex architecture design, multi-account, hybrid networking, migration, cost optimization, governance, and advanced resilience.

### Common service families

- Organizations and governance:
  - AWS Organizations
  - SCPs
  - Control Tower
  - IAM Identity Center
  - AWS Config
  - CloudTrail
  - Security Hub

- Networking:
  - Transit Gateway
  - Direct Connect
  - Site-to-Site VPN
  - Route 53
  - CloudFront
  - Global Accelerator
  - VPC endpoints
  - PrivateLink

- Migration:
  - Application Migration Service
  - Database Migration Service
  - DataSync
  - Storage Gateway
  - Migration Hub

- Compute and containers:
  - EC2
  - Auto Scaling
  - ECS
  - EKS
  - Lambda

- Data:
  - RDS
  - Aurora
  - DynamoDB
  - Redshift
  - ElastiCache
  - S3

- Integration:
  - SQS
  - SNS
  - EventBridge
  - Step Functions
  - API Gateway

### Question style

Prefer long scenario questions involving:
- multiple accounts
- multiple regions
- enterprise governance
- hybrid connectivity
- migration constraints
- disaster recovery strategies
- cost/performance trade-offs
- least operational overhead at scale

### Common traps

- Overengineering vs meeting stated requirements
- Ignoring governance requirements
- Choosing service-level solution when org-level control is required
- Misreading RTO/RPO
- Confusing backup, pilot light, warm standby, and active-active
- Choosing VPN when Direct Connect is required by bandwidth/consistency

---

## DOP-C02 — AWS Certified DevOps Engineer - Professional

### Main focus

CI/CD, automation, observability, incident response, configuration management, resilience, and governance.

### Common service families

- CI/CD:
  - CodePipeline
  - CodeBuild
  - CodeDeploy
  - CodeArtifact
  - CodeDeploy deployment strategies
  - CloudFormation
  - CDK
  - SAM

- Operations:
  - CloudWatch
  - X-Ray
  - EventBridge
  - CloudTrail
  - AWS Config
  - Systems Manager
  - OpsCenter
  - Incident Manager

- Compute:
  - EC2
  - Auto Scaling
  - ECS
  - EKS
  - Lambda

- Security and governance:
  - IAM
  - KMS
  - Organizations
  - SCPs
  - Secrets Manager
  - Parameter Store

- Resilience:
  - Route 53
  - ELB
  - Auto Scaling
  - Backup
  - Multi-region patterns

### Question style

Prefer scenarios involving:
- deployment automation
- blue/green and canary
- rollback
- monitoring and alerting
- compliance automation
- IaC drift detection
- multi-account pipelines
- incident response

---

# Specialty

## ANS-C01 — AWS Certified Advanced Networking - Specialty

### Main focus

Advanced AWS networking, hybrid connectivity, routing, DNS, network security, and troubleshooting.

### Common service families

- Core networking:
  - VPC
  - Subnets
  - Route tables
  - Security Groups
  - NACLs
  - VPC Flow Logs
  - Traffic Mirroring

- Hybrid:
  - Direct Connect
  - Direct Connect Gateway
  - Site-to-Site VPN
  - Transit Gateway
  - Customer Gateway
  - Virtual Private Gateway

- DNS:
  - Route 53
  - Resolver inbound endpoints
  - Resolver outbound endpoints
  - Private hosted zones
  - DNSSEC

- Edge:
  - CloudFront
  - Global Accelerator
  - AWS WAF
  - Shield

- Private access:
  - VPC endpoints
  - Gateway endpoints
  - Interface endpoints
  - PrivateLink

- Network security:
  - Network Firewall
  - AWS Firewall Manager
  - Security Groups
  - NACLs

### Question style

Prefer troubleshooting and design scenarios involving:
- BGP
- route propagation
- asymmetric routing
- overlapping CIDRs
- high availability Direct Connect
- hybrid DNS
- centralized inspection
- multi-account VPC architecture

### Common traps

- Confusing Direct Connect Gateway and Transit Gateway
- Misunderstanding BGP attributes
- Choosing VPN when bandwidth and consistency require Direct Connect
- Forgetting route propagation
- Forgetting security group/NACL/statefulness behavior
- Confusing Route 53 Resolver inbound vs outbound endpoints

---

## SCS-C02 — AWS Certified Security - Specialty

### Main focus

AWS security architecture, identity, detection, infrastructure protection, data protection, and incident response.

### Common service families

- Identity:
  - IAM
  - IAM Identity Center
  - Organizations
  - SCPs
  - Resource-based policies
  - Permission boundaries
  - STS

- Detection and response:
  - GuardDuty
  - Security Hub
  - Detective
  - CloudTrail
  - CloudWatch
  - Config
  - EventBridge

- Infrastructure protection:
  - WAF
  - Shield
  - Network Firewall
  - Security Groups
  - NACLs
  - VPC endpoints

- Data protection:
  - KMS
  - CloudHSM
  - Secrets Manager
  - ACM
  - S3 encryption
  - EBS encryption
  - RDS encryption

### Question style

Prefer scenarios involving:
- least privilege
- cross-account access
- key policies
- incident investigation
- threat detection
- logging and auditability
- encryption requirements
- data exfiltration prevention

### Common traps

- Confusing IAM policy and KMS key policy
- Forgetting CloudTrail data events for S3 object-level activity
- Choosing access keys instead of roles
- Ignoring organization-level guardrails
- Confusing GuardDuty, Detective, Security Hub, and Config

---

# Data and AI

## DEA-C01 — AWS Certified Data Engineer - Associate

### Main focus

Data ingestion, transformation, orchestration, storage, governance, monitoring, and data pipeline operations.

### Common service families

- Data ingestion:
  - Kinesis Data Streams
  - Kinesis Data Firehose
  - Amazon MSK
  - AWS DMS
  - AWS DataSync

- Storage:
  - S3
  - Lake Formation
  - Glue Data Catalog

- Processing:
  - AWS Glue
  - Glue Studio
  - Glue Crawlers
  - EMR
  - Lambda
  - Step Functions

- Analytics:
  - Athena
  - Redshift
  - OpenSearch
  - QuickSight

- Governance and security:
  - Lake Formation
  - IAM
  - KMS
  - Macie
  - CloudTrail

### Question style

Prefer scenarios involving:
- batch vs streaming
- schema evolution
- data cataloging
- partitioning
- compression
- ETL job design
- monitoring pipelines
- data quality
- least privilege for data lakes

---

## MLA-C01 — AWS Certified Machine Learning Engineer - Associate

### Main focus

ML workloads, data preparation, model development, deployment, monitoring, and operationalization.

### Common service families

- ML platform:
  - Amazon SageMaker
  - SageMaker Studio
  - SageMaker Pipelines
  - SageMaker Feature Store
  - SageMaker Model Registry
  - SageMaker Clarify
  - SageMaker Model Monitor
  - SageMaker Canvas

- Data:
  - S3
  - Glue
  - Athena
  - Redshift
  - Kinesis

- Compute:
  - EC2
  - Lambda
  - ECS
  - EKS

- Security and monitoring:
  - IAM
  - KMS
  - CloudWatch
  - CloudTrail

### Question style

Prefer scenarios involving:
- feature engineering
- model training
- model deployment
- endpoint scaling
- model monitoring
- bias/explainability
- data drift
- pipeline automation
- cost/performance trade-offs

---

## AIF-C01 — AWS Certified AI Practitioner

### Main focus

Foundational AI, ML, generative AI, responsible AI, and AWS AI services.

### Common service families

- AI services:
  - Amazon Bedrock
  - Amazon Q
  - Amazon Comprehend
  - Amazon Transcribe
  - Amazon Translate
  - Amazon Textract
  - Amazon Rekognition
  - Amazon Lex
  - Amazon Polly
  - Amazon Kendra

- ML services:
  - Amazon SageMaker
  - SageMaker Canvas

- Responsible AI:
  - bias
  - explainability
  - hallucination
  - toxicity
  - privacy
  - security
  - governance

### Question style

Prefer conceptual and service-selection questions involving:
- AI vs ML vs generative AI
- foundation models
- prompt engineering
- RAG
- embeddings
- vector stores
- responsible AI
- selecting managed AI services

---

## AIP-C01 — AWS Certified Generative AI Developer - Professional

### Main focus

Building, evaluating, securing, and operationalizing generative AI applications on AWS.

### Common service families

- Generative AI:
  - Amazon Bedrock
  - Bedrock Knowledge Bases
  - Bedrock Agents
  - Bedrock Guardrails
  - Bedrock Flows
  - Bedrock model evaluation

- Data and retrieval:
  - S3
  - OpenSearch Serverless
  - Aurora PostgreSQL with pgvector
  - Knowledge Bases
  - vector stores
  - embeddings
  - chunking
  - metadata filtering

- Application integration:
  - Lambda
  - API Gateway
  - Step Functions
  - EventBridge
  - SQS
  - SNS

- Security:
  - IAM
  - KMS
  - Secrets Manager
  - VPC endpoints
  - CloudTrail
  - CloudWatch

- MLOps / LLMOps:
  - evaluation
  - monitoring
  - prompt versioning
  - grounding
  - RAG quality
  - guardrail testing
  - model selection

### Question style

Prefer scenarios involving:
- RAG architecture
- prompt engineering
- grounding
- hallucination mitigation
- model evaluation
- cost/latency trade-offs
- security for generative AI apps
- orchestration with agents and tools
- responsible AI controls

---

# How to use this file

When the user asks for questions:

1. Identify the requested exam.
2. Load the official exam guide if available.
3. Use this file to select likely services and scenario patterns.
4. Validate domain/service alignment against the official guide.
5. Generate original questions.
6. Include:
   - domain
   - service/concept
   - correct answer
   - incorrect-answer explanations
   - exam trap
   - revision summary

When the user asks for summaries:

1. Identify the exam.
2. Identify the domain.
3. Use this file to list service families.
4. Explain what the exam is likely testing.
5. Add common traps and comparison points.