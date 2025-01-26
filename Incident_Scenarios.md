# Real-World Incident Simulation Scenarios

This document outlines **five common attack scenarios** and detailed incident response plans for each. The steps include actions to take, tools to use, and PCI DSS requirements addressed at each stage.

---

## **Scenario 1: Phishing Attack**
### **Description:**
An employee receives a phishing email and inadvertently provides login credentials to a malicious actor.

### **Steps for Response:**
1. **Identification:**
   - Monitor SIEM alerts for unusual login attempts or multiple failed login attempts.
   - Verify email content with anti-phishing tools.
   - Check logs for new login sessions from unfamiliar IP addresses.

2. **Containment:**
   - Disable the affected user’s account immediately.
   - Block the malicious IP address using a firewall.
   - Notify other employees to avoid similar phishing emails.

3. **Eradication:**
   - Remove the phishing email from all inboxes using email security tools.
   - Scan the affected system for malware or malicious scripts.

4. **Recovery:**
   - Reset the compromised user’s credentials.
   - Enable multi-factor authentication (MFA) for all users.

5. **Lessons Learned:**
   - Conduct a phishing awareness session for employees.
   - Update email security filters to block similar phishing emails.

### **Tools to Use:**
- Email security gateway (e.g., Proofpoint, Mimecast).
- SIEM tool (e.g., Splunk, ELK Stack).
- Endpoint protection software (e.g., CrowdStrike, Sophos).

### **PCI DSS Requirements Addressed:**
- **Requirement 10.6**: Log reviews to detect anomalies.
- **Requirement 8.3**: Implement multi-factor authentication.
- **Requirement 12.10.5**: Define roles and responsibilities in incident response.

---

## **Scenario 2: Ransomware Attack**
### **Description:**
A workstation connected to the CHD environment is infected with ransomware, encrypting critical files.

### **Steps for Response:**
1. **Identification:**
   - Monitor alerts for file encryption activities or unusual file extensions.
   - Detect abnormal system resource usage.

2. **Containment:**
   - Isolate the infected system from the network.
   - Block suspicious processes and connections using EDR tools.
   - Disable shared drives temporarily.

3. **Eradication:**
   - Remove ransomware using antivirus and endpoint protection software.
   - Perform a vulnerability scan to identify the root cause (e.g., unpatched software).

4. **Recovery:**
   - Restore encrypted files from secure backups.
   - Patch the vulnerability exploited by the ransomware.

5. **Lessons Learned:**
   - Conduct vulnerability assessments to strengthen defenses.
   - Update backup policies to ensure data availability.

### **Tools to Use:**
- Endpoint Detection and Response (EDR) tools (e.g., CrowdStrike Falcon, Carbon Black).
- Backup and recovery tools (e.g., Veeam, Rubrik).
- Vulnerability scanners (e.g., Nessus, OpenVAS).

### **PCI DSS Requirements Addressed:**
- **Requirement 6.2**: Ensure all systems are patched and up-to-date.
- **Requirement 9.5**: Maintain secure backups of critical systems.
- **Requirement 11.4**: Deploy tools to detect and respond to malware.

---

## **Scenario 3: Unauthorized Access to Cardholder Data (CHD)**
### **Description:**
A malicious actor gains unauthorized access to a database containing CHD.

### **Steps for Response:**
1. **Identification:**
   - Review access logs for anomalies (e.g., failed login attempts, new users).
   - Detect unusual database queries or bulk data exports.

2. **Containment:**
   - Temporarily disable access to the affected database.
   - Revoke suspicious accounts and reset credentials.
   - Block unauthorized IPs at the firewall level.

3. **Eradication:**
   - Audit database permissions to remove excessive privileges.
   - Implement additional access controls (e.g., role-based access control).

4. **Recovery:**
   - Restore database from the last known secure backup.
   - Monitor access to the database closely post-incident.

5. **Lessons Learned:**
   - Strengthen access controls and password policies.
   - Enable encryption for all stored CHD.

### **Tools to Use:**
- Database activity monitoring tools (e.g., SolarWinds Database Performance Analyzer).
- Firewalls and Intrusion Detection/Prevention Systems (IDS/IPS).
- Encryption tools (e.g., HashiCorp Vault).

### **PCI DSS Requirements Addressed:**
- **Requirement 3.4**: Encrypt stored CHD.
- **Requirement 7.1**: Restrict access based on roles and responsibilities.
- **Requirement 10.2**: Enable logging for all access to CHD.

---

## **Scenario 4: Web Application Attack (SQL Injection)**
### **Description:**
An attacker exploits a vulnerability in a web application to execute unauthorized SQL queries.

### **Steps for Response:**
1. **Identification:**
   - Monitor WAF alerts for SQL injection attempts.
   - Review logs for suspicious database queries.

2. **Containment:**
   - Block the malicious IP address using a WAF or firewall.
   - Disable the vulnerable feature of the web application temporarily.

3. **Eradication:**
   - Patch the application to address the SQL injection vulnerability.
   - Update input validation rules to sanitize user inputs.

4. **Recovery:**
   - Test the application for other vulnerabilities before bringing it back online.
   - Monitor application traffic for abnormal activity.

5. **Lessons Learned:**
   - Conduct regular application security assessments.
   - Implement automated vulnerability scanning for web applications.

### **Tools to Use:**
- Web Application Firewall (e.g., ModSecurity, AWS WAF).
- Vulnerability scanners (e.g., Burp Suite, Nessus).
- Secure coding frameworks (e.g., OWASP Dependency-Check).

### **PCI DSS Requirements Addressed:**
- **Requirement 6.5**: Protect against common coding vulnerabilities.
- **Requirement 6.6**: Implement a WAF for public-facing web applications.
- **Requirement 11.2**: Conduct regular vulnerability scans.

---

## **Scenario 5: Insider Threat**
### **Description:**
A disgruntled employee intentionally misuses access to CHD systems.

### **Steps for Response:**
1. **Identification:**
   - Monitor for unusual access patterns, such as after-hours access.
   - Review logs for unauthorized data exports or privilege escalations.

2. **Containment:**
   - Suspend the employee’s access immediately.
   - Lock down affected systems to prevent further misuse.

3. **Eradication:**
   - Audit all permissions granted to the insider.
   - Remove any backdoors or unauthorized changes made by the insider.

4. **Recovery:**
   - Restore affected systems from backups if necessary.
   - Reassign responsibilities to prevent operational disruption.

5. **Lessons Learned:**
   - Conduct regular employee background checks.
   - Enhance logging and monitoring for insider activities.

### **Tools to Use:**
- Privileged Access Management (PAM) tools (e.g., CyberArk, BeyondTrust).
- SIEM tools for access logging (e.g., Splunk, Graylog).
- Endpoint monitoring software (e.g., CrowdStrike).

### **PCI DSS Requirements Addressed:**
- **Requirement 8.1.4**: Restrict user access promptly when roles change.
- **Requirement 10.3**: Enable detailed logging for all activities.
- **Requirement 12.7**: Screen personnel before granting access to CHD.
