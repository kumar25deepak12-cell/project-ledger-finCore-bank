# Project LEDGER — FinCore Bank Enterprise Cloud Architecture

> **Enterprise Cloud Architecture | GCP | Security | Reliability | Observability | FinOps**

Project LEDGER is a self-directed enterprise cloud architecture portfolio project designed around a fictional **FinCore Bank** scenario.

The project demonstrates how an enterprise workload can be designed, implemented, secured, operated, validated, optimized, and finally decommissioned using Google Cloud capabilities.

## 🏦 Business Scenario

FinCore Bank is a fictional financial-services organization requiring a secure, resilient, scalable and operationally governed cloud platform for a modern enterprise web workload.

The architecture was developed to demonstrate an end-to-end enterprise architecture lifecycle rather than isolated cloud-service exercises.

### Business Drivers

- Enterprise-grade availability and resilience
- Secure internet-facing application access
- Scalable workload infrastructure
- Centralized security controls
- Operational visibility and monitoring
- Cost governance and FinOps
- End-to-end validation
- Controlled cloud-resource lifecycle management

> **Note:** FinCore Bank is a fictional/self-directed scenario created for architecture demonstration and portfolio purposes.

# 🎯 Architecture Objectives

Project LEDGER was designed around the following objectives:

1. Establish a secure enterprise network foundation
2. Deploy a standardized workload using a regional Managed Instance Group
3. Provide resilient and scalable application delivery
4. Implement secure HTTPS/TLS ingress
5. Protect the application using Cloud Armor/WAF
6. Apply IAM least-privilege principles
7. Establish monitoring and operational logging
8. Implement FinOps controls
9. Validate the complete application path
10. Demonstrate controlled cloud-resource decommissioning

# 🏗️ Architecture Story

FinCore Bank
     ↓
Enterprise Requirements
     ↓
Architecture Design
     ↓
GCP Implementation
     ↓
Security
     ↓
Reliability
     ↓
Observability
     ↓
FinOps
     ↓
End-to-End Validation
     ↓
Controlled Decommissioning

☁️ **GCP Architecture**

The Project LEDGER implementation uses the following major Google Cloud capabilities:

Virtual Private Cloud (VPC)
Custom VPC subnets
VPC firewall rules
Compute Engine
Instance Templates
Regional Managed Instance Groups
Health Checks
Auto-Healing
Global External Application Load Balancer
HTTPS/TLS
Cloud Armor
IAM
Cloud Monitoring
Cloud Logging
Cloud Billing
Budgets and Alerts

🌐 **Network Architecture**

The enterprise VPC foundation was designed using a custom VPC:

**ledger-vpc**
│
├── ledger-web-subnet
│   └── 10.10.1.0/24
│
├── ledger-app-subnet
│   └── 10.10.2.0/24
│
├── ledger-db-subnet
│   └── 10.10.3.0/24
│
└── ledger-mgmt-subnet
    └── 10.10.4.0/24
    The workload web tier uses the dedicated ledger-web-subnet
    
🔐 **Security Architecture**
Security was implemented as multiple layers rather than relying on a single control.

Network Security
Dedicated enterprise VPC
Segmented subnets
Explicit firewall rules
Health-check traffic allowance
IAP SSH access
Workload-specific network tags

**Application Security**
HTTPS/TLS frontend
Cloud Armor backend security policy
Preconfigured SQL-injection WAF protection
Least-privilege IAM hardening

**Identity**
The Compute Engine default service account was removed from the project-level Editor role because the workload did not require broad project permissions.

**🛡️ Cloud Armor / WAF**
Cloud Armor was attached to the application backend to provide application-layer protection.

The Project LEDGER policy includes a preconfigured SQL-injection WAF rule
Internet
   ↓
HTTPS
   ↓
Cloud Armor / WAF
   ↓
Global Load Balancer
   ↓
Backend Service
   ↓
Regional MIG
Normal application traffic was validated successfully after the security policy was attached.

🔄 **Reliability & Scalability**

The web tier was implemented using a Regional Managed Instance Group.
Regional MIG
│
├── asia-south1-a
├── asia-south1-b
└── asia-south1-c

