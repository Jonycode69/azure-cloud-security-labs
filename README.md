# Azure Cloud Security Lab Assessment (Labs 1–9)

## Project Overview

This project documents my hands-on learning and practical implementation of cloud security controls using Microsoft Azure. Across nine security labs, I explored identity and access management, network security, container security, storage protection, security monitoring, cloud posture management, just-in-time access, and security incident detection and response.

The assessment focused on understanding how Azure security services work individually and how they can be combined to strengthen an organisation's cloud security posture.

**Project type:** Cloud Security / Cybersecurity Hands-on Labs  
**Platform:** Microsoft Azure  
**Primary tools:** Azure Portal, Azure CLI, Azure PowerShell, Docker, Azure Kubernetes Service (AKS), Azure Container Registry (ACR), Azure Monitor, Log Analytics, Microsoft Defender for Cloud, and Microsoft Sentinel.

## Objectives

- Implement role-based access control and the principle of least privilege.
- Configure network security controls to restrict unauthorised traffic.
- Explore Azure Firewall and network traffic filtering.
- Build and deploy containerised applications using Azure services.
- Secure access to Azure Storage using network restrictions and service endpoints.
- Collect and monitor virtual machine performance data.
- Evaluate cloud security posture and server protection capabilities.
- Restrict administrative access through Just-In-Time (JIT) VM access.
- Configure security analytics and automated incident response using Microsoft Sentinel.

## Lab Implementations

### Lab 1 — Identity and Access Management (RBAC)

**Objective:** Control access to Azure resources through roles, users, and groups.

**Activities:**
- Created and managed user and group assignments.
- Used the Azure Portal, Azure PowerShell, and Azure CLI to explore identity administration.
- Assigned the Virtual Machine Contributor role at resource group scope.

**Security outcome:** Practised granting permissions according to job responsibilities rather than giving every user unrestricted access.

**Key concepts:** Microsoft Entra ID, Role-Based Access Control (RBAC), security groups, role assignments, scope, authentication, authorization, and least privilege.

### Lab 2 — Network Security Groups and Application Security Groups

**Objective:** Control network traffic to web and management resources.

**Activities:**
- Configured Network Security Groups (NSGs) and Application Security Groups (ASGs).
- Applied rules for HTTP traffic on TCP port 80 and Remote Desktop Protocol (RDP) on TCP port 3389.
- Tested web access and administrative connectivity.
- Verified that management access was restricted according to the configured rules.

**Security outcome:** Demonstrated network segmentation and the importance of allowing only required traffic.

**Key concepts:** Virtual networks, subnets, NSGs, ASGs, inbound rules, rule priorities, network interfaces, HTTP, RDP, and IIS.

### Lab 3 — Azure Firewall and Traffic Filtering

**Objective:** Explore centralised network traffic filtering and firewall-based protection.

**Activities:**
- Worked with Azure Firewall deployment concepts and supporting network resources.
- Explored firewall rules, routing, public and private IP addressing, and traffic-filtering requirements.
- Investigated deployment problems related to virtual machine size availability, subscription restrictions, and regional capacity.

**Security outcome:** Developed an understanding of how firewall policies and routing help control network communication, alongside practical troubleshooting experience.

**Key concepts:** Azure Firewall, ARM templates, route tables, user-defined routes, application rules, network rules, DNS, and fully qualified domain names (FQDNs).

### Lab 4 — Azure Container Registry and Azure Kubernetes Service

**Objective:** Build, store, and deploy a containerised web application.

**Activities:**
- Built a container image locally using Docker.
- Pushed the image to Azure Container Registry (ACR).
- Deployed an application to Azure Kubernetes Service (AKS).
- Tested application access using Kubernetes service configurations, including external and internal service exposure.

**Security outcome:** Gained practical experience with container image management and Kubernetes deployment, while exploring how application exposure is controlled.

**Key concepts:** Docker, Dockerfile, container image, image repository, image tags, ACR, AKS, Kubernetes pods, deployments, services, LoadBalancer, ClusterIP, and `kubectl`.

