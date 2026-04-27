# Lab 01 — Analyze a Live Enterprise Certificate Deployment

## Overview
Currently investigating the underlying design of a public-key infrastructure. Demonstrating the inspection of a certificate chain and a practical deployment in real-time.
Generating and inspecting TLS commands to engineer how they are applied in an enterprise environment.

---

## Environment
- Operating System: In practice, the overall lab environment will stem from the Windows 11 operating system.
- In practice, the overall lab environment will stem from the Windows 11 operating system.
- Terminal Used: PowerShell with OpenSSL embedded
- OpenSSL Version: OpenSSL 3.6.1 27 Jan 2026 (Library: OpenSSL 3.6.1 27 Jan 2026)

---

## Steps Performed
1. The basic architecture of a PKI system begins with connecting to the live endpoint to capture the certificate.  
2. Comparing the capture against a full chain confirms a chain's output and if the connection is successful.
3. Once pulled, technical details such as validity, subject, SAN, and Issuers are recorded.  

---

## Results
Checking CDN related SAn entries produces these results.

X509v3 Subject Alternative Name: 
                  DNS:www.salesforce.com, DNS:c.salesforce.com
              X509v3 Certificate Policies: 
                  Policy: 2.23.140.1.2.2
                    CPS: http://www.digicert.com/CPS
              X509v3 Key Usage: critical
                  Digital Signature, Key Agreement
              X509v3 Extended Key Usage: 
                  TLS Web Server Authentication, TLS Web Client Authentication
              X509v3 CRL Distribution Points: 
                  Full Name:

TLS structure and deployment results produced renegotiation status and an error 20 (unable to get local issuer certificate). Understanding the outcome, what to look for, and the ls output listing the leaf_cert.pem as available (along with several troubleshooting efforts) the outcome did not work for me.