**The workload was designed to provide:**

Multi-zone distribution
Health checking
Auto-healing
Horizontal scaling
Standardized VM deployment through an Instance Template
Load-balanced traffic distribution

❤️ **Health Checks & Auto-Healing**

A dedicated HTTP health check was configured for the workload.
Health Check
     ↓
Regional MIG
     ↓
Unhealthy VM
     ↓
Repair / Auto-Healing
This provides automated workload recovery based on application health.

🌍 **Global Application Delivery**

The application was exposed through a Global External Application Load Balancer.

Internet
   ↓
HTTPS :443
   ↓
Cloud Armor
   ↓
Global External Application Load Balancer
   ↓
Backend Service
   ↓
Regional MIG
   ↓
Healthy Web VM
The application was successfully validated through the external HTTPS endpoint.

📊 **Observability**

Project LEDGER includes both monitoring and logging capabilities.

**Cloud Monitoring**

A custom operations dashboard was created to observe:

Web-tier CPU utilization
HTTPS request activity
Regional workload behavior

**Cloud Logging**
Load-balancer traffic was validated through Cloud Logging using successful HTTP/HTTPS requests.

**Operational visibility includes:**
Request status
Request information
Latency
Backend service association
Timestamped traffic records

💰 **FinOps & Cost Governance**
FinOps was treated as an architectural responsibility rather than an afterthought.

**A dedicated Project LEDGER budget was configured:**

**Budget:**
₹500 / month

**Alert thresholds:**
50%
90%
100%

**Billing analysis was also performed to identify the major infrastructure cost drivers.**

This provided visibility into:

Compute costs
Networking costs
Load-balancing costs
Resource-level cost drivers
Historical usage
Cost optimization opportunities

🔎 **End-to-End Validation**

The architecture was validated through the complete application path:

User / Internet
      ↓
HTTPS / TLS
      ↓
Cloud Armor
      ↓
Global Load Balancer
      ↓
Backend Service
      ↓
Regional MIG
      ↓
Health Check
      ↓
Healthy Web VM
      ↓
Application Response

The Project LEDGER application returned a healthy response from the deployed workload.

**Controlled Cloud-Resource Cleanup**

After validation, the environment was intentionally decommissioned using a controlled cleanup procedure aligned with Google Cloud operational and cost-management guidance.

**Cleanup sequence**
Preserve Evidence
      ↓
Disable Autoscaling
      ↓
Reduce MIG Capacity
      ↓
Verify Zero Running Instances
      ↓
Remove Load Balancer
      ↓
Release Unused Reserved IP
      ↓
Review Billing
      ↓
Retain Reusable Architecture Evidence

The objective was not simply to delete resources.
The objective was to demonstrate the complete cloud lifecycle:

**Build → Secure → Operate → Validate → Optimize → Controlled Decommissioning**

# 📚 Evidence Index

The following evidence pack is the master evidence map for **Project LEDGER.**

## EP-08 — Enterprise Infrastructure Foundation

| ID | Capability | Evidence | Portfolio Purpose |
|---|---|---|---|
| E01 | VPC + Subnets | Screenshot | Network architecture |
| E02 | Firewall | Screenshot | Network security |
| E03 | Instance Template | Screenshot | Standardized workload |
| E04 | Regional MIG | Screenshot | HA + scalability |
| E05 | Health Check / Auto-healing | Screenshot | Reliability |
| E06 | Global Load Balancer | Screenshot | Global traffic management |
| E07 | Application Validation | Screenshot | E2E validation |

## EP-09 — Security & Platform

| ID | Capability | Evidence | Portfolio Purpose |
|---|---|---|---|
| E08 | HTTPS / TLS | Screenshot | Secure ingress |
| E09 | Cloud Armor / WAF | Screenshot | Application security |
| E10 | HTTPS Application Validation | Screenshot | Secure application validation |
| E11 | IAM Hardening | Screenshot | Least privilege |
| E12 | Monitoring | Screenshot | Observability |
| E13 | Cloud Logging | Screenshot | Operations |

