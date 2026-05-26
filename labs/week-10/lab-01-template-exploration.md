# Lab 01: Explore and Duplicate a Certificate Template

**Student Name: Alex B.  
**Date Completed: 5/17/26
**Phase:** 2 | **Week:** 10  
**Submission Path:** `labs/week-10/lab-01-template-exploration.md`

---

## Pre-Lab Verification

Run the following on PKI-SRV01 before starting. Do not proceed until all checks pass.

```powershell
# Check 1 — CA service running
Get-Service -Name CertSvc

# Check 2 — CA responding
certutil -ping

# Check 3 — Issuing CA cert in enterprise store
certutil -store -enterprise CA
```

**All checks passed:**
- [X] Yes
- [ ] No — describe the issue and how you resolved it:

```
Get-Service -Name CertSvc

Status   Name               DisplayName
------   ----               -----------
Running  CertSvc            Active Directory Certificate Services

certutil -ping
Connecting to PKI-SRV01.corp.cvilab.local\CVI Issuing CA 1 ...
Server "CVI Issuing CA 1" ICertRequest2 interface is alive (31ms)
CertUtil: -ping command completed successfully.

 certutil -store -enterprise CA
CA "Intermediate Certification Authorities"
================ Certificate 0 ================
Serial Number: 5800000002f7714edc7f317c46000000000002
Issuer: CN=CVI Root CA, DC=corp, DC=cvilab, DC=local
 NotBefore: 4/25/2026 7:26 PM
 NotAfter: 4/25/2027 7:36 PM
Subject: CN=CVI Issuing CA 1, DC=corp, DC=cvilab, DC=local
CA Version: V0.0
Certificate Template Name (Certificate Type): SubCA
Non-root Certificate
Template: SubCA
Cert Hash(sha1): 5137a597de2c3085ec5816c7f11edc18cfcdbaf8
No key provider information
  Provider = Microsoft Software Key Storage Provider
  Simple container name: CVI Issuing CA 1
  Unique container name: b52f658bb3f263e6f529f3a0187c63bc_f0a99c17-76d3-498a-97de-2992c06105fd
  ERROR: missing key association property: CERT_KEY_IDENTIFIER_PROP_ID
Signature test passed
CertUtil: -store command completed successfully.

Together, these checks validate the CA’s availability, responsiveness, and trust distribution across the enterprise system. In a strict PKI environment, these foundational controls protect uptime and enforce enterprise-wide security. 

```

---

## Part A — Explore Three Built-in Templates

Open the Certificate Templates console: **Run → certtmpl.msc**

### Template 1: User

| Field | Value |
|-------|-------|
| Template Display Name |User |
| Template Name (internal) |User|
| Minimum Supported CA | Window 2000|
| Validity Period |1 year |
| Renewal Period |6 weeks|


```
The user is working on a Windows 2000 PC with a certificate working for 1 year, but will need to be renewed every 6 weeks. It is assigned to publish itself within the active directory only.
```

**Request Handling tab — Purpose:**

```
Signature and Encryption
```

**Subject Name tab — Subject name format:**

```
Built from AD (include e-mail name)
```

**Extensions tab — Key Usage:**

```
Signature requirements:
Digital signature

Allow key exchange only with key encryption
Critical extension.
```

**Extensions tab — Application Policies (EKU):**

```
Encrypting File System
Secure Email
Client Authentication

```

---

### Template 2: Computer

| Field | Value |
|-------|-------|
| Template Display Name |Computer |
| Template Name (internal) |Machine|
| Validity Period |1 year |
| Renewal Period |6 weeks|

**Request Handling tab — Purpose:**

```
Signature and Encryption

```

**Subject Name tab:**

```
Built from AD
```

**Extensions tab — Key Usage:**

```
Signature requirements:
Digital signature

Allow key exchange only with key encryption
Critical extension.
```

**Extensions tab — Application Policies (EKU):**

```
Client Authentication
Server Authentication
```

---

## Part B — Duplicate the Web Server Template

1. Right-clicked the **Web Server** template → **Duplicate Template**
2. Selected compatibility settings:

   - Certification Authority: _Windows Server 2003
   - Certificate Recipient: Windows XP /Windows Server 2003

3. Opened the properties of the new duplicate template.

**General tab — changes made:**

| Setting | Original Value | New Value |
|---------|---------------|-----------|
| Template display name | Web Server | CVI-WebServer |
| Template name | WebServer | CVI-WebServer |
| Validity Period |2 year|
| Renewal Period |6 weeks|

**Rationale for validity period chosen:**
The CRL validity periods must be longer than the publishing interval. Removing a window of exposure removes impostors from disturbing security mechanisms from soft-fail to hard-fail enterprise-wide. I can only assume a strict PKI environment prefers automation, but prefers their certificates to have shorter lifetimes.
```
When a timeframe is chosen, it allows for a strict environment such as PCI-DDS to secure data transmission, for NIST 800-57 to align with its cryptographic key management, and supports the industry's internal governance policies.

```

