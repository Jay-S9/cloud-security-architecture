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
