# DEVSECOPS

## What is DevSecOps?

DevSecOps means integrating **security controls throughout the Software Development Life Cycle (SDLC)** instead of treating security as a final manual stage.

The main goal of DevSecOps is to:

* Detect security issues early.
* Automate security checks.
* Enforce security policies in CI/CD pipelines.
* Continuously monitor applications and infrastructure in production.
* Make security a shared responsibility between Development, Security, and Operations teams.

---

# What Does a DevSecOps Engineer Do in Daily Work?

A DevSecOps Engineer performs the following activities:

* Integrates security into the development lifecycle.
* Performs **SAST (Static Application Security Testing)**.
* Performs **SCA (Software Composition Analysis)**.
* Scans repositories for **secret leakage**.
* Secures **Infrastructure as Code (IaC)**.
* Scans **container images** for vulnerabilities.
* Performs **DAST (Dynamic Application Security Testing)**.
* Automates security checks in **CI/CD pipelines**.
* Enforces **security gates**.
* Monitors applications and infrastructure.
* Manages vulnerabilities.
* Implements security as a **shared responsibility**.
* Performs **code quality checks**.
* Performs **code smell checks**.
* Performs **CI/CD security scanning**.

---

# DevSecOps Security Flow

```text
Developer Code Commit
        |
        v
Git Repository
        |
        +---- Secret Scanning
        |
        +---- SAST
        |
        +---- Code Quality Check
        |
        +---- Code Smell Check
        |
        +---- SCA / Dependency Scanning
        |
        v
Application Build
        |
        +---- IaC Security Scan
        |
        +---- Container Image Scan
        |
        v
Security Gates
        |
        v
Deployment
        |
        +---- DAST
        |
        v
Production
        |
        +---- Runtime Security Monitoring
        |
        +---- Vulnerability Management
```

---

# Tools and Technologies Used in DevSecOps

## 1. Securing Code

### Tools

* SonarQube
* Checkmarx

These tools are mainly used for:

* Static code analysis.
* Finding security vulnerabilities.
* Code quality checks.
* Code smell detection.
* Bug detection.
* Security hotspot detection.

---

## 2. Scanning Dependencies and Libraries

### Tools

* OWASP Dependency-Check
* Snyk

This is also known as:

**SCA – Software Composition Analysis**

These tools scan third-party dependencies and libraries used inside an application.

They help detect:

* Vulnerable libraries.
* Vulnerable packages.
* Known CVEs.
* Outdated dependencies.
* Open-source security issues.

**Snyk is pronounced as "Sneek".**

---

## 3. Detecting Secrets

### Tools

* Gitleaks
* GitGuardian

Secret scanning is used to detect sensitive information accidentally committed to Git repositories.

Examples:

* Passwords.
* API keys.
* Access tokens.
* Private keys.
* AWS credentials.
* Database credentials.
* Authentication tokens.

---

## 4. Scanning Infrastructure as Code

### Tools

* Trivy
* Checkov

These tools scan Infrastructure as Code such as:

* Terraform.
* Kubernetes YAML.
* Dockerfiles.
* CloudFormation templates.

They identify:

* Security misconfigurations.
* Insecure permissions.
* Publicly exposed resources.
* Weak security configurations.
* Policy violations.

---

## 5. Testing Running Applications

### Tools

* OWASP ZAP
* Burp Suite

These tools are mainly used for:

**DAST – Dynamic Application Security Testing**

DAST tests the application while it is running.

It can detect issues such as:

* Injection vulnerabilities.
* Authentication issues.
* Security misconfigurations.
* Exposed endpoints.
* Web application vulnerabilities.
* Access control issues.

---

## 6. Automating Security Checks

### Tools

* GitHub Actions
* GitLab CI/CD
* Jenkins

Security tools are integrated into CI/CD pipelines to automate security checks.

Examples:

* SAST scanning.
* SCA scanning.
* Secret scanning.
* Container scanning.
* IaC scanning.
* DAST scanning.
* Security policy validation.

