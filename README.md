# Enterprise Infrastructure, Identity & Security Home Lab

## Project Objective

Build and administer a hybrid enterprise infrastructure environment that combines on-premises and cloud technologies to simulate real-world IT operations. The project demonstrates hands-on experience with virtualization, Active Directory, Microsoft Entra ID, endpoint management, networking, security monitoring, and troubleshooting across interconnected systems.

## Technologies Used

### Core Infrastructure
- Proxmox VE
- Windows Server 2025
- Active Directory
- Windows 11
- pfSense

### Hybrid Identity & Endpoint Management
- Microsoft Entra ID
- Microsoft Entra Cloud Sync / Entra Connect
- Microsoft Intune
- Hybrid Azure AD Join
- dsregcmd

### Networking
- VLANs
- DNS
- DHCP
- NAT
- Firewall Rules

### Security Monitoring
- Security Onion
- Elastic Agent
- Elastic Stack
- Zeek

### Additional Operating Systems
- Ubuntu
- Arch Linux
- Kali Linux
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## Project Overview

Designed and maintained a Proxmox VE enterprise-style home lab focused on virtualization, network segmentation, security monitoring, and system administration. The environment was built to simulate real-world IT and cybersecurity infrastructure using VLANs, firewall policies, SIEM monitoring, and multi-OS virtualized systems.

<img width="1536" height="1024" alt="ChatGPT Image Jun 8, 2026 at 07_57_17 PM" src="https://github.com/user-attachments/assets/694b0ca4-593f-4eb8-aedc-b1997de73055" />


## Key Responsibilities & Configurations

* Designed and administered a multi-tier Proxmox VE home lab environment to simulate enterprise infrastructure, networking, identity management, and security operations workflows.
* Deployed and maintained Windows Server 2025, Active Directory Domain Services (AD DS), Windows 11, pfSense, Security Onion, and Linux-based systems to support infrastructure and cybersecurity testing.
* Configured Active Directory organizational units (OUs), user accounts, security groups, Group Policy Objects (GPOs), and domain-joined endpoints to simulate enterprise identity and access management practices.
* Implemented VLAN segmentation, virtual switches, network bridges, DHCP, DNS, firewall policies, and inter-VLAN routing to create isolated network zones and controlled communication paths.
* Managed pfSense firewall configurations, NAT policies, and access control rules to secure network traffic between client, server, and monitoring segments.
* Integrated Security Onion and Elastic Agents to centralize log collection, endpoint visibility, intrusion detection, and security event monitoring across the lab environment.
* Performed system administration tasks including user provisioning, password management, policy enforcement, operating system updates, troubleshooting, and system hardening.
* Diagnosed and resolved network connectivity, authentication, DNS, Group Policy, Elastic Agent, and firewall-related issues using structured troubleshooting methodologies.
* Documented infrastructure architecture, configurations, implementation procedures, and lessons learned to improve repeatability and operational efficiency.
* Configured and administered Active Directory Domain Services (AD DS), including user account management, password policy enforcement, organizational unit design, security group administration, and Group Policy deployment.



--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## Identity & Access Management

Deployed Windows Server 2025 as an Active Directory Domain Services environment to simulate enterprise user, group, and workstation administration.

- Promoted Windows Server 2025 to a domain controller and configured a lab domain for centralized identity management.
- Created organizational units, domain users, security groups, and basic role-based access structures.
- Joined a Windows 11 client VM to the domain and validated domain authentication.
- Configured Group Policy Objects for password policy, account controls, and workstation management.
- Troubleshot domain login, DNS, password reset, and Group Policy application issues using Windows administrative tools.

  Below: Configured and enforced domain-wide password policies through Group Policy Management, including password complexity requirements, 12-character minimum passwords, password history enforcement, and password expiration settings to strengthen identity security and align with enterprise security best practices.

<img width="730" height="508" alt="Screenshot 2026-06-09 at 7 11 50 PM" src="https://github.com/user-attachments/assets/09ac6ed6-f709-4e7a-9486-77e25d7bbd7a" />

## Hybrid Identity & Endpoint Management

Extended the on-premises Active Directory lab by integrating Microsoft Entra ID to simulate a hybrid enterprise identity environment. This portion of the project focused on connecting traditional Windows Server Active Directory services with cloud-based identity and endpoint management workflows.

- Configured Microsoft Entra ID tenant settings to support hybrid identity integration.
- Installed and configured Microsoft Entra Cloud Sync / Entra Connect components to synchronize on-premises Active Directory users to Microsoft Entra ID.
- Validated directory synchronization between the local `middleearth.local` domain and Microsoft Entra ID.
- Prepared domain-joined Windows client systems for Hybrid Azure AD Join testing.
- Used `dsregcmd /status` to validate device join state, domain join status, Azure AD join status, and troubleshooting results.
- Troubleshot hybrid join issues related to AD configuration, synchronization scope, device registration, and authentication.
- Explored Microsoft Intune endpoint management concepts including device enrollment, compliance visibility, ownership assignment, and BitLocker recovery workflows.

 Below: Microsoft Entra ID user synchronization showing Active Directory user accounts synchronized from the on-premises `middleearth.local` domain into Microsoft Entra ID using Microsoft Entra Cloud Sync.
