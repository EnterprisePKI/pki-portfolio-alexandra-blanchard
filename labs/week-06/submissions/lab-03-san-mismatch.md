
Lab 03 -  Diagnose a Hostname and SAN Mismatch
Incident Summary
Target system: Staff scheduling portal (simulated via wrong.host.badssl.com) Diagnosed by: Alex Blanchard
Date of diagnosis:4/12/2026

What failed
openssl verify mismatch_cert.pem
CN=*.badssl.com
error 20 at 0 depth lookup: unable to get local issuer certificate
error mismatch_cert.pem: verification failed


Evidence
document the hostname accessed, the Subject CN, and the exact SAN entries from the certificate
 Subject: CN=*.badssl.com
X509v3 Subject Alternative Name:
DNS:*.badssl.com, DNS:badssl.com


Why it failed
The TLS error is proof of the local issuer cert being unavailable. Making the putput a chain/trust-anchor problem. In the real world, it may cause a deployment problem. A trusted root is not present to create a reliable chain of trust.

Chain status
The status had an error of 20 at 0 depth, making the certificate that issues/signed mismathc_cert.pem unable to build a chain of trust. 


Remediation path
To restore this failing system, the Browser and TLS must see staff. metrogeneral.org and scheduling.metrogenreal.org s seperat4e certificates. Even if the cname is using staff. to point to scheduling. The browser is still dependent on the TLS certificate and what it says. Each department would need its own TLS certificate and point directly to itself for it to work. CNAME cannot replace a secure and trusted full chain.

Prevention
Remaining  consistent with the TLS hostnames and making sure each department retain their separate identities. 

Diagnostic Steps
Document each step of the PKI Diagnostic Framework as you worked through it.

Step 1 — Retrieve
Command used:
| openssl s_client -connect wrong.host.badssl.com:443 `    -servername wrong.host.badssl.com -showcerts 2>$null |  openssl x509 -outform PEM |  Set-Content -Encoding ascii mismatch_cert.pem

What you observed:
Output:
  
  X509v3 Key Usage: critical
                Digital Signature, Key Encipherment
            X509v3 Extended Key Usage: 
                TLS Web Server Authentication
         X509v3 Basic Constraints: critical   
         Subject: CN=*.badssl.com
          
     


Step 2 — Parse
Command used:

openssl x509 -in mismatch_cert.pem -text -noout
Key fields from the certificate:

Signature Algorithm: sha256WithRSAEncryption
        Issuer: C=US, O=Let's Encrypt, CN=R13
        Validity
            Not Before: Mar 24 20:02:52 2026 GMT
            Not After : Jun 22 20:02:51 2026 GMT
      CA:FALSE
            X509v3 Subject Key Identifier: 
                02:BE:1E:8F:84:38:A9:1F:93:8E:F8:27:80:EA:E7:8D:EB:2B:70:E4
            X509v3 Authority Key Identifier: 
                E7:AB:9F:0F:2C:33:A0:53:D3:5E:4F:78:C8:B2:84:0E:3B:D6:92:33
            Authority Information Access: 
                CA Issuers - URI:http://r13.i.lencr.org/
            X509v3 Subject Alternative Name: 
                DNS:*.badssl.com, DNS:badssl.com
            X509v3 Certificate Policies: 
                Policy: 2.23.140.1.2.1
            X509v3 CRL Distribution Points: 
                Full Name:
                  URI:http://r13.c.lencr.org/64.crl

An OCSP is not listed in the leaf because the revocation path is CRL-based.

Step 3 — Validate the Chain
Command used:

 openssl verify mismatch_cert.pem


Result:

CN=*.badssl.com
error 20 at 0 depth lookup: unable to get local issuer certificate
error mismatch_cert.pem: verification failed


What you found:

Am intermediate CA is not provided to link the leaf to the root.

Step 4 — Check Revocation and Trust
Command used:

$txt | Select-String -Pattern 'CRL Distribution Points' -Context 0,12
openssl x509 -in mismatch_cert.pem -noout -ocsp_uri
$txt | Select-String -Pattern 'CRL Distribution Points' -Context 0,20


What you found:

This certificate publishes a CRL distribution point, not an OCSP. Meaning revocation can be valid by downloading the CA’s revocation list and confirming it against the leaf’s serial number.

Reflection
PKI is not made to align with any other system or request, but its own. No changes can be made to appease any part of an organization because of the strict policies and cryptographic fields that must adhere to the PKI check and balance process, policies, and procedures. TLS only reinfroces SAN’s information on a certificate, so changes can be made only by the creation of a new ce4rtifricate c an satisfy a change.  
