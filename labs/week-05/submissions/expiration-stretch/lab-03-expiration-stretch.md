

# Lab 03 — Simulate a Certificate Expiration Scenario

## Overview

Initially, the lab creates three certificates using OpenSSL commands. The system behavior being investigated is presented as a drill to show how short-lived certs operate, how an already-expired cert responds, and how a replacement certificate serves as an alternative to the expired one.
---

## Environment
- Operating System: In practice, the overall lab environment will stem from the Windows 11 operating system. In practice, the overall lab environment will stem from the Windows 11 operating system.
- Terminal Used: PowerShell with OpenSSL embedded
- OpenSSL Version: OpenSSL 3.6.1 27 Jan 2026 (Library: OpenSSL 3.6.1 27 Jan 2026)

---

## Steps Performed
1. The PKI identification process began by generating a test key and a CSR, which created a short validity window.
2. After reading the validity window, the certificate was determined as valid. Understanding the mechanism of key creation and validation is crucial during high-volume transactions. 
3. Simulating an expired certificate to address the operational business environment in real-time magnifies a list of dates by producing the windows of service through an OpenSSL command. 
4. Fundamentally, the workflow of replacing an expired cert requires a new private key, a new CSR with a new key,
5. In support of the workflow is the issuing of the replacement certificate and its validation.

---

## Results
- The `notBefore` and `notAfter` dates, for your short-lived certificate, look like:
    
The notBefore=Apr  9 19:45:32 2026 GMT
notAfter=Apr  9 19:45:32 2027 GMT

- The output stated as `openssl x509 -checkend` produced the following for each certificate:
  
The output protocol enabled “Certificate will not expire”.

- The error message stated that `openssl verify` returned the following output for the expired certificate:

OpenSSL verify produced the following message :
CN=shortlived.cvi.internal, O=CyberVisionaries Institute, C=US
error 18 at 0 depth lookup: self-signed certificate
CN=shortlived.cvi.internal, O=CyberVisionaries Institute, C=US
error 10 at 0 depth lookup: certificate has expired
error labs/week-05/submissions/expiration-stretch/test_cert_expired.pem: verification failed

The message allowed me to examine the leaf, the owner (short-lived.cvi.internal). Error 18 indicates the cert is self-signed; error 10 presents the certificate as expired; and verification failed.

- What changed in the replacement certificate compared to the expired one?
The replacement certificate retained an ok, provided a “notBefore and notAfter date of service, as well as an output stating the certificate will not expire.

---

## Key Findings
Document the most important observations from the lab.

The lab held a detailed engagement meeting to create a short-lived certificate.
Followed by an expired cert and a new key creation for the replacement cert.
•The combined results show the cert can’t be used for a secure TLS and is unable to operate within a chain of trust (to a trusted CA). 

---

## Explanation
Explain why the results matter.

- Why does certificate expiration still cause outages despite being 100% predictable?

Outages are still plausible if the lack of predictable renewals and regulatory evidence is not addressed by PCI DSS automated alerts. Another consequence of outages can stem from PKI engineers working manually, undiscoverable certs, and an overlooked short-lived certificate. 

- What is the difference between renewal and replacement, and when would you choose each?
- 
To renew a cert means the cert has not yet expired, and it has validity. Whereas, the replacement of a cert is required when certs are no longer valid and expired.

- How would you use `openssl x509 -checkend` in a real monitoring script?
- 
After pulling the notBefore and notAfter (openssl x509 -in labs/week-05/submissions/expiration-stretch/test_cert_replacement.pem -dates -noout), the next command to evaluate the maintenance of the cert is openssl x509 -in labs/week-05/submissions/expiration-stretch/test_cert_replacement.pem -checkend 0.

- What does "certificate inventory" mean, and why is it necessary at enterprise scale?
- 
A certificate inventory is mandatory on an enterprise scale. Although the CRL is a part of the inventory, automated systems and certified lifecycle management create reports  to root out missing and overlooked certs to avoid enterprise-wide outages.
---

## Challenges / Troubleshooting
The command to extract the cert request output (Openssl x509 -req -in  labs/week-05/submissions/expiration-stretch/test_csr.pem -signkey labs/week-05/submissions/expiration-stretch/test_key.pem -set_serial 0x02 -startdate 20230101000000Z -days 1 -out labs/week-05/submissions/expiration-stretch/test_cert_expired.pem); however, the working command (openssl x509 -req -in  labs/week-05/submissions/expiration-stretch/test_csr.pem -signkey labs/week-05/submissions/expiration-stretch/test_key.pem -set_serial 0x02 -days 0 -out labs/week-05/submissions/expiration-stretch/test_cert_expired.pem) zeroed out the days for it to produce (Certificate request self-signature ok
subject=CN=shortlived.cvi.internal, O=CyberVisionaries Institute, C=US) a successful output.

---

## Artifacts

- test_cert_short.pem
- test_cert_expired.pem
- test_cert_replacement.pem