<img width="1448" height="895" alt="Screenshot 2026-06-19 at 8 32 35 PM" src="https://github.com/user-attachments/assets/53f0965b-b812-4b34-bba9-920ee5ca7da6" />
Below: Microsoft Entra ID device inventory showing Windows systems successfully configured as Hybrid Microsoft Entra Joined devices, demonstrating integration between the on-premises Active Directory environment and Microsoft Entra ID.
  <img width="762" height="440" alt="Screenshot 2026-06-19 at 8 34 28 PM" src="https://github.com/user-attachments/assets/ab53f875-4340-4703-a981-38c27a968a96" />
  
  Below: Device registration validation using `dsregcmd /status`, confirming successful Hybrid Microsoft Entra Join with both Active Directory domain membership (`DomainJoined : YES`) and Microsoft Entra ID registration (`AzureAdJoined : YES`).
  <img width="754" height="194" alt="Screenshot 2026-06-19 at 8 42 37 PM" src="https://github.com/user-attachments/assets/bf4e0482-a7c2-4575-b941-21fb4b31b510" />



----

### Network Segmentation

Implemented five VLANs to separate management, client, server, monitoring, and security tool traffic.

- Configured inter-VLAN routing through pfSense.
- Implemented firewall policies to control communication between network segments.
- Restricted access to Security Onion management interfaces.
- Validated traffic flow using connectivity testing and firewall log analysis.
---

### pfSense Administration

- Configured VLAN interfaces, DHCP services, NAT policies, and inter-VLAN routing.
- Implemented firewall rules to regulate communication between management, client, and security monitoring networks.
- Troubleshot routing, DNS resolution, and connectivity issues across segmented environments.
- Validated network access controls through packet inspection and firewall log analysis.

 Below: Configured pfSense firewall policies to manage inter-VLAN communication and secure network segmentation. Implemented access control rules allowing workstation systems (VLAN 20) to communicate with Security Onion services on ports 8220, 8443, and 9200, supporting Elastic Agent enrollment, Fleet management, and centralized log collection.

 <img width="1043" height="343" alt="Screenshot 2026-06-09 at 7 34 22 PM" src="https://github.com/user-attachments/assets/358cddaa-7c44-4e0f-8bf3-ea2cf2fd123e" />

  

---

### Network Security
- Restricted communication between VLANs using firewall policies
- Validated connectivity using ICMP, TCP port testing, and packet filtering
- Monitored network traffic through Security Onion and Zeek
- Troubleshot routing, DNS resolution, and Elastic Agent communication issues

---

### Virtual Networking
- Configured Proxmox network bridges and virtual NIC assignments
- Integrated pfSense as the primary virtual firewall/router
- Connected virtual machines across segmented VLAN environments


--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
## Lessons Learned

- Improved understanding of VLAN segmentation, inter-VLAN routing, and firewall rule processing within pfSense.

- Gained hands-on experience troubleshooting Elastic Agent enrollment, Fleet communication issues, and Security Onion connectivity across segmented networks.

- Strengthened knowledge of network troubleshooting by diagnosing DNS resolution failures, blocked ports, routing issues, and firewall misconfigurations.

- Learned how NAT rules, interface assignments, and rule order impact traffic flow within virtualized environments.

- Developed practical experience deploying and maintaining virtualized infrastructure using Proxmox VE, including network bridges, virtual switches, storage management, and multi-VM environments.

- Gained hands-on experience deploying and administering Active Directory, including creating organizational units (OUs), managing users and groups, joining endpoints to the domain, and implementing role-based access controls.

- Strengthened understanding of enterprise identity and access management concepts through Active Directory user lifecycle management, authentication, authorization, and security group administration.

- Learned how to design, implement, and troubleshoot Group Policy Objects (GPOs) to enforce centralized security configurations across domain-joined systems.

- Applied password security best practices by configuring domain-wide password policies, including password complexity requirements, minimum password length, password history enforcement, password expiration settings, and account lockout policies.

- Improved understanding of Windows Server administration by integrating DNS, DHCP, Active Directory, and Group Policy services within a centralized domain environment.

- Developed practical troubleshooting skills by resolving domain join issues, Group Policy application problems, user authentication failures, DNS-related Active Directory issues, and endpoint connectivity challenges.

- Improved familiarity with SIEM monitoring, endpoint telemetry, threat detection workflows, and log analysis through Security Onion and Elastic Stack integrations.

- Enhanced documentation and change management practices by maintaining network diagrams, firewall rule documentation, system configurations, and deployment procedures throughout the lab environment.
- Gained hands-on experience integrating on-premises Active Directory with Microsoft Entra ID to simulate a hybrid enterprise identity environment.
- Strengthened understanding of identity synchronization, device registration, Hybrid Azure AD Join, and cloud-based endpoint management workflows.
- Developed troubleshooting experience using `dsregcmd /status` to validate domain join state, Azure AD join state, SSO status, and hybrid join errors.
- Improved understanding of how Microsoft Intune supports endpoint administration, device compliance, BitLocker recovery, and user-device ownership management.