### Lab 5 — Azure Storage Security and Service Endpoints

**Objective:** Restrict access to Azure Storage using network security controls.

**Activities:**
- Configured private and public subnet environments.
- Created an Azure Storage resource and file share.
- Explored storage firewall rules and the Microsoft.Storage service endpoint.
- Tested connectivity from different virtual machine network contexts.

**Security outcome:** Verified that storage access could be restricted by network configuration and that connectivity should be tested from both permitted and denied environments.

**Key concepts:** Azure Storage, Azure Files, service endpoints, storage firewalls, network access rules, public network access, NSGs, and connectivity testing.

### Lab 6 — Azure Monitor, Log Analytics, and Data Collection Rules

**Objective:** Configure monitoring resources and collect virtual machine performance data.

**Activities:**
- Created an Azure Monitor Log Analytics workspace.
- Created an Azure Storage account.
- Created a Data Collection Rule (DCR).
- Configured performance counters for CPU, memory, disk, and network.
- Associated the collection configuration with a virtual machine and selected the Log Analytics workspace as a destination.

**Security outcome:** Learned how monitoring configurations support resource visibility and how collected telemetry can support operational monitoring and security investigations.

**Key resources used:** `lgawIgnite` (Log Analytics workspace), `strgactignite` (Storage account), and `DCR1` (Data Collection Rule).

**My contribution:** I completed the practical lab activities and contributed the Lab 6 steps, configuration details, and documentation to the team assessment report.

**Key concepts:** Azure Monitor, Log Analytics, DCR, performance counters, telemetry, data sources, destinations, and log analysis.

### Lab 7 — Microsoft Defender for Cloud

**Objective:** Explore cloud security posture management and server protection.

**Activities:**
- Enabled and explored Defender for Servers Plan 2.
- Reviewed available security recommendations and vulnerability assessment capabilities.
- Examined how Defender for Cloud supports security visibility and protection.

**Security outcome:** Learned how cloud security posture management can identify weaknesses and help organisations prioritise security improvements.

**Key concepts:** Microsoft Defender for Cloud, cloud security posture management (CSPM), workload protection, vulnerability assessment, security recommendations, and security alerts.

### Lab 8 — Just-In-Time Virtual Machine Access

**Objective:** Reduce unnecessary exposure of administrative access to virtual machines.

**Activities:**
- Enabled Just-In-Time (JIT) access for a virtual machine.
- Configured and reviewed access requirements for RDP on TCP port 3389.
- Requested temporary access from the source IP address and verified that access was granted.

**Security outcome:** Demonstrated how time-limited, controlled administrative access can reduce the period during which management ports are exposed.

**Key concepts:** JIT VM access, Defender for Cloud, RDP, source IP restrictions, temporary access requests, and attack surface reduction.

### Lab 9 — Microsoft Sentinel SIEM and SOAR

**Objective:** Explore security event monitoring, detection rules, incidents, and automated response.

**Activities:**
- Enabled Microsoft Sentinel on a Log Analytics workspace.
- Connected Azure Activity data and explored security event queries using Kusto Query Language (KQL).
- Created a scheduled analytics rule to identify activity associated with JIT network access policy deletion.
- Created a Logic App playbook named `Change-Incident-Severity`.
- Configured automation to invoke the playbook and change incident severity to High.
- Reviewed the automation and playbook execution results.

**Security outcome:** Demonstrated the core stages of a security monitoring workflow: collecting activity data, detecting suspicious events, creating incidents, and automating a response action.

**Key concepts:** Microsoft Sentinel, SIEM, SOAR, Azure Activity Log, KQL, analytics rules, incidents, Logic Apps, playbooks, automation rules, and incident severity.

Example query used during the exercise:

```kusto
AzureActivity
| where OperationNameValue contains "jitNetworkAccessPolicies"
| where OperationNameValue contains "delete"
```

The query filters Azure Activity records for operations associated with deleting JIT network access policies. The actual results depend on the activity data available in the workspace.