## EP-10 — Operations, Governance & FinOps

| ID | Capability | Evidence | Portfolio Purpose |
|---|---|---|---|
| E14 | Operational Readiness | Screenshot | Production readiness |
| E15 | End-to-End Validation | Screenshot | Complete architecture validation |
| E16 | Billing / Cost Analysis | Screenshot | Cost optimization |
| E17 | FinOps Budget / Alerts | Screenshot | Cost governance |

### Supporting Lifecycle Artifact

**Controlled Cloud-Resource Cleanup**
The controlled cleanup journey is retained as a supporting lifecycle artifact rather than receiving a new Master Evidence ID.
It demonstrates:
**Preserve Evidence → Disable Autoscaling → Reduce MIG Capacity → Verify → Remove Load Balancer → Release Static IP → Review Billing → Retain Architecture Evidence**
This completes the Project LEDGER lifecycle:
**Build → Secure → Operate → Validate → Optimize → Controlled Decommissioning**

🧠 **Architecture Principles Demonstrated**
Project LEDGER demonstrates the following architecture principles:

Business requirements before technology selection
Security by design
Least privilege
Defense in depth
High availability through multi-zone deployment
Standardized infrastructure
Health-driven recovery
Observable systems
Cost-aware architecture
Controlled resource lifecycle
Evidence-based architecture validation

⚖️ **Architecture Trade-offs**

Several practical trade-offs were considered during implementation.

**Regional MIG vs single VM**
A Regional MIG provides better resilience and scalability but introduces additional infrastructure and operational complexity.

**Global Load Balancer vs direct VM access**
The Load Balancer provides centralized traffic management and enterprise ingress capabilities but introduces additional cost and configuration complexity.

**Self-managed lab certificate**
A self-managed certificate was used for portfolio validation. This demonstrates the TLS path but is not intended as a production certificate-management model.

**Cost vs continuous availability**
The validated infrastructure was intentionally decommissioned after testing to avoid unnecessary ongoing infrastructure charges.

🎓 **Architect Learning Outcomes**

Project LEDGER strengthened practical capability across:

Enterprise cloud architecture
GCP networking
Compute architecture
High availability
Load balancing
Security architecture
IAM
WAF
Observability
FinOps
Operational readiness
Cloud lifecycle management
Architecture evidence and documentation

🗣️ **Architecture Defense**

The project can be defended through questions such as:

Why use a Regional MIG?
Why use a Global Load Balancer?
How does health checking differ from auto-healing?
How does Cloud Armor protect the application?
Why was the Compute Engine service account hardened?
How would you replace the self-managed certificate in production?
How would you design this for multi-region disaster recovery?
How would you reduce the networking cost?
How would you monitor application-level SLOs?
How would you extend this architecture for a production banking platform?
What would change for hybrid or multi-cloud requirements?
How would you implement centralized governance at enterprise scale?

🚀 **Project Lifecycle**

PLAN
 ↓
DESIGN
 ↓
BUILD
 ↓
SECURE
 ↓
VALIDATE
 ↓
OBSERVE
 ↓
OPTIMIZE
 ↓
DECOMMISSION
 ↓
DOCUMENT

📌 **Portfolio Positioning**

Project LEDGER is part of the broader **GLSP — Grow, Learn, Solve, Perform career and architecture-development framework.**

The project demonstrates the transition from cloud knowledge to practical architecture capability through:

**Learn → Build → Validate → Explain → Defend**

👤 **Portfolio Disclaimer**

Project LEDGER is a self-directed architecture portfolio project.

FinCore Bank is a fictional enterprise scenario created specifically for demonstrating **architecture design, cloud implementation, security, reliability, operations and FinOps capabilities**.

The project does not represent a production deployment for an actual bank or customer.

**Project Status**

**Architecture: ✅ Complete
Implementation: ✅ Completed and validated
Security: ✅ Implemented
Observability: ✅ Implemented
FinOps: ✅ Implemented
Evidence Pack: 🔒 Frozen
Controlled Cleanup: ✅ Completed**




    
