
# Lab 02: AD CS Console Exploration & CA Hierarchy Documentation

**Student Name: Alex B.
**Date Completed: 5/10/26
**Phase:** 2 | **Week:** 9  
**Submission Path:** `labs/week-09/lab-02-environment-documentation.md`

---

## Part A — AD CS Console Exploration (PKI-SRV01)

### CA Console Nodes — Observations

| Node | Contents / Observations |
|------|------------------------|
| Revoked Certificates | There are no items to show in this view. |
| Issued Certificates | There are no items to show in this view. |
| Pending Requests | There are no items to show in this view. |
| Certificate Templates |Temjplate information could not be loaded. The specific domain either does not exist or could not be contacted.|

### CA Properties — Key Settings

**General Tab**
- CA Name: Certificate #0
- Computer Name: PKI-SRV01

**Extensions Tab — CRL Distribution Points (CDP):**

```
C:\Windows\Systems32\CertSrv\CertEnroll\...
```

**Extensions Tab — Authority Information Access (AIA):**

```
Idap:///CN=<TruncatedName>.CN…
```

**Storage Tab**
- Database Path: C:\Windows\system32\CertLog
- Log Path: C:\Windows\system32\CertLog

### Certificate Templates Console (certtmpl.msc)

Templates visible in the forest (list what you observed):

```
Temjplate information could not be loaded. The specific domain either does not exist or could not be contacted.
```

---

## Part B — CA Hierarchy Verification (PKI-SRV01)

### Command: certutil -store -enterprise Root

```
PS C:\Windows\system32> certutil -store -enterprise Root
Root "Trusted Root Certification Authorities"
================ Certificate 0 ================
Serial Number: 26373e51a6ab669340c47caef2232ce1
Issuer: CN=CVI Root CA, DC=corp, DC=cvilab, DC=local
 NotBefore: 4/25/2026 6:15 PM
 NotAfter: 4/25/2046 6:25 PM
Subject: CN=CVI Root CA, DC=corp, DC=cvilab, DC=local
CA Version: V0.0
Signature matches Public Key
Root Certificate: Subject matches Issuer
Cert Hash(sha1): b805e6ab548f6e7c57d3989f61de7fe6a51031d1
No key provider information
Cannot find the certificate and private key for decryption.
CertUtil: -store command completed successfully.

```

**What did you see?** (Subject, Issuer, Thumbprint — describe in your own words):

```
The output provides the Unique identifier, Issuer, the CA’s validity period, Root Certificate, Subject, CA Version, and the certs assigned sha1 algorithm.
```

### Command: certutil -store -enterprise CA

```
PS C:\Windows\system32>  certutil -store -enterprise CA
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

```

**What did you see?** (Subject, Issuer, Thumbprint — describe in your own words):

```
The output includes serial number, issuer, validity period, subject, CA version, the CA template, and Non-root Certificate. 
```

---

## Part C — Active Directory Structure (DC01)

### Active Directory Users and Computers (dsa.msc)

**PKI Admins OU — accounts found:**

```
Cert Manager
PKI Admin
PKI Admin
```

**pki.admin account — group memberships:**

```
Domain Admins
Domain Users
PKI Admin
```

**cert.manager account — group memberships:**

```
Domain Users
PKI Admi
```

**Domain-joined computer accounts found:**

```
PKI Admins
```

### Active Directory Sites and Services (dssite.msc)

**Server registered under Default-First-Site-Name:**

```
DNS Settings
```

### Certificate Templates Console (certtmpl.msc on DC01)

Did templates appear here, confirming they are stored in AD?
- [ ] Yes
- [X] No — describe what happened: Error Message - Windows cannot find ‘certtmpl.msc’. Make sure you typed the name correctly, and then try again.
The templates proceeded to populate further into the lab notes.
---

## Part D — Environment Summary Write-Up

### 1. Environment Topology

*(Describe the three VMs, their roles, and IP addresses.)*

DCO1 - 192.168.10.10
PKI-SRV01 - 192.168.10.20
Root-CA - 192.168.10.30

### 2. CA Hierarchy

A Root CA is kept offline for security reasons, it not domain joined, and is only turned on on an as needed basis. The Issuing CA comes from the PKI-SVR01 computer.

### 3. Certificate Templates

Name	Intended Purpose
Directory Email Replication	Directory Service Email Replication
Domain Controller Authentication	Client Authentication, Server Authentication, Smart Card Logon
Kerberos Authentication	Client Authentication, Server Authentication, Smart Card Logon, KDC Authentication
EFS Recovery Agent	File Recovery
Basic EFS	Encrypting File System
Domain Controller	Client Authentication, Server Authentication
Web Server	Server Authentication
Computer	Client Authentication, Server Authentication
User	Encrypting File System, Secure Email, Client Authentication
Subordinate Certification Authority	<All>
Administrator	Microsoft Trust List Signing, Encrypting File System, Secure Email, Client Authentication



### 4. Active Directory Structure

*(Describe the PKI Admins OU. Explain the difference between the pki.admin and cert.manager accounts and their roles.)*

The cert manager is only the member of Users and the PKI Admins OU. PKI Admin is member of Domain Users, and Admin, and PKI Admins.

### 5. One Thing I Found Interesting or Unexpected

I didn’t expect to get an error message from the certtmpl.msc when it is a well known command used to gain access to AD CS.
