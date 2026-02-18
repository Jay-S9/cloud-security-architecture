# Azure Infrastructure Security

This section covers preventive security controls in cloud infrastructure.  
Unlike SOC tools that detect attacks, these mechanisms reduce attack surface before compromise occurs.

## Defense in Depth Model
Azure applies layered protection:

Network Edge → Traffic Filtering → Access Control → Secure Access → Secret Protection

The goal is to stop attackers before they reach application or data layers.

## Security Layers
- DDoS Protection – protects service availability
- Firewall / WAF – filters malicious traffic
- Network Segmentation – isolates resources
- NSG – granular traffic rules
- Bastion – secure administrative access
- Key Vault – secret and key protection

This model is widely used in financial infrastructure where availability and confidentiality are critical.

## Changing security perimeter
Traditional security relied on a single network boundary.  
Cloud environments remove this boundary as services, users, and applications operate over the public internet.

Security must therefore protect resources from multiple directions rather than a single entry point.

Azure provides configurable layered controls to protect availability, network access, and sensitive data.

This reflects the shift from perimeter security to distributed security architecture.

## Azure DDoS Protection
DDoS attacks attempt to overwhelm services with excessive traffic, making systems unavailable to legitimate users.

Azure DDoS Protection filters malicious traffic before it reaches application infrastructure.

### Protection mechanism
- Learns normal traffic patterns
- Detects abnormal spikes
- Drops attack traffic
- Allows legitimate users

### Attack layers
- L3 (Network): volumetric bandwidth flooding
- L4 (Transport): connection exhaustion
- L7 (Application): handled separately by WAF

### Why needed beyond default protection
Azure infrastructure protection safeguards the platform, but application-specific DDoS protection applies tuned thresholds and monitoring to protect individual services.

Availability protection is critical in financial systems where downtime directly impacts transactions.

## Azure Firewall
Azure Firewall is a managed, cloud-based traffic control system that filters inbound and outbound network traffic based on defined security rules.

### Architecture model
Often deployed in a centralized hub-and-spoke model:
- Central VNet hosts the firewall
- All other VNets route traffic through it
- Enables centralized traffic governance

### Key capabilities
- Stateful inspection (tracks active connections)
- Network-level filtering (IP, port, protocol)
- Application-level filtering (FQDN / HTTP/S rules)
- Source and Destination NAT (SNAT/DNAT)
- Threat intelligence-based blocking
- Built-in high availability across zones

### Financial infrastructure relevance
Firewalls enforce strict traffic control policies between:
- Internet and applications
- Internal microservices
- Cloud and on-premises systems

Centralized firewall design improves auditability and policy consistency.

### Integration with Security Copilot
Firewall logs can be sent to Log Analytics and analyzed via Security Copilot, linking preventive controls with investigative capabilities.

# Azure Network Security Layers

## DDoS Protection
Protects applications from traffic flooding attacks.
- Stops volumetric and protocol attacks
- Works at Layer 3 & 4
- Learns normal traffic patterns
- Automatically mitigates attacks

## Azure Firewall
Central network traffic controller.
- Filters inbound & outbound traffic
- Supports NAT (SNAT/DNAT)
- Uses threat intelligence feeds
- Stateful firewall

## Web Application Firewall (WAF)
Protects web applications from exploits.
- SQL injection
- Cross-site scripting (XSS)
- HTTP flood attacks
- Works at Layer 7

---

### Memory Tip
Flood → DDoS Protection  
Access → Firewall  
Exploit → WAF

## Network Segmentation (Azure VNet)

Network segmentation divides infrastructure into isolated zones to limit damage during a breach.

Why it exists:
- Contain attackers (Assume Breach principle)
- Control communication paths
- Apply governance policies
- Support Zero Trust architecture

### Azure Virtual Network (VNet)
Private network inside Azure cloud.

Key properties:
- Default: no communication allowed between VNets
- Must explicitly allow traffic
- Can create multiple subnets inside a VNet
- Isolates workloads (apps, databases, services)

Security Benefit:
If one segment is compromised → attacker cannot move laterally across the network.

---

### Real World Analogy
Office building:
- HR room
- Finance room
- Server room

Breaking into HR room ≠ access to Finance records

## Azure Network Security Groups (NSG)

NSG filters traffic to and from Azure resources (VMs/Subnets).

Purpose:
Prevent lateral movement after a breach.

---

### How NSG Works
Traffic evaluated using:
- Source IP
- Source Port
- Destination IP
- Destination Port
- Protocol

Rules:
ALLOW or DENY

Lower priority number = evaluated first.

---

### Default Security Behavior
Inbound:
- Allow Virtual Network
- Allow Azure Load Balancer
- Deny all others

Outbound:
- Allow internal traffic
- Allow internet
- Deny rest

---

### NSG vs Azure Firewall

NSG → protects individual VM/subnet (micro protection)
Azure Firewall → protects entire network (macro protection)

Together = Defense in Depth

## Azure Bastion

Azure Bastion provides secure RDP/SSH access to VMs without exposing them to the internet.

Problem:
Opening RDP (3389) or SSH (22) ports allows attackers to brute-force login.

Solution:
Connect through Azure Portal → Bastion → Private IP → VM

---

### Security Benefits
- No public IP required on VMs
- Prevents port scanning attacks
- TLS encrypted connection
- Centralized secure access point
- Reduces attack surface

---

### Architecture
User → HTTPS → Azure Portal → Bastion → Private Network → VM

---

Purpose:
Secure administrative access to cloud servers
