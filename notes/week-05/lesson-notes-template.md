Week 5 Lesson Notes —Certificate Lifecycle Management

1. Core Concept
The concept for this week involves OCSP, CSR, and CRL maintenance. 

2. Why It Matters
In a FinTech enterprise environment, the regulatory expectation of PCI DSS v4.0, FFIEC CAT (Domain 4.B), EBA Guidelines, and the Cryptographic policy (ISO 27001 A.10.1). Implementing OCSP and CRL simultaneously monitors failures, regulatory defensibility, and operational resilience. 


3. Technical Breakdown
Components

Certificate Signing Request (CSR)
CRL Distribution Point
Certificate's revocation status using OCSP

4. Common Misconceptions
Misconception 1- The CA generates my private key when it issues the certificate.
Misconception 2- Renewal and replacement are the same; either one fixes expiration.


5. Where This Shows Up
Web security
Strict PKI fails when teams treat certificates as “files” instead of “governed identities” with lifecycle controls (renewal vs replacement decision).
