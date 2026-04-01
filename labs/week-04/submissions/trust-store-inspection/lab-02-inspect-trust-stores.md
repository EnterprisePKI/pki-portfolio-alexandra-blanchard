

# Lab 02 — Inspect Your Trust Store

## Overview
Certification practice proceeded by corresponding with the certification manager within Windows. 

---

## Environment
- Operating System: Win 11
- Terminal Used: OpenSSL (Embedded in PowerShell)
- OpenSSL Version: OpenSSL 3.6.1 27 Jan 2026 (Library: OpenSSL 3.6.1 27 Jan 2026)

---

## Steps Performed

1. I began the process of locating the trust store in my OS by first creating the directory [certmgr.msc].
2. I then proceeded to locate the number of root certificates in my certificate manager. 
3. Found ISRG Root X1
Subject: CN = ISRG Root X1
O = Internet Security Research Group
C = US
Issuer: CN = ISRG Root X1
O = Internet Security Research Group
C = US
Valid From [‎Thursday, ‎June ‎4, ‎2015 4:04:38 AM] / Valid To [‎Monday, ‎June ‎4, ‎2035 4:04:38 AM]
Public key algorithm
[30 82 02 0a 02 82 02 01 00 ad e8 24 73 f4 14 37 f3 9b 9e 2b 57 28 1c 87 be dc b7 df 38 90 8c 6e 3c e6 57 a0 78 f7 75 c2 a2 fe f5 6a 6e f6 00 4f 28 db de 68 86 6c 44 93 b6 b1 63 fd 14 12 6b bf 1f d2 ea 31 9b 21 7e d1 33 3c ba 48 f5 dd 79 df b3 b8 ff 12 f1 21 9a 4b c1 8a 86 71 69 4a 66 66 6c 8f 7e 3c 70 bf ad 29 22 06 f3 e4 c0 e6 80 ae e2 4b 8f b7 99 7e 94 03 9f d3 47 97 7c 99 48 23 53 e8 38 ae 4f 0a 6f 83 2e d1 49 57 8c 80 74 b6 da 2f d0 38 8d 7b 03 70 21 1b 75 f2 30 3c fa 8f ae dd da 63 ab eb 16 4f c2 8e 11 4b 7e cf 0b e8 ff b5 77 2e f4 b2 7b 4a e0 4c 12 25 0c 70 8d 03 29 a0 e1 53 24 ec 13 d9 ee 19 bf 10 b3 4a 8c 3f 89 a3 61 51 de ac 87 07 94 f4 63 71 ec 2e e2 6f 5b 98 81 e1 89 5c 34 79 6c 76 ef 3b 90 62 79 e6 db a4 9a 2f 26 c5 d0 10 e1 0e de d9 10 8e 16 fb b7 f7 a8 f7 c7 e5 02 07 98 8f 36 08 95 e7 e2 37 96 0d 36 75 9e fb 0e 72 b1 1d 9b bc 03 f9 49 05 d8 81 dd 05 b4 2a d6 41 e9 ac 01 76 95 0a 0f d8 df d5 bd 12 1f 35 2f 28 17 6c d2 98 c1 a8 09 64 77 6e 47 37 ba ce ac 59 5e 68 9d 7f 72 d6 89 c5 06 41 29 3e 59 3e dd 26 f5 24 c9 11 a7 5a a3 4c 40 1f 46 a1 99 b5 a7 3a 51 6e 86 3b 9e 7d 72 a7 12 05 78 59 ed 3e 51 78 15 0b 03 8f 8d d0 2f 05 b2 3e 7b 4a 1c 4b 73 05 12 fc c6 ea e0 50 13 7c 43 93 74 b3 ca 74 e7 8e 1f 01 08 d0 30 d4 5b 71 36 b4 07 ba c1 30 30 5c 48 b7 82 3b 98 a6 7d 60 8a a2 a3 29 82 cc ba bd 83 04 1b a2 83 03 41 a1 d6 05 f1 1b c2 b6 f0 a8 7c 86 3b 46 a8 48 2a 88 dc 76 9a 76 bf 1f 6a a5 3d 19 8f eb 38 f3 64 de c8 2b 0d 0a 28 ff f7 db e2 15 42 d4 22 d0 27 5d e1 79 fe 18 e7 70 88 ad 4e e6 d9 8b 3a c6 dd 27 51 6e ff bc 64 f5 33 43 4f 02 03 01 00 01]
4. Lastly, the Common Names were listed from a command [certutil -store Root | Select-String "CN="], which was verified by inputting [openssl s_client -connect google.com:443 -verify_return_error] with a verification return code of 0 (ok).

