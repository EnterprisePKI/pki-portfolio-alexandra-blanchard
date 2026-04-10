
# Lab 01 — Generate a CSR and Simulate the Issuance Workflow

## Overview
Since learning cryptography, generating a CSR focuses on the creation, dissection, and fundamental practices involved in supporting hands-on applications towards this part of PKI. 
The concept in question this week relies heavily on key generation and heavy certificate signing request adaptation.

---

## Environment
- Operating System: In practice, the overall lab environment will stem from the Windows 11 operating system. In practice, the overall lab environment will stem from the Windows 11 operating system.
- Terminal Used: PowerShell with OpenSSL embedded
- OpenSSL Version: OpenSSL 3.6.1 27 Jan 2026 (Library: OpenSSL 3.6.1 27 Jan 2026)

---

## Steps Performed
Once the artifact directory was created, the generation of the RSA key followed the confirmation of the key to ensure it authentic creation. Making sure not to commit the private key publicly, it was securely put away for security's sake.
The lab was then followed by the generation and inspection of the CSR. Analyzing the fields and gathering information on where they can be found. Fields such as CN, O, OU, C, ST, and L.
The next step involved signing the central authority involved in this workflow and, naturally, following up with an inspection to ensure an effective chain of authentication protocols.
The best way to guard against outages is to compare CSR to a signed certificate. Doing so involves keeping the realities of regulation, policies, and sufitng at the forefront of why comparing keys are og high importance. 
5. The relationship between the private key and the certificate is solidified by an empty diff displaying the complete success of key extraction as it decrypts the certificate's message, signaling a successful self-signed certificate.

---

## Results

- What Subject fields did you include in your CSR, and what does each one represent?
Field
Abbreviation
Value in Your CSR

Common Name
CN
lab01.cvi.internal

Organization
O
CyberVisionaries Institute

Organizational Unit
OU
PKI Career Pathway

Country
C
US

State
ST
California

Locality
L
San Francisco


- What is the Issuer field in a self-signed certificate, and why does it match the Subject?
The issuer  (who signs the certificate for the Subject) matches the Subject (Public key owner); they are both under the same organization.

- What did the public key comparison (diff) show, and what does that mean?

  diff /tmp/cert_pubkey.pem /tmp/key_pubkey.pem

InputObject          SideIndicator
-----------          -------------
/tmp/key_pubkey.pem  =>
/tmp/cert_pubkey.pem <=

This means each key isn’t missing major components that would promote failure between the private and public keys.

- How do the fields in your signed certificate connect to what you learned about X.509 in Week 3?
Each field displayed vital information in two forms. They both provided information aligned with the subject and issuer of the certificate. Indicating the trust available to encrypt and decrypt the certificate in question.
 
---

## Key Findings
The lab taught me how to extract the public key from the certification.
To operate in real time, the ability to extract the private key from the public key is sure to prove worthy on the job site. 
Being able to extract the correct information from the Subject field and not seeing it as two separate pieces of information is imperative.

---

## Explanation
- What is the purpose of a CSR in the real certificate issuance workflow?
The CSR tells the CA who you are, where you are coming from, and verifies the private key for the public key.

- Why does the CA receive a CSR rather than a private key?
The private key must remain hidden within the CSR at all times to protect the message it carries. 

- What would it mean if the public key in the certificate did NOT match the private key?
It would’ve caused a failure in the trust chain as well as violate OU and API regulatory practices.
---

## Challenges / Troubleshooting
No challenges were experienced in this lab.

---

## Artifacts

- test_csr.pem
- test_cert.pem
