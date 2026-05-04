# PKI Troubleshooting Runbook

--
## Lab 03 — Diagnose a Hostname and SAN Mismatch

Title: Certificate Input Structure not found

---

## Problem Statement

> The command expects to parse a certificate successfully. Instead, the output produced an error message.

---

## Environment

Tool(s) used:
openssl version
OpenSSL 3.6.1 27 Jan 2026 (Library: OpenSSL 3.6.1 27 Jan 2026)
And
VSCode

The PKI Diagnostic Framework is relevant to  Step 2 — Parse—Read the SAN and Subject fields — find the mismatch.

---

## Symptoms

-Command line [ openssl x509 mismatch_cert.pem -text -noout] did not provide the expected output [of Subject: C=..., ST=..., O=..., CN=...].  

- Could not find certificate from mismatch_cert.pem
- EC380000:error:1E08010C:DECODER routines:OSSL_DECODER_from_bio:unsupported:crypto\encode_decode\decoder_lib.c:104:No supported data to decode. Input structure: Certificate
- Cannot find path 'C:\Full\Path\To\mismatch_cert.pem' because it does not exist

---

## Diagnostic Steps

1. Get-ChildItem *.pem
Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----         4/14/2026   5:49 PM           2186 issuer_cert.pem
-a----         4/13/2026   9:46 PM           1806 leaf_cert.pem
-a----         4/20/2026  10:11 PM           3614 mismatch_cert.pem
-a----          3/7/2026   9:46 PM           3324 privkey.pem
-a----          3/8/2026   9:27 PM           1732 rsa_priv.pem
-a----          3/7/2026   9:57 PM            814 rsa_pub.pem

2. Verified the location agai nursing the ls command
3. Moved the platform from OpenSSL (within the Windows PowerShell) to VSCode.

---

## Resolution

The fix to the resolution of the command [openssl x509 -in mismatch_cert.pem -text -noout] produced an output of:

Certificate:
    Data:
        Version: 3 (0x2)
        Serial Number:
            05:31:b4:91:c9:1b:ef:4e:68:43:5b:23:08:42:f0:8b:dd:3f
        Signature Algorithm: sha256WithRSAEncryption
        Issuer: C=US, O=Let's Encrypt, CN=R13
        Validity
            Not Before: Mar 24 20:02:52 2026 GMT
            Not After : Jun 22 20:02:51 2026 GMT

---

## Prevention Note

> The best way to avoid these issues is to use the VSCode platform to pull files correctly. If this happens again, the platforms being used will be updated to ensure the full certificate can be read.

---

labs/week-06/submissions/lab-03-san-mismatch.md

---

*CVI PKI Career Pathway — Phase 1 Foundations*