---

## 7. Scanning Container Images

### Tools

* Trivy
* Grype

Container image scanning checks Docker/container images for vulnerabilities.

It can identify:

* Vulnerable OS packages.
* Vulnerable libraries.
* Known CVEs.
* Critical vulnerabilities.
* High vulnerabilities.
* Medium vulnerabilities.
* Low vulnerabilities.

---

## 8. Blocking Insecure Deployments

### Tools

* SonarQube Quality Gates
* OPA – Open Policy Agent

Security gates are used to stop insecure builds or deployments.

Examples:

* Stop pipeline if Critical vulnerabilities are found.
* Stop pipeline if SonarQube Quality Gate fails.
* Stop deployment if IaC contains serious security issues.
* Prevent insecure Kubernetes configurations.
* Enforce organizational security policies.

---

## 9. Monitoring Production Security

### Tool

* Falco

Falco is mainly used for **runtime security monitoring**.

It monitors suspicious activities occurring inside containers and Kubernetes environments.

Falco can detect:

* Unexpected shell execution.
* Sensitive file access.
* Privilege escalation.
* Suspicious process execution.
* Unexpected system calls.
* Abnormal container behavior.

---

## 10. Vulnerability Management

### Tools

* Snyk
* DefectDojo

These tools help teams:

* Track vulnerabilities.
* Prioritize vulnerabilities.
* Assign vulnerabilities for remediation.
* Manage security findings.
* Generate security reports.
* Monitor vulnerability status.
* Collect findings from multiple security tools.

---

# Main DevSecOps Tools

The main tools to focus on are:

* SonarQube
* Trivy
* OWASP
* Gitleaks

---

# SonarQube

SonarQube is a code quality and static code analysis tool.

It is used for:

* SAST.
* Code quality checking.
* Code smell detection.
* Bug detection.
* Vulnerability detection.
* Security hotspot detection.
* Quality Gate enforcement.

### Example Pipeline Flow

```text
Developer Push
      |
      v
Jenkins
      |
      v
SonarQube Scan
      |
      v
Quality Gate
      |
      +---- Pass ----> Continue Build
      |
      +---- Fail ----> Stop Pipeline
```

---

# Trivy

Trivy is an open-source security scanner.

It can scan:

* Container images.
* Filesystems.
* Git repositories.
* Kubernetes resources.
* Infrastructure as Code.
* Application dependencies.
* Operating system packages.

### Example

```text
Docker Image
     |
     v
Trivy Scan
     |
     +---- Critical Vulnerability Found
     |
     v
Pipeline Failed
```

---

# OWASP

OWASP stands for:

**Open Worldwide Application Security Project**

OWASP provides security guidelines, tools, standards, and awareness for application security.

Important OWASP resources include:

* OWASP Top 10.
* OWASP Dependency-Check.
* OWASP ZAP.

OWASP helps identify and prevent common application security risks.

---

# Gitleaks

Gitleaks is a secret scanning tool.

It scans Git repositories and detects secrets such as:

* Passwords.
* API keys.
* Access tokens.
* Private keys.
* Cloud credentials.
* Database credentials.

It can be integrated into:

* Developer machines.
* Git hooks.
* Pull requests.
* CI/CD pipelines.

---

# Core DevSecOps Concepts

## 1. Shift-Left Security

Shift-left security means moving security activities earlier in the Software Development Life Cycle.

Instead of checking security only before production, security checks are performed during development and CI/CD.

Examples:

* Secret scanning before code merge.
* SAST during CI.
* Dependency scanning.
* IaC scanning.
* Container scanning.

### Goal

Find security problems early so they can be fixed before reaching production.

---

# 2. Shift-Right Security

Shift-right security means continuing security activities after an application has been deployed.

Examples:

* Runtime security monitoring.
* DAST.
* Production monitoring.
* Log monitoring.
* Threat detection.
* Vulnerability monitoring.
* Falco monitoring.

### Goal

Detect security issues that appear when the application is running.

---

# 3. Defense in Depth

