# Lab 05 — Extract a Certificate from a Live Website

## Overview
The deep dive involved in this lab involves parsing a certificate, saving locally, and analyzing each field, it role, indicator, and use.

---

## Environment
The environment allowing this implementation is on a Windows x64 computer. 
Operating System: In practice, the overall lab environment will be based on Windows 11. 
Terminal Used: PowerShell with OpenSSL embedded PowerShell with OpenSSL embedded
OpenSSL Version - OpenSSL 3.6.1 27 Jan 2026 (Library: OpenSSL 3.6.1 27 Jan 2026)
- Website used: github.com

---

## Certificate Fields

| Field                    | Value from your output |
|--------------------------|------------------------|
| Subject                  | CN=github.com  |
| Issuer                   | C=GB, O=Sectigo Limited, CN=Sectigo Public Server Authentication CA DV E36                       |
| Not Before               | Mar  6 00:00:00 2026 GMT                       |
| Not After                |Jun  3 23:59:59 2026 GMT                        |
| Public Key Algorithm     |id-ecPublicKey                        |
| Subject Alternative Name | DNS:github.com, DNS:www.github.com                       |
| Key Usage                | critical -  Digital Signature
| Extended Key Usage       |  TLS Web Server Authentication |

---

## Observations

1. What organization does this certificate belong to?
This certification belongs to github.com.
2. Which Certificate Authority issued it?
Authority Information Access states the CA is issued as:
CA Issuers - URI:http://crt.sectigo.com/SectigoPublicServerAuthenticationCADVE36.crt

3. When does it expire?
The validity period ranges from:
Validity
            Not Before: Mar  6 00:00:00 2026 GMT
            Not After: Jun  3 23:59:59 2026 GMT
After Jun  3 23:59:59 2026 GMT, all secure continuous functions

4. What domains are listed in the SAN field?
The domains listed in the SAN’s field are DNS: github.com and DNS:www.github.com.

5. What is this certificate authorized to be used for?
X509v3 Key Usage: critical
                Digital Signature
X509v3 Extended Key Usage: 
                TLS Web Server Authentication
Both outputs state the certificate is authorized for a web server. Within the TLS the KU proves it controls the private key during the handshake. 
