# Security Management (Defender for Cloud)

Focus:
Continuous monitoring and improvement of cloud security posture.

Unlike infrastructure security (preventive controls),
this layer identifies misconfigurations and active threats.

Key idea:
Security is not a one-time setup — it is continuously evaluated.

## Security Posture Concept
Cloud environments constantly change — new resources, configuration updates, and user actions can weaken security.

Microsoft Defender for Cloud continuously evaluates the environment to detect risks, misconfigurations, and active threats.

Security becomes an ongoing process rather than a one-time configuration.

## Microsoft Defender for Cloud

Microsoft Defender for Cloud is a cloud-native application protection platform that monitors security across development, configuration, and runtime environments.

### Three Pillars

1. DevSecOps
Security during development. Scans repositories, pipelines, and dependencies to prevent insecure code from deployment.

2. Cloud Security Posture Management (CSPM)
Continuously evaluates configurations and provides recommendations to prevent vulnerabilities.

3. Cloud Workload Protection Platform (CWPP)
Detects and responds to threats affecting running workloads such as VMs, containers, databases, and storage.

Security coverage lifecycle:
Build → DevSecOps
Deploy → CSPM
Run → CWPP
