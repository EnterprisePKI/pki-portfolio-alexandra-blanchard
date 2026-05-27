# Lab 02: Issue Your First Certificate from a Custom Template

**Student Name:  Alex Blan
**Date Completed: 5/18/26
**Phase:** 2 | **Week:** 10  
**Submission Path:** `labs/week-10/lab-02-first-issuance.md`

---

## Pre-Lab Verification

Run on PKI-SRV01 before starting.

```powershell
Get-Service -Name CertSvc
certutil -ping
```

**CertSvc status:** Server "CVI Issuing CA 1" ICertRequest2 interface is alive (63ms)
**CA responding (certutil -ping):**
- [X] Yes
- [ ] No — action taken:

**CVI-WebServer template visible in certtmpl.msc (from Lab 01):**
- [X] Yes
- [ ] No — complete Lab 01 before proceeding

---

## Part A — Publish the Template to the CA

The CVI-WebServer template exists in Active Directory but is not yet published to CVI Issuing CA 1. Publishing it makes it available for certificate requests.

**Steps performed on PKI-SRV01:**

1. Opened **certsrv.msc**
2. Expanded **CVI Issuing CA 1** → right-clicked **Certificate Templates** → **New → Certificate Template to Issue**
3. Selected **CVI-WebServer** from the list
4. Clicked **OK**

**CVI-WebServer template now visible under Certificate Templates node:**
- [X] Yes
- [ ] No — describe what happened:

```
The results of Lab 01 were noticed when the step to publish the template was completed. The blueprint of CVI- Webserver populates amongst the list of Certificate Templates allowing for it to be used successfully.
```
<img width="740" height="510" alt="CVI-WebServer Node" src="https://github.com/user-attachments/assets/168bd729-71db-4038-b1cc-80892e2bae9b" />



```
The output for certsrv.msc resulted in producing a server authenticated 
```

---

## Part B — Request the Certificate via MMC

**Steps performed on PKI-SRV01, logged in as CORP\pki.admin:**

1. Opened **mmc.exe** → **File → Add/Remove Snap-in**
2. Added **Certificates** snap-in
3. Selected: Computer account 
4. Navigated to **Personal → Certificates**
5. Right-clicked → **All Tasks → Request New Certificate**
6. Proceeded through the Certificate Enrollment wizard

**Certificate Enrollment wizard — enrollment policy selected:**

```
Active Directory Enrollment Policy
```

**Templates shown in the wizard:**

```
(list all templates visible)
```

**CVI-WebServer template visible:**
- [X] Yes
- [ ] No — troubleshooting steps taken:

**Subject name entered (if prompted):**

```
Auto-populated
```

**Certificate request submitted:**
- [X] Yes — certificate issued immediately
- [ ] Yes — certificate pending manager approval
- [ ] No — error encountered:

```
(paste error here if applicable)
```

---

## Part C — Inspect the Issued Certificate

### In the MMC Certificates Snap-in

Navigate to the Personal → Certificates store and double-click the issued certificate.

**General tab:**

| Field | Value |
|-------|-------|
| Issued to |CVI Issuing CA 1 |
| Issued by |CVI Root CA |
| Valid from |4/25/2026 |
| Valid to |4/25/2007 |

**Details tab — record the following fields:**

| Field | Value |
|-------|-------|
| Serial Number |5800000002f7714edc7f317c46000000000002 |
| Signature Algorithm | sha256RSA|
| Subject | CN = CVI Issuing CA 1
DC = corp
DC = cvilab
DC = local|
| Key Usage |Digital Signature, Certificate Signing, Off-line CRL Signing, CRL Signing (86)
 |
| Enhanced Key Usage | |
| Subject Alternative Name (if present) |n/a |
| Thumbprint |5137a597de2c3085ec5816c7f11edc18cfcdbaf8 |

---

### Via certutil

Export the certificate thumbprint from the Details tab, then run:

```powershell
certutil -store My "<thumbprint>"
```

Replace `<thumbprint>` with the thumbprint value (no spaces).

**Full certutil output:**

```
My "Personal"
================ Certificate 2 ================
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
  Key Container = CVI Issuing CA 1
  Unique container name: b52f658bb3f263e6f529f3a0187c63bc_f0a99c17-76d3-498a-97de-2992c06105fd
  Provider = Microsoft Software Key Storage Provider
Signature test passed
CertUtil: -store command completed successfully.
```

---

### In certsrv.msc — Issued Certificates Node

Navigate to **certsrv.msc → CVI Issuing CA 1 → Issued Certificates**.

**Does the certificate appear in the Issued Certificates node?**
- [X] Yes

**Record from the Issued Certificates node:**

| Column | Value |
|--------|-------|
| Request ID |3|
| Requester Name |CORP\PKI-SRV01$ |
| Certificate Template |Machine|
| Issued Common Name |PKI-SRV01.corp.cvilab… |
| Certificate Expiration Date |4/25/2027 |

---

## Part D — Write-Up: The Issuance Workflow

Describe the full certificate issuance workflow in your own words. Cover:

1. What happened in Active Directory when you published the template
2. What the MMC Certificate Enrollment wizard sent to the CA
3. What the CA evaluated before issuing the certificate
4. Where the issued certificate was placed and why

```
When publishing the template within the Active Directory, it stored the template, and it included the template’s EKU, Key Usage, validity period, subject name, key size, and enrolment selections. The template was not automatically active for the wizard to see it. A few commands were used to ensure it was explicitly issued. The command used were:

```certutil -template CVI-WebServer
certutil -adca
certsrv.msc
certutil -template

The wizard generated a private key, CSR, Subject, key usage, and EKU. To say the least CA validated enrollment permissions and template compatibility.Therefore , confirming issuance with the certutil -store My command.Since the certificate lived in the computer account/local computer it allowed for TLS services to operate efficiently. 

**One thing about the issuance process that you did not expect or want to understand better:**

```
I did not expect for the template must be explicitly issued on the CA using “Certificate Template to Issue,” and compatibility settings can prevent it from appearing in the wizard.