## Key Skills Developed

- Azure identity and access management
- RBAC and least-privilege access control
- Network segmentation and traffic filtering
- Azure Storage network protection
- Docker and Kubernetes fundamentals
- Cloud monitoring and telemetry configuration
- Cloud security posture assessment
- Just-In-Time administrative access
- KQL-based security investigation
- SIEM/SOAR concepts and automated response
- Azure Portal, CLI, and PowerShell troubleshooting
- Technical documentation and evidence collection

## Major Challenge

The main challenge was troubleshooting Azure deployment and configuration issues, including virtual machine size and regional availability constraints, subscription restrictions, and permissions or connector configuration in Microsoft Sentinel.

I approached these challenges by reviewing deployment settings, checking configuration requirements, testing connectivity, exploring alternative approaches where appropriate, and verifying results in the Azure environment.

This experience reinforced the importance of systematic troubleshooting and validating security configurations rather than assuming that a successful deployment automatically means a control is working as intended.

## Key Takeaways

1. **Identity is a security boundary:** Users should receive only the permissions required for their responsibilities.
2. **Network access must be intentional:** NSGs, ASGs, firewall rules, and storage network controls help reduce unnecessary exposure.
3. **Visibility supports security:** Monitoring and log collection provide evidence needed to investigate activity.
4. **Detection and response work together:** Microsoft Sentinel can use activity data and analytics rules to identify events and trigger automated response workflows.
5. **Validation matters:** Security controls should be tested to confirm that permitted activity succeeds and prohibited activity is blocked.
6. **Cost awareness is part of cloud security practice:** Resource usage and paid security plans should be reviewed and cleaned up when no longer required.

## Relevance to CYV Telecomms

The skills explored in this assessment are relevant to a telecommunications organisation such as CYV Telecomms, where protecting customer information, infrastructure, administrative access, and service availability is essential.

- **Identity and access management** can help prevent unauthorised access to cloud resources.
- **Network segmentation and firewall controls** can restrict unnecessary communication between workloads.
- **Storage protection** can reduce exposure of sensitive information.
- **Monitoring and security posture assessment** can improve visibility into resource health and security weaknesses.
- **Sentinel SIEM/SOAR workflows** can support the detection, investigation, and handling of suspicious activity.

These are potential applications of the skills developed in the labs, rather than a claim that the lab environment was deployed in CYV Telecomms' production infrastructure.

## Repository Structure

```text
azure-cloud-security-labs/
├── README.md
├── lab-01-rbac/
│   └── README.md
├── lab-02-nsg-asg/
│   └── README.md
├── lab-03-azure-firewall/
│   └── README.md
├── lab-04-acr-aks/
│   └── README.md
├── lab-05-storage-security/
│   └── README.md
├── lab-06-azure-monitor-dcr/
│   └── README.md
├── lab-07-defender-for-cloud/
│   └── README.md
├── lab-08-jit-access/
│   └── README.md
├── lab-09-sentinel-siem-soar/
│   └── README.md
└── screenshots/
    ├── lab-01/
    ├── lab-02/
    ├── lab-04/
    ├── lab-05/
    ├── lab-06/
    ├── lab-07/
    ├── lab-08/
    └── lab-09/
```

Each lab folder can contain its own objective, implementation steps, evidence screenshots, verification results, and lessons learned. Add screenshots only when they are available and ensure they do not reveal credentials, subscription identifiers, personal information, or sensitive network details.

## Conclusion

This assessment strengthened my understanding of practical Azure security and the relationship between preventive controls, monitoring, detection, and response. It also improved my confidence in using cloud security tools and troubleshooting configuration issues.

The most important lesson was that effective cloud security depends not on a single product, but on combining appropriate access controls, network restrictions, monitoring, security assessment, and incident response into a coherent security approach.

**Disclaimer:** This repository documents educational lab work conducted in a learning environment. It does not represent a production deployment or an independent security audit of CYV Telecomms or any other organisation.
