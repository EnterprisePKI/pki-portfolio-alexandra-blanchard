Lab 1 — Symmetric Encryption (Confidentiality)

##Overview
In regulated environments, operational understanding of encryption and decryption of files verifies production to ensure the same trust anchors exist. Testing for checks in the same network path and TLS layers.

##Environment
The environment allowing this implementation is on a Windows x64 computer. 
Operating System: In practice, the overall lab environment will stem from the Windows 11 operating system. 
Terminal Used: PowerShell with OpenSSL embedded PowerShell with OpenSSL embedded.
OpenSSL Version - OpenSSL 3.6.1 27 Jan 2026 (Library: OpenSSL 3.6.1 27 Jan 2026)

##Results
Use of the AES-256 encryption verifies the integrity of the decrypted files. If the wrong password is used, an error message flags this issue requiring debugging to remediate 
using OpenSSL outputs and troubleshooting techniques.


##Examples
Encrypted tokens and sessions discovered in public keys increase security. When private keys are kept in an HSM, it removes the opportunities for leaks.
The validation result indicated OK from the outcome. Encryption is only as trustworthy when the certificate advertises the public key. 


##Any unexpected behavior or results
The output results are aligned with a PKI-secure data transaction.
 

##Examples
A specific field is required to determine the OpenSSL commands path and outcome by creating a workflow that will deliver the assigned output based on the end od the command (i.e., openssl enc -aes-256-cbc -salt -pbkdf2
-in labs/02-week-02-cryptography-fundamentals/submissions/encrypted/plaintext.txt
-out labs/02-week-02-cryptography-fundamentals/submissions/encrypted/plaintext.txt.enc).

Validation succeeded because the symmetric session key was negotiated after the handshake.
In a real-world PKI context, enterprises use certificates anytime a machine or user requires proof of who they are. This connects to the week's learning outcomes because of the necessity of strict PKI environments requiring web security to users using the internet and intranet on their behalf. The device, or services account, must follow group-policy rules, stores, and verify keys before traffic is accepted.


##Challenges / Troubleshooting
The output results are aligned with a PKI-secure data transaction.
