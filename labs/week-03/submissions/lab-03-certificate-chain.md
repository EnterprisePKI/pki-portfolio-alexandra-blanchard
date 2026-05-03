# Lab 03 — Verify a Certificate Chain

## Overview
Strict PKI ensures encryption happens with the correct identity (i.e., chain) and not an imposter. Continuity in secure Public Key Infrastructures are found in OpenSSL commands line when seeking to see the whole chain (-show_chain -verbose or openssl s_client -connect). Lab 3 creates a chain assembly workflow to thoroughly inspect each certificate block reliably and validate it.

---

## Environment
The environment allowing this implementation is on a Windows x64 computer. 
Operating System: In practice, the overall lab environment will be based on Windows 11. 
Terminal Used: PowerShell with OpenSSL embedded PowerShell with OpenSSL embedded
OpenSSL Version - OpenSSL 3.6.1 27 Jan 2026 (Library: OpenSSL 3.6.1 27 Jan 2026)

---

## Chain Verification Result
server.pem: OK
Chain:
depth=0: CN = github.com (untrusted)
depth=1: CN = Sectigo Public Server Authentication CA DV E36 (untrusted)
depth=2: CN = Sectigo Public Server Authentication Root E46 (trusted)
---

## Certificate Roles

| Certificate  | Role                        | Key Indicator                    |
|--------------|-----------------------------|----------------------------------|
| root.pem     |CA:TRUE — Issuer = Subject (self-signed)   |CN=USERTrust ECC Certification Authority|
| intermediate.pem |CA:TRUE — Issuer points to Root CA     |CN=Sectigo Public Server Authentication Root E46|
| server.pem   |CA:FALSE — Issuer points to Intermediate CA|CN=github.com|

---

## Observations

1. Did the chain verify successfully? What did the output say?
Verification of the server.pem signing the intermediate.pem and it being signed by the root.pem accepts the chain successfully with an output of OK.

2. How did you identify the root CA? 
The command line [openssl x509 -in root.pem -noout -subject -issuer -dates] produced an output of: 
subject=C=GB, O=Sectigo Limited, CN=Sectigo Public Server Authentication Root E46
issuer=C=US, ST=New Jersey, L=Jersey City, O=The USERTRUST Network, CN=USERTrust ECC Certification Authority
notBefore=Mar 22 00:00:00 2021 GMT
notAfter=Jan 18 23:59:59 2038 GMT

CN=USERTrust ECC Certification Authority is what identifies the block cert of a root. Another way to identify a root cert is the validity period having the longest window. 

3. How did you identify the intermediate CA?
The command line [openssl x509 -in intermediate.pem -noout -subject -issuer -dates] produced an output of:
subject=C=GB, O=Sectigo Limited, CN=Sectigo Public Server Authentication CA DV E36                  
issuer=C=GB, O=Sectigo Limited, CN=Sectigo Public Server Authentication Root E46
notBefore=Mar 22 00:00:00 2021 GMT
notAfter=Mar 21 23:59:59 2036 GMT

An intermediate cert is identified by the subject matching the leaf cert. The issuer points to the root (CN=Sectigo Public Server Authentication Root E46) and the validity is longer than the leaf cert.

4. What field confirms whether a certificate can issue other certificates?
When Basic Constraints produce an out of CA: True it signifies that this sert is allowed to issue leaf certs.

5. Why does removing the intermediate certificate break the chain?
Removing an intermediate certificate breaks the chain because it is the bridge between matching the leaf's Issuer (subject), while pointing to the root (Issuer). 
