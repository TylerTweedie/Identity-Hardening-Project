Markdown
# Project: Personal Identity Hardening & Credential Lifecycle Management

## 📌 Project Overview
This project demonstrates the systematic auditing, securing, and hardening of personal digital assets against modern cyber threats. By implementing enterprise-grade credential management via **Bitwarden** and enforcing **Two-Factor Authentication (2FA)** across high-value targets (Email, Banking, and Social Media), this project showcases practical knowledge of IAM (Identity and Access Management) best practices, risk reduction, and defense-in-depth methodologies.

---

## 🎯 Threat Model & Motivation
In cybersecurity, the "human element" and credential vulnerability remain the top attack vectors. The primary security objectives of this deployment were:

1. **Eliminate Credential Stuffing Risk:** Replacing weak, reused passwords with globally unique, high-entropy strings to prevent a single data breach from compromising multiple accounts.
2. **Mitigate Phishing Impact:** Utilizing an integrated password manager browser extension that detects URL mismatches, effectively neutralizing basic credential-harvesting phishing sites.
3. **Protect Sensitive PII & Financial Assets:** Securing critical nodes (Gmail, Online Banking, Instagram) to prevent identity theft, unauthorized financial exfiltration, and social engineering pivots.

---

## 🛠️ Architecture & Workflow

The image below outlines the end-to-end blueprint implemented to audit and harden the digital footprint:

<p align="center">
<img src="https://github.com/TylerTweedie/Identity-Hardening-Project/blob/main/Securing%20my%20digital%20identity.png?raw=true" alt="Securing My Digital Identity" width="200%" />
</p>

---

## 🚶‍♂️ Step-by-Step Implementation Walkthrough

### Step 1: Motivation & Asset Identification
* **Objective:** Map out high-value personal applications containing sensitive Personally Identifiable Information (PII) and financial data.
* **Target Assets:** Primary Email (Gmail), Financial Institutions (Banking), and Social Media (Instagram).
* **Security Rationale:** Compromise of a primary email allows an attacker to reset passwords across almost every other connected service.

### Step 2: Bitwarden Deployment & Vault Syncing
* **Action:** Deployed the Bitwarden client across desktop, browser extensions, and mobile devices.
* **Master Password Strategy:** Configured a high-entropy, memorable master passphrase combined with a strict PBKDF2 or Argon2id key derivation function iteration count to maximize local encryption strength.
* **Verification:** Enforced secure cloud vault syncing and enabled biometric locking for secure, frictionless access.

### Step 3: Strong Password Generation Lifecycle
* **Action:** Audited existing credentials and replaced them using Bitwarden's built-in generator.
* **Cryptographic Standards:** All new passwords were set to a minimum of **16–24 characters**, containing an randomized mix of uppercase, lowercase, numbers, and special characters (`<3#fG&p!`).
* **Implementation:** Leveraged the Bitwarden extension to auto-fill credentials, reducing exposure to clipboard-sniffing malware.

### Step 4 & 5: Implementing Multi-Factor Authentication (MFA/2FA)
* **Action:** Enforced 2FA across all targeted applications using secure Time-based One-Time Passwords (TOTP) and hardware keys where supported.
* **Gmail:** Enabled Google 2-Step Verification, storing backup codes securely off-system.
* **Instagram:** Moved away from vulnerable SMS-based 2FA to authenticator-app-based TOTP.
* **Automation:** Integrated the TOTP generation directly into Bitwarden to streamline the secure login process while maintaining strict multi-factor isolation.

### Step 6: Securing High-Risk Financial Nodes
* **Action:** Applied the highest available tier of security policies to online banking applications.
* **Controls Implemented:** Mandatory MFA on every login attempt (session-based timeouts), distinct high-entropy credentials separate from daily-use applications, and active login notification alerts.

---

## 📊 Security Outcomes & Key Takeaways

| Metric / Risk Vector | Before Project | After Project (Hardened State) |
| :--- | :--- | :--- |
| **Password Reuse** | Moderate (Vulnerable to Credential Stuffing) | **Zero** (100% Unique, High-Entropy Passwords) |
| **Authentication Strength** | Single-Factor (Password Only) | **Multi-Factor (2FA/TOTP Enabled Everywhere)** |
| **Phishing Resistance** | Low (Susceptible to Look-alike Domains) | **High** (Bitwarden will not auto-fill on unverified URLs) |
| **Credential Management** | Manual / Unencrypted Browser Storage | **AES-256 Bitwarden Encrypted Vault** |