---

## Results
Command: certutil -store Root | Select-String "CN="

Output: 

Issuer: CN=Microsoft Root Certificate Authority, DC=microsoft, DC=com
Subject: CN=Microsoft Root Certificate Authority, DC=microsoft, DC=com
Issuer: CN=Thawte Timestamping CA, OU=Thawte Certification, O=Thawte, L=Durbanville, S=Western Cape, C=ZA
Subject: CN=Thawte Timestamping CA, OU=Thawte Certification, O=Thawte, L=Durbanville, S=Western Cape, C=ZA
Issuer: CN=Microsoft Root Authority, OU=Microsoft Corporation, OU=Copyright (c) 1997 Microsoft Corp.
Subject: CN=Microsoft Root Authority, OU=Microsoft Corporation, OU=Copyright (c) 1997 Microsoft Corp.
Issuer: CN=Symantec Enterprise Mobile Root for Microsoft, O=Symantec Corporation, C=US
Subject: CN=Symantec Enterprise Mobile Root for Microsoft, O=Symantec Corporation, C=US
Issuer: CN=Microsoft Root Certificate Authority 2011, O=Microsoft Corporation, L=Redmond, S=Washington, C=US
Subject: CN=Microsoft Root Certificate Authority 2011, O=Microsoft Corporation, L=Redmond, S=Washington, C=US
Issuer: CN=Microsoft Authenticode(tm) Root Authority, O=MSFT, C=US
Subject: CN=Microsoft Authenticode(tm) Root Authority, O=MSFT, C=US
Issuer: CN=Microsoft Root Certificate Authority 2010, O=Microsoft Corporation, L=Redmond, S=Washington, C=US
Subject: CN=Microsoft Root Certificate Authority 2010, O=Microsoft Corporation, L=Redmond, S=Washington, C=US
Issuer: CN=Microsoft ECC TS Root Certificate Authority 2018, O=Microsoft Corporation, L=Redmond, S=Washington, C=US
Subject: CN=Microsoft ECC TS Root Certificate Authority 2018, O=Microsoft Corporation, L=Redmond, S=Washington, C=US
Issuer: CN=Microsoft ECC Product Root Certificate Authority 2018, O=Microsoft Corporation, L=Redmond, S=Washington, C=US
Subject: CN=Microsoft ECC Product Root Certificate Authority 2018, O=Microsoft Corporation, L=Redmond, S=Washington, C=US
Issuer: CN=Microsoft Time Stamp Root Certificate Authority 2014, O=Microsoft Corporation, L=Redmond, S=Washington, C=US
Subject: CN=Microsoft Time Stamp Root Certificate Authority 2014, O=Microsoft Corporation, L=Redmond, S=Washington, C=US


- How many trusted root CAs did you find on your system?
The Win11 system currently has 49 root certifications. 

