Week 3 Lesson Notes — X.509 Certificate Anatomy

##1. Core Concept
Inspecting the core fields of an X.509 certificate. Deep diving into the use and relevance, of each of each certificate extension.

##2. Why It Matters
In a real, strict-PKI enterprise environment, every certificate extension is a security risk if not handled correctly. A continuous chain of trust is profitable to an enterprise when avoiding hard-fails within an operational resilient playbook aligned with a certificate lifecycle management.

##3. Technical Breakdown
Components
Certificate Fields
Field
Value from your output
Subject
CN=github.com
Issuer
C=GB, O=Sectigo Limited, CN=Sectigo Public Server Authentication CA DV E36
Not Before
Mar 6 00:00:00 2026 GMT
Not After
Jun 3 23:59:59 2026 GMT
Public Key Algorithm
id-ecPublicKey
Subject Alternative Name
DNS:github.com, DNS:www.github.com
Key Usage
critical - Digital Signature
Extended Key Usage
TLS Web Server Authentication


Flow
Each layer depends on the integrity of the one before it: break any link and the whole trust chain will fail.


##4. Common Misconceptions
Misconception 1 - Certificates introduce the public key and operate in encrypting the keys, too.
Misconception 2 - PKI is made for browsers only and has nothing to do with e-mails, container images, and IoT devices.

##5. Where This Shows Up
Enterprises use certificates for the main job of identity and key distribution, while AES usually handles the majority of encryptions. Renewal failures can also break third-party integrations leading to companies operating outside of the compliance framework. These frameworks keep organizations under the umbrella of Identity + Trust + Verification through periodic key replacements to mitigate key compromise risk.
