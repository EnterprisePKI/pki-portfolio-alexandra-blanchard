
Lab 02 — Diagnose a Broken Certificate Chain
Week 6 · PKI Incident Diagnosis & Troubleshooting CVI PKI Career Pathway — Phase 1 Foundations

Incident Summary
Target system: Radiology imaging platform (simulated via incomplete-chain.badssl.com) Diagnosed by: Alex B. 
Date of diagnosis: 4/13/26

What failed:
Certificate expired because the After dates are in the past (NotAfter: Apr 12 23:59:59 2015 GMT, NotAfter: Feb 11 23:59:59 2029 GMT, and NotAfter: May 30 10:48:38 2020 GMT).

Evidence
The X.509 identified the failure of the TLS handshake as follows:
SSL handshake has read 5003 bytes and written 1675 bytes
Verification error: certificate has expired

Once connected to:
104.154.89.105
CONNECTED(000001FC)
depth=2 C=GB, ST=Greater Manchester, L=Salford, O=COMODO CA Limited, CN=COMODO RSA Certification Authority
verify error:num=20:unable to get local issuer certificate
verify return:1
depth=1 C=GB, ST=Greater Manchester, L=Salford, O=COMODO CA Limited, CN=COMODO RSA Domain Validation Secure Server CA
verify return:1
depth=0 OU=Domain Control Validated, OU=PositiveSSL Wildcard, CN=*.badssl.com
Verify error:num=10:certificate has expired
notAfter=Apr 12 23:59:59 2015 GMT
verify return:1
depth=0 OU=Domain Control Validated, OU=PositiveSSL Wildcard, CN=*.badssl.com
notAfter=Apr 12 23:59:59 2015 GMT
verify return:1

Error num 20 was addressed in the following output, and error num 10 output was solidified twice by the output notAfter=Apr 12 23:59:59 2015 GMT.

Why it failed
The reason behind the certificate failure is the certification expiration. The leaf certificate and the issuer certificate have expired and cannot be considered as certificates to renew, but they are certificates requiring replacement.

Chain status
The full chain provided the leaf cert, the intermediate cert, and the root cert. 

Remediation path
Restoring the system requires replacing the expired certificate. 
The workflow for this procedure is as follows:
Create a new private key
Create a new CSR with the new key
Issue a replacement certificate
Confirm the validity of the certificate
Confirm the NotBefore and NotAfter dates as well

Prevention
Strict PKI environments must have layer failsafes to prevent such outages from occurring. A continuous feed of PKI system scanning, alerting the owner of each cert when to renew. Automated renewal and revocation practices, using cert managers, have a higher chance of eliminating cert outages.  Quarterly risk management rollouts of table-top exercises of cert revocation and renewal lessen the stresses on a PKI team if, or when, an outage occurs. Naturally, internal auditing against NIST and PIC SSC standards creates resilience and routine for a strict PKI environment.

Diagnostic Steps
Document each step of the PKI Diagnostic Framework as you worked through it.

Step 1 — Retrieve
Command used:

'' | openssl s_client -connect expired.badssl.com:443 -servername expired.badssl.com -showcerts 2>$null | openssl x509 -outform PEM | Set-Content expired_cert.pem


What you observed:
The leaf of the certificate is saved in a PEM file.
       
   
Step 2 — Parse
Command used:

openssl x509 -in expired_cert.pem -text -noout

Key fields from the certificate:

Field	Value
Subject CN	*.badssl.com 	
Issuer	CN=COMODO RSA Domain Validation Secure Server CA
Not Before	9 April 2015
Not After	12 April 2015
SAN entries	DNS:**.badssl.com and .badssl.com 	

What you found:

PKI trust depends on a working certificate not an expired one. The signature is invalid because of the validity window being closed, whci make is crytptographically invalid. The chain of trust is present, but again the cert lack validity. An operational impact (involving FFIEC, PCI DSS) would flag auditors as an enterprise having weak key-management controls. In a strict PKI environment, continuous maintenance includes layering renewal automation, cross-checking CRL inventory, and monitoring hard-fail revocations to prevent outages and stay compliant.

Parsing the certificate presented

Step 3 — Validate the Chain
Command used:

openssl s_client -connect expired.badssl.com:443 -showcerts

Result:

The chain is broken with error num=10 being the cause. 

What you found:

This step confirmed the cert was out of it validity period.
depth=0 OU=Domain Control Validated, OU=PositiveSSL Wildcard, CN=*.badssl.com
Verify error:num=10:certificate has expired
notAfter=Apr 12 23:59:59 2015 GMT
verify return:1
depth=0 OU=Domain Control Validated, OU=PositiveSSL Wildcard, CN=*.badssl.com
notAfter=Apr 12 23:59:59 2015 GMT
verify return:1


Step 4 — Check Revocation and Trust
Command used:

openssl x509 -in expired_cert.pem -noout -text | Select-String -Pattern 'OCSP' -Context 0,1
What you found:

The OCSP URL presented OCSP - URI:http://ocsp.comodoca.com .

Reflection
This lab reinforced that the NotAfter date will trigger immediate outages is layered reinforcements are not in place. This lab illustrates how imperative time-based validity is for preventing PKI from breaking the entire TLS trust path. 