- The one specific root CA inspected is the following:
Found ISRG Root X1
Subject: CN = ISRG Root X1
O = Internet Security Research Group
C = US
Issuer: CN = ISRG Root X1
O = Internet Security Research Group
C = US
Valid From [‎Thursday, ‎June ‎4, ‎2015 4:04:38 AM] / Valid To [‎Monday, ‎June ‎4, ‎2035 4:04:38 AM]
Public key algorithm
[30 82 02 0a 02 82 02 01 00 ad e8 24 73 f4 14 37 f3 9b 9e 2b 57 28 1c 87 be dc b7 df 38 90 8c 6e 3c e6 57 a0 78 f7 75 c2 a2 fe f5 6a 6e f6 00 4f 28 db de 68 86 6c 44 93 b6 b1 63 fd 14 12 6b bf 1f d2 ea 31 9b 21 7e d1 33 3c ba 48 f5 dd 79 df b3 b8 ff 12 f1 21 9a 4b c1 8a 86 71 69 4a 66 66 6c 8f 7e 3c 70 bf ad 29 22 06 f3 e4 c0 e6 80 ae e2 4b 8f b7 99 7e 94 03 9f d3 47 97 7c 99 48 23 53 e8 38 ae 4f 0a 6f 83 2e d1 49 57 8c 80 74 b6 da 2f d0 38 8d 7b 03 70 21 1b 75 f2 30 3c fa 8f ae dd da 63 ab eb 16 4f c2 8e 11 4b 7e cf 0b e8 ff b5 77 2e f4 b2 7b 4a e0 4c 12 25 0c 70 8d 03 29 a0 e1 53 24 ec 13 d9 ee 19 bf 10 b3 4a 8c 3f 89 a3 61 51 de ac 87 07 94 f4 63 71 ec 2e e2 6f 5b 98 81 e1 89 5c 34 79 6c 76 ef 3b 90 62 79 e6 db a4 9a 2f 26 c5 d0 10 e1 0e de d9 10 8e 16 fb b7 f7 a8 f7 c7 e5 02 07 98 8f 36 08 95 e7 e2 37 96 0d 36 75 9e fb 0e 72 b1 1d 9b bc 03 f9 49 05 d8 81 dd 05 b4 2a d6 41 e9 ac 01 76 95 0a 0f d8 df d5 bd 12 1f 35 2f 28 17 6c d2 98 c1 a8 09 64 77 6e 47 37 ba ce ac 59 5e 68 9d 7f 72 d6 89 c5 06 41 29 3e 59 3e dd 26 f5 24 c9 11 a7 5a a3 4c 40 1f 46 a1 99 b5 a7 3a 51 6e 86 3b 9e 7d 72 a7 12 05 78 59 ed 3e 51 78 15 0b 03 8f 8d d0 2f 05 b2 3e 7b 4a 1c 4b 73 05 12 fc c6 ea e0 50 13 7c 43 93 74 b3 ca 74 e7 8e 1f 01 08 d0 30 d4 5b 71 36 b4 07 ba c1 30 30 5c 48 b7 82 3b 98 a6 7d 60 8a a2 a3 29 82 cc ba bd 83 04 1b a2 83 03 41 a1 d6 05 f1 1b c2 b6 f0 a8 7c 86 3b 46 a8 48 2a 88 dc 76 9a 76 bf 1f 6a a5 3d 19 8f eb 38 f3 64 de c8 2b 0d 0a 28 ff f7 db e2 15 42 d4 22 d0 27 5d e1 79 fe 18 e7 70 88 ad 4e e6 d9 8b 3a c6 dd 27 51 6e ff bc 64 f5 33 43 4f 02 03 01 00 01]


- What did the verify return code output tell you?
The verification code of 0 lets me know the https websites, maching-tomachine trust, code signing, and internal PKI validates the certification chain is secure and valid to be used.

---

## Key Findings
The key observations observed in this lab are listed as:
•no peer certificate available
•This TLS version forbids renegotiation.
•No ALPN negotiated.
rather than observations about the trust store itself. These are output lines from the s_client session — they are not the key findings of a trust store inspection lab. Replace these with observations about what you discovered: how many CAs are pre-installed, why root CAs are self-signed, and what it means that trust is automatically inherited from the trust store.

---

## Explanation
Explain why the results matter.

- Why does your browser trust a certificate from a website you have never visited before?
A certificate issued by the certificate authority was forwarded to DigiCert. This is why the chain was accepted.
 The correct answer is that the browser checks whether the server's certificate chains back to a root CA already installed in the system trust store — no forwarding involved. DigiCert is one of those trusted roots, not a relay.


- What would happen if an enterprise's internal root CA were NOT in the trust store?
The trust store would ensure that the PKI fails immediately and prevents it from proceeding.
The precise answer is: browsers and applications would show a security warning or refuse the connection because the certificate chain cannot be validated to a trusted root.

- What surprised you about how many roots are pre-installed on your system?
To see 49 root certs, let me know the roots installed are required for the safety of the system.
---

## Challenges / Troubleshooting
No challenges were present in this lab.

---

## Artifacts
No artifacts were created in this lab.


