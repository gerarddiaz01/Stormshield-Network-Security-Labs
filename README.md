# Stormshield Network Security (CSNA Lab Configuration)

![Certification](https://img.shields.io/badge/Certification-CSNA-success?style=flat-square)
![Focus](https://img.shields.io/badge/Focus-Network_Security-005571?style=flat-square)
![Vendor](https://img.shields.io/badge/Vendor-Stormshield-red?style=flat-square)

**Deployment and hardening of a network infrastructure built on Stormshield SNS appliances.**

This repository documents all the technical labs I completed while preparing for the **CSNA (Certified Stormshield Network Administrator)** certification.

> **Note on language:** I prepared and passed the CSNA within a French-language program. The procedure documents linked below are written in French. This README gives the full overview in English.

## Lab Architecture

| Component | Role | Configuration |
| :--- | :--- | :--- |
| **Firewall** | Stormshield SNS (EVA) | Filtering, NAT, IPS, SSL VPN |
| **LAN Zone** | Trust | `192.168.1.0/24`, administration |
| **DMZ Zone** | Public services | `172.16.0.0/24`, Web & DNS |
| **WAN** | Untrust | Internet access (simulated) |

## Technical Documentation (My Procedures)

The operational guides I wrote, based on ANSSI best practices and the official Stormshield documentation:

### Initialization & System
- [00 - Standard Deployment Procedures](./00-Deployment-Standard-Procedures.md) : *initial hardening, breaking the default bridge, boot partition management.*
- [01 - Initial Configuration & Log Management](./01-Initial-Configuration-and-Log-Management.md) : *securing the administration plane and log retention strategy.*

### Architecture & Security
- [02 - Network Objects Management](./02-Network-Objects-Management.md) : *structuring the object base, creating custom services, and automation (CSV import).*
- [03 - Network Configuration: Interfaces & Routing](./03-Network-Interfaces-and-Routing.md) : *defining zones (LAN/DMZ/WAN), static routing, and DNS Proxy setup.*
- [04 - Address Translation (NAT)](./04-Address-Translation-NAT.md) : *Masquerading (SNAT), service publishing via BIMAP, and port redirection (PAT).*
- [05 - Filtering Policy & Security Monitoring](./05-Traffic-Filtering-and-Security-Monitoring.md) : *strict filtering (LAN/DMZ), application controls (URL/GeoIP), log configuration, and alarm raising.*
- [06 - Web Content Filtering (HTTP & HTTPS)](./06-Content-Filtering-HTTP-HTTPS.md) : *application-layer access control (Layer 7), URL filtering strategy, and SSL/TLS inspection (SNI) without decryption.*
- [07 - Authentication & Identity-Based Filtering](./07-Authentication-and-Identity-Based-Filtering.md) : *LDAP directory integration, captive portal (enrollment), the shift from IP filtering to identity filtering (Layer 8), and administration rights delegation.*

### Remote Connectivity & VPN
- [08 - Secure Remote Access (SSL VPN)](./08_VPN_SSL_Client_Access.md) : *Client-to-Site SSL VPN (OpenVPN), virtual IP pool management, Split/Full Tunneling, roaming user authentication, and strict filtering of tunneled flows.*

## Skills Demonstrated

- **SNS Administration:** command of the Web interface and the CLI recovery commands.
- **Network Segmentation:** building airtight security zones (LAN/DMZ/WAN).
- **Risk Management:** applying least privilege to traffic flows.
- **Maintenance:** firmware lifecycle management (Active/Passive partitions).

---
*This project was carried out on a personal virtualization environment.*