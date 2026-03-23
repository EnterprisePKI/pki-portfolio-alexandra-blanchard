
# Lab 01 — Inspect X.509 Certificate Fields

## Overview
To authenticate Google's certificates, I first analyzed the first block of this certificate, known as the leaf certificate. 

This lab focused on generating architectural keys using OpenSSL.  
The goal is to break down a certification generation and identify the version, 
serial number, signature algorithm, Issuer, Subject, Not Before, Not After, and Public Key Algorithm. 
---

## Environment
- OS: The environment allowing this implementation is on a Windows 11 (x64) computer. 
- Terminal used (Mac Terminal / Git Bash / WSL): PowerShell with OpenSSL embedded
- OpenSSL version:
OpenSSL Version - OpenSSL 3.6.1 27 Jan 2026 (Library: OpenSSL 3.6.1 27 Jan 2026)

---

## Certificate Fields

| Field                | Value from your output |
|----------------------|------------------------|
| Version              |     3                  |
| Serial Number        |                        |
| Signature Algorithm  |sha256WithRSAEncryption |
| Issuer               |Google Trust Services LLC|
| Subject              |google.com              |
| Not Before           |Feb 23 18:19:44 2026 GMT|
| Not After            |May 18 18:19:43 2026 GMT|
| Public Key Algorithm |EC, (prime256v1)        |

---

## Observations

1. Who issued the certificate?
2. What domain or organization does it represent?
3. When does it expire?
4. What public key algorithm is used?
5. Why does the Issuer field matter in a PKI system?



---

## Observations

1. Who issued the certificate? After a few tries [verify error:num=20:unable to get local issuer certificate
verify return:1
depth=1 C=US, O=Google Trust Services, CN=WR2
verify return:1
depth=0 CN=*.google.com
verify return:1] Google Trust Services issued the certificate to google.com.
2. What domain or organization does it represent? The entity represented is Google.com.
3. When does it expire? The certificate expires on May 18 18:19:43 2026 GMT.
4. What public key algorithm is used? The public key algorithm is not in its usual format; however, in this instance, it is presented as: PKEY: EC, (prime256v1).
5. Why does the Issuer field matter in a PKI system?  The issuer field matters because it identifies the CA verifying the digital signature.
6. Why is a specific field or extension required?  The specific is required because -connect is required to connect to the website, and -showcerts is required to fulfill the demand of retrieving all of the certificates tied to that website.
7. Why does a validation succeed or fail? Everything worked in this instance.
8. What does the result mean in a real-world PKI context? In Fintech, authentication and verified identity of every entity is imperative to keeping finances safe from virtual intruders.
9. How does this connect to the week's learning outcomes? The main goal of this week's learning outcomes is structured around the structure of digital certificates. We identify the key components of certificates to increase the ability to monitor and respond diligently to certificate-related expirations, incidents, and vulnerabilities. 


Challenges / Troubleshooting:
Although this lab did not require troubleshooting, it did permit instances to implement the ability to build strong attention to detail with the ability to identify inconsistencies and potential issues if they were to arise with an Issuer/CA, subject, and/or entity.
**