Defense in Depth means using multiple layers of security.

Instead of depending on one security control, multiple security controls protect the system.

Example:

```text
Firewall
   |
Authentication
   |
Authorization
   |
Encryption
   |
Container Security
   |
Kubernetes Security
   |
Runtime Monitoring
```

If one security layer fails, another layer continues protecting the system.

---

# 4. Principle of Least Privilege

Least Privilege means giving only the minimum permissions required to perform a task.

Example:

Do not provide Administrator access if a user only requires read access.

Examples in DevOps:

* Limited IAM permissions.
* Kubernetes RBAC.
* Restricted Jenkins permissions.
* Limited service account permissions.
* Read-only access where possible.

---

# 5. Zero Trust

Zero Trust follows the principle:

**Never Trust, Always Verify.**

No user, device, application, or service should automatically be trusted.

Every request should be:

* Authenticated.
* Authorized.
* Validated.
* Monitored.

Important Zero Trust principles:

* Verify identity.
* Use least privilege.
* Assume breach.
* Continuously monitor.
* Restrict unnecessary access.

---

# 6. Security Gates

Security Gates are conditions used to stop an insecure build or deployment.

Examples:

```text
Critical Vulnerability Found
          |
          v
      Pipeline Fail
```

Other examples:

* SonarQube Quality Gate failure.
* Critical Trivy vulnerabilities.
* IaC security violation.
* Secret detected in repository.
* Failed security policy.

---

# 7. Risk Management

Risk Management means identifying, evaluating, prioritizing, and reducing security risks.

Basic process:

```text
Identify Risk
     |
     v
Analyze Risk
     |
     v
Prioritize Risk
     |
     v
Mitigate Risk
     |
     v
Monitor Risk
```

Risk is normally evaluated based on:

* Severity.
* Business impact.
* Exploitability.
* Exposure.
* Likelihood.
* Asset importance.

---

# 8. Threat Modeling

Threat Modeling is the process of identifying possible security threats before or during application design.

It tries to answer:

* What are we protecting?
* Who can attack it?
* How can they attack it?
* What vulnerabilities may exist?
* What controls should be implemented?
* What happens if a control fails?

The correct term is:

**Threat Modeling**

Not:

**Thread Modeling**

---

# 9. Attack Surface

Attack Surface means all possible entry points that attackers can use to attack a system.

Examples:

* APIs.
* Open ports.
* Login pages.
* Public endpoints.
* Cloud resources.
* Third-party dependencies.
* Kubernetes services.
* Containers.
* CI/CD pipelines.
* Exposed secrets.

### Goal

Reduce unnecessary attack surfaces and properly secure required entry points.

---

# 10. CIA Triad

CIA stands for:

* Confidentiality
* Integrity
* Availability

These are the three main principles of information security.

---

## Confidentiality

Confidentiality ensures that sensitive information is accessible only to authorized users.

Examples:

* Encryption.
* Authentication.
* Access control.
* Secrets management.
* IAM.

---

## Integrity

Integrity ensures that data is accurate and cannot be modified without authorization.

Examples:

* Hashing.
* Digital signatures.
* Audit logs.
* Version control.
* File integrity monitoring.

---

## Availability

Availability ensures that applications and data remain accessible whenever required.

Examples:

* High availability.
* Load balancing.
* Backups.
* Disaster recovery.
* Auto Scaling.
* Monitoring.
* Redundancy.

---

# CIA Formula

```text
CIA

C = Confidentiality
I = Integrity
A = Availability
```

---

# Important Security Testing Types

| Security Type      | Full Form                              | Purpose                                           |
| ------------------ | -------------------------------------- | ------------------------------------------------- |
| SAST               | Static Application Security Testing    | Scans source code without running the application |
| DAST               | Dynamic Application Security Testing   | Tests running applications                        |
| SCA                | Software Composition Analysis          | Scans dependencies and third-party libraries      |
| Secret Scanning    | Secret Detection                       | Finds passwords, API keys, tokens and credentials |
| IaC Scanning       | Infrastructure as Code Scanning        | Finds infrastructure security misconfigurations   |
| Container Scanning | Container Image Vulnerability Scanning | Finds vulnerabilities inside container images     |

