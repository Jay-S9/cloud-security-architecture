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