**Subject Name tab — changes made:**

| Setting | Change Made | Rationale |
|---------|-------------|-----------|

|Build from AD Directory | Subject name form: Fully distinguished name, DNS Name, and User Principal.| Enterprise systems will require the DNS hostname to match the identity of the certificate since it represents the certificate's authentication.|

**Security tab — permissions confirmed:**

| Group / Account | Enroll | Autoenroll |
|-----------------|--------|------------|
| Domain Admins | CORP\Domain Admins|Yes |No|
| Authenticated Users |Authenticated Users |Yes |No|


**Template saved:**
- [X] Yes — template visible in certtmpl.msc

---

## Part C — Inspect the Duplicate Template with certutil


Run the following command on PKI-SRV01:

```powershell
certutil -template CVI-WebServer
``` 

```
Name: Active Directory Enrollment Policy
  Id: {41635678-B3E8-4BD7-8FE7-D49A1E336991}
  Url: ldap:
34 Templates:

  Template[8]:
  TemplatePropCommonName = CVI-WebServer
  TemplatePropFriendlyName = CVI-WebServer
  TemplatePropSecurityDescriptor = O:S-1-5-21-3975454498-3980183307-2685672490-1105G:S-1-5-21-3975454498-3980183307-2685672490-519D:PAI(OA;;RPWPCR;0e10c968-78fb-11d2-90d4-00c04f79dc55;;DA)(OA;;RPWPCR;0e10c968-78fb-11d2-90d4-00c04f79dc55;;S-1-5-21-3975454498-3980183307-2685672490-519)(OA;;CR;0e10c968-78fb-11d2-90d4-00c04f79dc55;;AU)(A;;CCDCLCSWRPWPDTLOSDRCWDWO;;;DA)(A;;CCDCLCSWRPWPDTLOSDRCWDWO;;;S-1-5-21-3975454498-3980183307-2685672490-519)(A;;CCDCLCSWRPWPDTLOSDRCWDWO;;;S-1-5-21-3975454498-3980183307-2685672490-1105)(A;;LCRPWPLORCWDWO;;;AU)

    Allow Enroll        CORP\Domain Admins
    Allow Enroll        CORP\Enterprise Admins
    Allow Enroll        NT AUTHORITY\Authenticated Users
    Allow Full Control  CORP\Domain Admins
    Allow Full Control  CORP\Enterprise Admins
    Allow Full Control  CORP\pki.admin
    Allow Write NT AUTHORITY\Authenticated Users


CertUtil: -Template command completed successfully.
```

**From the certutil output — record the following:**

| Field | Value from certutil Output |
|-------|---------------------------|
| Template Name |Active Directory Enrollment Policy |
| Template OID |{41635678-B3E8-4BD7-8FE7-D49A1E336991} |
| Schema Version | 2|
| Key Usage |Digital Signature, Key Encipherment (a0) |
| Enhanced Key Usage (EKU) |Server Authentication (1.3.6.1.5.5.7.3.1) |
| Validity Period |2 years |
| Subject Name flags |   CT_FLAG_SUBJECT_ALT_REQUIRE_UPN -- 2000000 (33554432)
    CT_FLAG_SUBJECT_ALT_REQUIRE_DNS -- 8000000 (134217728)
    CT_FLAG_SUBJECT_REQUIRE_DIRECTORY_PATH -- 80000000 (-2147483648) |

---

## Reflection

**Why does AD CS require you to duplicate a built-in template rather than modifying it directly?**

```
The configuration from the first certificate creates a blueprint for the next certificate. Modifying an EKU or Validity periods can potentially break servers and domain controllers. This exposure increases risks in the areas of compliance and governance.

```

**One setting in the template you found unexpected or would want to explore further:**

```
The extension tab seems interesting, and wonder what approach is required to make it of use.
```

---



### Template 3: Web Server

| Field | Value |
|-------|-------|
| Template Display Name |Web Server|
| Template Name (internal) |WebServer|
| Validity Period |2 years|
| Renewal Period |6 weeks|

**Request Handling tab — Purpose:**

```
Signature and Encryption
```

**Subject Name tab:**

```
Supplied in request
```

**Extensions tab — Key Usage:**

```
Signature requirements:
Digital signature
```

**Extensions tab — Application Policies (EKU):**

```
Server Authentication
```

---

### Template Comparison

In your own words, what is the most significant difference between the User, Computer, and Web Server templates?

```
Each tab provides areas of strength and security based on its operation within the certificate.  Each area defines its use with a standard based on the configuration of the template.  The User template displays name, supported CA, validity, and renewal periods.  The computer and web server templates display the same information, minus the Minimum Supported CA. 
```

Why does the Web Server template use "Supplied in the request" for the subject name rather than building it from Active Directory?

```
The value of the subject name flags confirms that when the request is made, the subject must be supplied in the request.  
```

---

