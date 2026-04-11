Week 2 Lesson Notes —Cryptography Fundamentals (Just Enough)

1. Core Concept
Performance and capacity of cryptography stand upon the columns of Confidentiality, Integrity, and Authenticity. Strict PKI environments constantly utilize HTTPS as they enforce hard-fail policies and their assigned certificate manager. Code signing comes in the form of HSMs’ retrieval of dedicated signatures. For particular business enterprises, certificate validation comes in the form of reverse proxies and policy-driven trust stores. Distribution of secure API communication meets zero- trust mandates (NIST SP 800-207) and PSD2 for financial APIs. Enterprise PKI system integrates an established application of governance, operations, and compliance that relatively aligns with the amount of data moving across the enterprise estate.

2. Why It Matters
In situations where enterprise environments demand confidentiality, data encryption during transit. Key management performs at high speeds and requires a large amount of storage as it defines distorted files, proof of identity from every certificate, and has the ability to maintain updates without disrupting the system.

Operational PKI polices hierarchy must not involve the risk of operating without cryptography. This would easily enable someone to impersonate a server, while the data in transit and at rest would be compromised. If such destructive measures hack risk management controls, the notification system would remain blind to viruses attacking the system.    


3. Technical Breakdown
Definition
Components
Flow
Trust implications

A Symmetric Encryption (Confidentiality) is known for sharing a private key known to encrypt and decrypt messages.
Thales uses symmetric encryption components as long-term private keys wrapped in AES-KW, or AES-GCM, during export or import of keys.  
The flow of this tool is found in PHI regulatory protocols, as it encrypts itself on a disk.
The trust implication is non-negotiable regarding a key never being exposed because to do so is to destroy trust and confidentiality within the system, clients, investors, and all stakeholders involved.  

The integrity of the key is known as hashing since it is a mathematical function producing a fixed-length non-replicable forensic data profile.  
Enterprises utilize the components of hashing by blocking rogue CA when certificates are being established in their systems. SHA-256 or SHA-384 protects environments from a man-in-the-middle attack after keys are exchanged.
The flow of such a tool is evident in how data is processed through OCSP and CRL records, log integrity, and key wrapping.
Trust implications are very high with hashing because it exposes tampering and can set off an alarm once auditors detect tampering.
Hashing performed correctly attests to the enterprise knowing it is irreversible, and it satisfies NIST and PCI DSS credential protection. Cloud HSMs (including SHA-256) are found to be less expensive than asymmetric while still binding data to a key or signature.

Digital Signatures are knwo to be a mechanism that proves integrity and identity to integrity and authenticity. 
Common components established in an enterprise environment are private keys, public keys, and hashing.
The most typical implementation of a digital signature is found in the hashing of data, which is encrypted with a private key, the signature is attached to the data, and the public key verifies the signature.
Trust implications are found in the outcome of the signature once decrypted. If it fails, then it is based upon a wrong cert, a misconfigured chain, tampered data, or a man-in-the-middle.


4. Common Misconceptions
First, misconceptions heard in boardrooms rest upon the fact that encryption accounts for compliance. It is incorrect because NIST and PCI Security Standards Council require documentation of key management aligned with audit trails. Auditors want to know how keys are generated, stored, rotated, and revoked. 
Another boardroom misconception is that hashing and encryption are interchangeable. Hashing scans of integrity (data and key alignments) and encryption demands confidentiality (i.e., PII).
An up-and-coming misconception relies heavily on ignoring best practices (i.e., crypto-agile tooling) to prepare for PQC and ongoing regulations. 


Where This Shows Up
Strict PKI environments will see digital signatures as it relates to HTTPS, TLS Sessions, trust points for internal certificates, efficient API authentication, and hashing as it seeks out verification from container images.

Web security
Strict PKI environments trust models resembles certs valide for less than 90 days, while ensuring a hard-fail revocation.

Internal enterprise systems
Operate in an internal CA hierarchy with short-lived leaf certs and NIST 800-57 rotation schedules. 

Cloud environments
Cloud HSM provides hardware-backed keys and a cloud root CA to on-premises root (X.509 cross-sign).

DevOps workflows
In DevOps, it is necessary to utilize HSM-protected signing keys with automatic revocation or key rollover that are triggered automatically. Administratively code signing incorporates code signing to ensure authenticity. It determines hash verification in container images, but another workflow involves Git as it uses hashing for commit integrity.

Mental Model.
The relationship used to establish trust within a strict PKI environment is scaled to demonstrate encryption as it protects data, hashing for direct integrity protection, and the system-intensive approach of assuring digital signatures are set to protect identity and integrity. The trust model for these environments rests on the verification of identity, the enforcement of trust, and the automated advantage of verification.
