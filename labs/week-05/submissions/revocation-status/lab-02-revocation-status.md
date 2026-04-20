
# Lab 02 — Check Certificate Revocation Status with OCSP

## Overview
The lab allows operations to be conducted to determine whether the OCSP is trustworthy.  The differences presented between the CRL Distribution and the OCPS provided the opportunity to focus on the revocation and the OCSP response.
The PKI system behavior being investigated this week is the performance of an OCSP real-time status. 

---

## Environment
- Operating System: In practice, the overall lab environment will stem from the Windows 11 operating system. In practice, the overall lab environment will be based on the Windows 11 operating system.
- Terminal Used: PowerShell with OpenSSL embedded
- OpenSSL Version: OpenSSL 3.6.1 27 Jan 2026 (Library: OpenSSL 3.6.1 27 Jan 2026):

---

## Steps Performed
Summarize the key steps you performed to complete the lab.
Do not copy the lab instructions — describe what you actually did.

The infrastructure of this lab involves an artifact directory and a live connection to evaluate a leaf certificate. Confirmation of the extraction was provided by the -noout command. 
A full chain was retrieved from the same live website for a complete investigation of all three blocks of certificates.
Close investigation of the last step reveals the CA with the typical request of a verification command to ensure its rightful presence.
4. The commands applied process an OCSP responder URL (informing you of what is current and functional as of today) and a CRL Distribution Point URL (allows for documented precision when monitoring revocation failures.).
5. Systematically, the process calls for a query of the OCSP to the extent of it being a responder, extraction for a direct interpretation, and comparing them maximizes validity of a continued connection.   

---
 
## Results
Include the important outputs or findings from the lab.

- What was the Subject and Issuer of the leaf certificate?
The subject (CN=github.com) and issuer (C = G B ,   O = S e c t i g o   L i m i t e d ,   C N = S e c t i g o   P u b l i c   S e r v e r   A u t h e n t i c a t i o n   C A   D V   E 3 6)
- What OCSP URL did you find in the Authority Information Access extension?
Sectigo published the OCSP URL as http://ocsp.sectigo.com. 


- What CRL Distribution Point URL did you find?
The CRL Distribution Point URL points to http://crl.sectigo.com.

- What was the OCSP response status for the certificate?
Response was verified as ok and the leaf certificate responded as good.

- What do "This Update" and "Next Update" tell you?
It tells me the OSCP has been received and signed. The Next update signals the expiration date.

---

## Key Findings
Learning the TLS certificate is like a digital ID card, and seeing the CRl and OCSP at work to validate the certificate stood out the most.
Noticing the certificate chain embedded in the certificate header and pulling the browser to validate is what made the lab valuable.
Verifying the OCSP to make sure the certificate is not revoked and trustworthy.

---

## Explanation
Explain why the results matter.

- Why does an OCSP query require both the leaf certificate and the issuer certificate?
The protocol requires the subject and issuer to determine identity. It must also provide the public key throughout ongoing transactions. NIST SP 80-52 requires the leaf and issuer to identify themselves and maintain the hash needed to pass the chain of authentication.

- What is the difference between OCSP and CRL in practice?
OCSP provides up-to-the-minute updates of a cert, and when regulated (FFIEC, PCI SSC, and eIDAS) is considered useful when available. OCSP can also expose operational risks when soft-fails happen.

On the other hand, a CRL update is delayed (by 24-72 hours) compared to OCSP up-to-the-minute updates. Exporting the entire list is imperative to service all requirements, including legacy and air gapped devices.   

- What would happen if a system trusted a revoked certificate because OCSP was unavailable?
A few things come into play when fines are inevitable. Auditors will seek out overlooked fallback and fail-safe policies, an outage, and exposure for hackers to clone and gain system access, until it is revoked.
---

## Challenges / Troubleshooting
The openssl command produced outputs using “”, and not echo, for better results..

---

## Artifacts

- leaf_cert.pem
- issuer_cert.pem
- ocsp_response.txt
