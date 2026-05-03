
Lab 2 — Hashing & Integrity

##Overview
At the enterprise level, the PKI concept being investigated uses SHA-256 to generate certificate fingerprints.

##Environment
The environment allowing this implementation is on a Windows x64 computer. 
Operating System: In practice, the overall lab environment will be based on Windows 11. 
Terminal Used: PowerShell with OpenSSL embedded PowerShell with OpenSSL embedded.
OpenSSL Version - OpenSSL 3.6.1 27 Jan 2026 (Library: OpenSSL 3.6.1 27 Jan 2026)


##Results
Findings from the lab produced hash signatures (message.txt). Once the command (echo” tampered”) the output changes the hash output.

Result examples can be found in Week-02/assets/submissions:
message.sha256.tx	
message.txt
message_tampered.sha256.txt


##Examples
The discovery made is the outcome of the command openssl dgst -sha256, and the digital signature outcome of generating a new hash.


##Explanation
Handshake transcripts matter because it prevents man-in-the-middle-attacks. Alerting the system of tampering after a key exchange.

##Examples:
In a real-world, strict-PKI context, hash pairs guarantee the OK verification as it stems from only one certificate. This lab example displays a snippet of how hashing keys are "tampered" with, and how they are detected by auditors.

##Challenges / Troubleshooting
No issues were encountered during the lab. 

##Artifacts
message.sha256.tx	
message.txt
message_tampered.sha256.txt