New, TLSv1.3, Cipher is TLS_AES_256_GCM_SHA384
Protocol: TLSv1.3
Server public key is 256 bit
This TLS version forbids renegotiation.
Compression: NONE
Expansion: NONE
No ALPN negotiated
Early data was not sent
Verify return code: 20 (unable to get local issuer certificate)
---
---
Post-Handshake New Session Ticket arrived:
SSL-Session:
    Protocol  : TLSv1.3
    Cipher    : TLS_AES_256_GCM_SHA384
    Session-ID: 024D17F74202214F35BC80AF743A0000210B1848B4A2FFAEABB2D5CE32812AC3
    Session-ID-ctx: 
    Resumption PSK: 57BB3AF13029393DBCFDAD67041D7CB2C2B4FCF157725853D714516CAF056695DD1A519D8E594C817A62E123896943ED
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 83100 (seconds)
    TLS session ticket:
    0000 - 00 00 f8 02 9a 6e ca 0d-ea 25 cd 69 e7 99 b6 8d   .....n...%.i....
    0010 - 92 2f 11 8d 0d 96 79 92-64 aa 6d c7 90 9c 55 30   ./....y.d.m...U0
    0020 - 69 38 cb 3c 4f a9 da 29-e1 3f 32 be 97 6d c7 93   i8.<O..).?2..m..
    0030 - d7 b8 9e aa 3b 62 68 c1-7f d7 5c d1 01 0a 8c fc   ....;bh...\.....
    0040 - 59 85 80 11 18 b5 ad d4-55 a3 44 98 8c de 3c 09   Y.......U.D...<.
    0050 - 85 18 fc 52 48 a8 02 6a-5a 81 03 3d 9b fd 1d d4   ...RH..jZ..=....
    0060 - 9d d2 e0 68 28 08 1d c7-89 31 ba 2d dd b6 11 a6   ...h(....1.-....
    0070 - 8e 55 5c 3a 16 bd 5c ca-c4 b7 c2 3a c4 f3 47 cb   .U\:..\....:..G.
    0080 - d8 7b 06 8a eb 99 98 d1-32 db ef 3b ca c6 22 16   .{......2..;..".
    0090 - 48 9c f6 37 ae d0 fa 01-86 e1 22 e6 0a 7d 06 fb   H..7......"..}..
    00a0 - ae bf cd 79 51 a0 e7 98-98 5f 20 60 7b 8f 17 31   ...yQ...._ `{..1
    00b0 - 4b 4f 20 05 46 8d 2f 6f-5a 1d 7c f8 76 85 23 e0   KO .F./oZ.|.v.#.
    00c0 - 3d d2 b5 c0 36 66 01 64-8f 87 ce 34 87 86 5d 57   =...6f.d...4..]W
    00d0 - 71 48 d6 cb b8 f6 ea 46-a9 fb 10 56 c2 de 76 72   qH.....F...V..vr
    00e0 - 0c bc ec 9b 68 df e2 0e-d0 b1 f5 24 6f 5c 9e 86   ....h......$o\..
    00f0 - 04 10 b5 fe e3 4f df 51-00 86 a0 59 ef a7 45 8d   .....O.Q...Y..E.

    Start Time: 1777005631
    Timeout  : 7200 (sec)
    Verify return code: 20 (unable to get local issuer certificate)
    Extended master secret: no
    Max Early Data: 0
---
read R BLOCK
---
Post-Handshake New Session Ticket arrived:
SSL-Session:
    Protocol : TLSv1.3
    Cipher   : TLS_AES_256_GCM_SHA384
    Session-ID: E3A1D6F12C2829BCFDF28EECE26D409D314D4DEE0973B5107FE3ED0B93734750
    Session-ID-ctx: 
    Resumption PSK: 8D872AF95FA92EB92E4A69AE9456E6E9596265FE627F6F5784883FA0127E0E5EE2EE952931A51CBB50F19CEB86B3DBBA
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 83100 (seconds)
    TLS session ticket:
    0000 - 00 00 f8 02 9a 6e ca 0d-ea 25 cd 69 e7 99 b6 8d   .....n...%.i....
    0010 - 30 91 42 a9 72 b8 35 dc-21 18 62 e1 9b b1 4f 28   0.B.r.5.!.b...O(
    0020 - 8d 6b 9b f3 32 e7 6e 96-36 dc 76 5c aa f6 26 37   .k..2.n.6.v\..&7
    0030 - 39 02 a4 13 dc 76 f8 e2-53 e1 eb 7f 42 55 d5 0a   9....v..S...BU..
    0040 - ee c7 87 34 c4 1f 1a ad-88 4e 2f 9d a5 d2 5d 92   ...4.....N/...].
    0050 - be 71 14 3b f6 06 26 fd-7a cb cf fc 09 07 39 93   .q.;..&.z.....9.
    0060 - d5 7f 25 13 cc 34 f4 e7-83 4f b7 7a 24 af 7e 8f   ..%..4...O.z$.~.
    0070 - 3c 5c bf 49 f3 15 fb 0f-71 f3 7c 10 d3 b7 d4 9b   <\.I....q.|.....
    0080 - 83 b7 6a 35 33 f1 31 36-f1 1f 2a 0f 00 b0 3f 92   ..j53.16..*...?.
    0090 - 96 e3 a9 e2 41 27 b3 29-30 1f 32 21 6b 9d ed d0   ....A'.)0.2!k...
    00a0 - 96 5b c0 d0 0f ee c9 7a-b2 c6 bb bf 61 5b ca 47   .[.....z....a[.G
    00b0 - 2e 24 8d f7 1e c6 dd 5d-2d 17 23 3d 16 02 0e 88   .$.....]-.#=....
    00c0 - 97 14 96 d6 51 9a 7f 5e-d2 81 06 2d 96 a2 91 33   ....Q..^...-...3
    00d0 - 75 c1 30 3b aa 70 ed 86-92 9e 8a b8 12 2d 01 c9   u.0;.p.......-..
    00e0 - d9 82 a5 aa 7d f3 ad be-ff e1 4c f0 41 82 e4 18   ....}.....L.A...
    00f0 - 3b 6f 1e ee f9 5f b3 fd-1c 5c 1e 85 fa f6 a0 13   ;o..._...\......

    Start Time: 1777005631
    Timeout  : 7200 (sec)
    Verify return code: 20 (unable to get local issuer certificate)
    Extended master secret: no
    Max Early Data: 0


Verification results for certificate transparency logs were unsuccessful when attempting to use https://crt.sh: the page displays 502 Bad Gateway. 
Nevertheless, I understand I would have been provided a list of certifications issued to this domain. Along with verification of recent CA’s, and their history.

---

## Key Findings
Verification results for certificate transparency logs were unsuccessful when attempting to use https://crt.sh the page displays 502 Bad Gateway. Nevertheless, I understand I would have been provided a list of certifications issued to this domain. Along with verification of recent CA’s and their history. 

Example:
In this lab, Salesforce.com  output is the following:
HTTP/1.1 200 OK
server: AkamaiGHost
via: 1.1 varnish, 1.1 varnish
x-cache: TCP_HIT from a23-45-67-89.deploy.akamaitechnologies.com (Akamai/10.4.3)
cf-ray: (not present – Cloudflare not in path)
x-amz-cf-pop: (lacks Amazon CloudFront, so it will not populate)
  

---

## Explanation
The results matter because cf-ray and x-amz-cf-pop will populate differently when crossing different regions and time zones. Since the server shows Akamai on the edge, it also identified the x-cache for Cloudflare as expired.

Examples:

- Why the issuer is important in PKI
- Why SAN is required for modern TLS validation
- Why the certificate chain validates successfully
- Why a misconfiguration would cause a failure

---

## Challenges / Troubleshooting
THe first challenge entailed the inputting  of the correct command line for OpenSSL to run. Restructuring each command to deliver proper output are the steps that were taken to complete the portion of the lab requiring an OpenSSL command line. Document any issues encountered during the lab and how you resolved them.

Examples:

This command error exposed mechanisms aimed to provide sufficient technical detail to produce the correct outcome; however you will notice the difference between the two commands and which terminal it addresses. 
I openssl x509 -in enterprise_cert.pem -noout -text | grep -A10 "Subject Alternative Name
*Linux above/Windows(OpenSSL) below
openssl x509 -in enterprise_cert.pem -noout -text |    Select-String -Pattern 'Subject Alternative Name' -Context 0,10

---

## Artifacts
- enterprise_cert.pem
- screenshots stored in assets/week-07/crt.sh.jpg
- screenshots stored in assets/SSL Labs Analysis.jpg

---
