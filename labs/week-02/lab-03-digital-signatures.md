

Lab 3 — Digital Signatures (Integrity + Authenticity)

##Overview
In strict PKI and secure API environments, this lab identifies how digital signatures are the backbone to deliver security based on integrity and authentication.  

##Environment
The environment allowing this implementation is on a Windows x64 computer. 
Operating System: In practice, the overall lab environment will be based on Windows 11. 
Terminal Used: PowerShell with OpenSSL embedded PowerShell with OpenSSL embedded.
OpenSSL Version - OpenSSL 3.6.1 27 Jan 2026 (Library: OpenSSL 3.6.1 27 Jan 2026)


##Results
Findings from the command (openssl genpkey -algorithm RSA…) produced a private_key.pem output. Extracting the public key from the leaf certificate (openssl pkey…), signing the file with an AES-sha256, and watching the validation loop close in real time with a verification OK.
The results of the outputs can be found in Week-02/assets/submissions:
artifact.sig
artifact.txt
private_key.pem
public_key.pem


##Example
The discovery made is that the actual digital signature bytes produced by the private key tell verifiers how to check the signature and to verify that it has not been modified.

##Explanation
The lab displays the need for both hashing and asymmetric cryptography since digital signatures demand a resilient verification.

##Examples
In a real-world, strict-PKI context, the three blocks involved in the certificate chain revolve around the leaf (carries the public key), the intermediate certificate (safety layers so the root can stay offline), and the root certificate, which is trusted automatically. If the root were ever compromised, it would undermine the entire hierarchy.

##Challenges / Troubleshooting
No issues were encountered during the lab. 

##Artifacts
artifact.sig
artifact.txt
private_key.pem
public_key.pem