---

# DevSecOps Tool Mapping

```text
Code Security
     |
     +---- SonarQube
     +---- Checkmarx

Dependency / SCA Scanning
     |
     +---- OWASP Dependency-Check
     +---- Snyk

Secret Scanning
     |
     +---- Gitleaks
     +---- GitGuardian

IaC Scanning
     |
     +---- Trivy
     +---- Checkov

DAST
     |
     +---- OWASP ZAP
     +---- Burp Suite

CI/CD Automation
     |
     +---- Jenkins
     +---- GitHub Actions
     +---- GitLab CI/CD

Container Scanning
     |
     +---- Trivy
     +---- Grype

Security Gates
     |
     +---- SonarQube Quality Gates
     +---- OPA

Production Runtime Security
     |
     +---- Falco

Vulnerability Management
     |
     +---- Snyk
     +---- DefectDojo
```

---

# Main Tools for Interview Preparation

Focus more on these four tools:

## 1. SonarQube

Mainly used for:

* SAST.
* Code quality.
* Code smells.
* Bugs.
* Vulnerabilities.
* Quality Gates.

---

## 2. Trivy

Mainly used for:

* Container scanning.
* Filesystem scanning.
* Repository scanning.
* Kubernetes scanning.
* IaC scanning.
* Vulnerability scanning.

---

## 3. OWASP

Mainly focus on:

* OWASP Top 10.
* OWASP Dependency-Check.
* OWASP ZAP.

---

## 4. Gitleaks

Mainly used for:

* Secret scanning.
* Password detection.
* Token detection.
* API key detection.
* Credential leakage prevention.

---

# Short Interview Answer

**What is DevSecOps?**

DevSecOps is the practice of integrating security throughout the complete Software Development Life Cycle instead of performing security only at the end.

In DevSecOps, we automate security checks such as SAST, SCA, secret scanning, Infrastructure as Code scanning, container image scanning and DAST through CI/CD pipelines.

For example, we can use SonarQube for code quality and SAST, Trivy for container and IaC scanning, Gitleaks for secret scanning, OWASP tools for dependency and dynamic application security testing, and Falco for runtime security monitoring.

We also implement concepts such as Shift-Left Security, Shift-Right Security, Defense in Depth, Least Privilege, Zero Trust, Security Gates, Risk Management, Threat Modeling, Attack Surface reduction and the CIA Triad.

---

# Quick Revision

```text
SonarQube
→ Code Quality
→ SAST
→ Code Smells
→ Quality Gates

Trivy
→ Container Scanning
→ IaC Scanning
→ Filesystem Scanning
→ Kubernetes Scanning

OWASP
→ OWASP Top 10
→ Dependency-Check
→ OWASP ZAP

Gitleaks
→ Secret Scanning

Checkmarx
→ SAST

Snyk
→ SCA
→ Vulnerability Management

GitGuardian
→ Secret Detection

Checkov
→ IaC Scanning

OWASP ZAP
→ DAST

Burp Suite
→ DAST / Web Security Testing

Grype
→ Container Image Scanning

OPA
→ Security Policy Enforcement

Falco
→ Runtime Security Monitoring

DefectDojo
→ Vulnerability Management
```

---

# Core Concepts Quick Revision

```text
Shift Left
→ Security before deployment.

Shift Right
→ Security after deployment / runtime security.

Defense in Depth
→ Multiple security layers.

Least Privilege
→ Minimum required permissions.

Zero Trust
→ Never trust, always verify.

Security Gates
→ Block insecure builds or deployments.

Risk Management
→ Identify, prioritize and reduce risks.

Threat Modeling
→ Identify possible threats and attack paths.

Attack Surface
→ All possible entry points for attackers.

CIA Triad
→ Confidentiality
→ Integrity
→ Availability
```
