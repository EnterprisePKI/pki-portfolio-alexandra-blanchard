
# Lab 03 — Install a Certificate and Validate Trust (Stretch)

## Overview
Lab 03 is where I created a full certificate and trust validation. The system involved in creating, testing, and verifying the validity of a certificate will be displayed below.
---

## Environment
- Operating System: Win 11
- Terminal Used: OpenSSL (Embedded in PowerShell)
- OpenSSL Version: OpenSSL 3.6.1 27 Jan 2026 (Library: OpenSSL 3.6.1 27 Jan 2026)

---

## Steps Performed
1. The private key [openssl genrsa  -out labs/week-04/submissions/install-validate/test-root-ca.key  2048] and root CA [openssl req -new -x509  -key labs/week-04/submissions/install-validate/test-root-ca.key  -out labs/week-04/submissions/install-validate/test-root-ca.crt -days 30 \  -subj "/CN=CVI-Lab-Root-CA/O=CyberVisionaries Institute/C=US"]
2. Installed the Root CA into the trust store [Import-Certificate -FilePath "labs\week-04\submissions\install-validate\test-root-ca.crt"  -CertStoreLocation Cert:\LocalMachine\Root].
3. The key created [openssl genrsa -out labs/week-04/submissions/install-validate/test-signed.key 2048




openssl req -new \
  -key labs/week-04/submissions/install-validate/test-signed.key \
  -out labs/week-04/submissions/install-validate/test-signed.csr \
  -subj "/CN=test.cvi-lab.local/O=CyberVisionaries Institute/C=US" ] involved an output which created a .key and .csr file.   
4. The .csr was then signed by the test root CA [openssl x509 -req \
  -in labs/week-04/submissions/install-validate/test-signed.csr \
  -CA labs/week-04/submissions/install-validate/test-root-ca.crt \
  -CAkey labs/week-04/submissions/install-validate/test-root-ca.key \
  -CAcreateserial \
  -out labs/week-04/submissions/install-validate/test-signed.crt \
  -days 30].
5. Validation of the entire chain [openssl verify \
  -CAfile labs/week-04/submissions/install-validate/test-root-ca.crt \
  labs/week-04/submissions/install-validate/test-signed.crt] was certified by OK output [test-signed.crt: OK] defined by the system within the trust chain.

---

## Results
Once the certificate was complete, verification of the test-root-ca.crt populated in the install-validate folder.

 Once signed the following became available:

Certificate:
    Data:
        Version: 3 (0x2)
        Serial Number:
            77:ff:da:50:85:df:f9:4d:f9:a1:02:15:f4:f5:ef:76:f6:b3:12:76
        Signature Algorithm: sha256WithRSAEncryption
        Issuer: CN=CVI-Lab-Root-CA, O=CyberVisionaries Institute, C=US
        Validity
            Not Before: Mar 30 01:42:23 2026 GMT
            Not After : Apr 29 01:42:23 2026 GMT
        Subject: CN=CVI-Lab-Root-CA, O=CyberVisionaries Institute, C=US
        Subject Public Key Info:
            Public Key Algorithm: rsaEncryption
                Public-Key: (2048 bit)
                Modulus:
                    00:80:c8:ed:79:e9:b1:07:27:62:d8:12:4e:94:76:
                    23:7c:c4:1e:06:da:8a:56:43:e4:d3:ed:91:7a:e8:
                    21:9d:ea:23:ce:7b:07:05:1c:da:c5:aa:69:22:28:
                    a2:86:59:82:4c:cf:9c:f2:95:e6:69:bb:1f:8b:f4:
                    8c:af:9c:d7:11:62:a8:cc:1b:cd:17:f2:3d:7f:1f:
                    1b:da:0c:20:51:2a:26:37:af:38:70:83:75:d6:b5:
                    c9:f5:12:99:99:2a:f2:dc:1c:64:0e:78:8b:71:66:
                    81:86:c3:c0:68:df:3c:03:cc:bd:92:87:85:fc:dd:
                    c7:bf:01:ba:32:87:2c:76:13:e9:07:1c:29:bb:82:
                    78:36:cf:f6:d4:8c:ad:cf:0a:7c:84:7f:3a:f1:e1:
                    6b:56:9b:1b:be:20:68:88:6d:27:17:38:0b:c4:6d:
                    42:de:6c:0c:85:36:0f:36:79:de:af:ee:b2:14:89:
                    e5:df:e5:e8:11:66:7c:d6:3e:6b:f5:4c:11:c9:75:
                    77:51:d2:97:05:e6:97:f4:c7:84:4b:ce:56:70:e0:
                    3e:05:bd:34:5f:0a:f0:93:a0:33:58:11:83:22:59:
                    52:b9:30:05:a9:71:94:6e:b6:6d:7d:28:21:10:ad:
                    af:2d:8c:8e:33:26:a1:83:ba:a1:53:be:c3:ca:59:
                    4b:c7
                Exponent: 65537 (0x10001)
        X509v3 extensions:
            X509v3 Subject Key Identifier:
                DE:38:B7:4E:0D:24:17:F2:A4:01:CE:8C:05:D3:23:94:51:9D:78:68
            X509v3 Authority Key Identifier:
                DE:38:B7:4E:0D:24:17:F2:A4:01:CE:8C:05:D3:23:94:51:9D:78:68
            X509v3 Basic Constraints: critical
                CA:TRUE
    Signature Algorithm: sha256WithRSAEncryption
    Signature Value:
        2b:22:1b:d6:ab:2b:94:51:b4:89:71:70:4f:71:a0:5c:d0:d6:
        92:a3:fd:ae:84:c6:e6:b9:4d:e0:21:1e:e4:35:e7:5b:e7:9c:
        c3:55:d9:5b:3f:cb:82:29:62:2e:a4:4e:bf:6b:61:1a:f4:08:
        c2:6d:88:9a:1b:7e:9f:b8:62:40:89:31:fc:9e:49:6f:a6:a5:
        2c:5e:8a:12:0a:9f:c2:c6:33:2f:77:e4:63:2d:87:23:76:d1:
        27:ec:86:42:d5:16:13:cf:d6:f5:21:b1:74:1f:fb:57:42:77:
        df:12:e3:39:e5:e4:f3:e6:1c:97:af:c9:2b:96:00:70:95:47:
        3b:c9:ef:94:0e:3e:53:7e:ea:74:f9:05:33:f2:bc:1c:b3:11:
        1e:54:12:27:6d:36:43:9e:24:d4:1f:1b:8e:30:eb:cc:81:8c:
        6d:0e:d1:58:c8:18:d9:bf:5f:94:1c:7d:0f:a3:4f:21:7b:26:
        2e:73:e0:f5:fd:00:60:20:e8:37:34:5c:0a:a0:bc:26:58:3c:
        e3:79:d5:1c:96:d6:22:98:55:3d:32:a0:13:fb:06:d5:a0:3f:
        1a:6b:f8:a8:ff:08:13:68:00:ff:23:af:7b:be:c6:70:8e:6d:
        2a:8c:c3:4f:22:b8:cf:97:9a:66:56:ce:20:84:5c:94:bf:1a:
        6c:f6:9e:22



- The verified output return after signing — before:
Import-Certificate -FilePath "labs\week-04\submissions\install-validate\test-root-ca.crt" -CertStoreLocation Cert:\LocalMachine\Root


   PSParentPath: Microsoft.PowerShell.Security\Certificate::LocalMachine\Root

Thumbprint                                Subject
----------                                -------
8905E8557FB249E5CECFF5BE2DDBE0092BCB5D54  C=US, O=CyberVisionaries Institute, CN=...



 and after cleaning up the directory, validated the removal of the root [Get-ChildItem Cert:\LocalMachine\Root | Where-Object { $_.Subject -like "*CVI-Lab*" } | Remove-Item]

    Directory: C:\Users\Cyber\labs\week-04\submissions\install-validate


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----

-a----         3/29/2026   6:41 PM           1732 test-root-ca.key
-a----         3/29/2026   6:59 PM             42 test-root-ca.srl
-a----         3/29/2026   6:59 PM           1266 test-signed.crt
-a----         3/29/2026   6:47 PM            988 test-signed.csr
-a----         3/29/2026   6:46 PM           1732 test-signed.key




-Confirmation of the trust chain was established once the output was verified as:
 Certificate request self-signature ok
subject=CN=test.cvi-lab.local, O=CyberVisionaries Institute, C=US




---

## Key Findings
•openssl genrsa -out labs\week-04 genrsa: Can't open "labs\week-04" for writing, Permission denied- but the folder populated the correct file in spite of this message.
•The thumbprint provided by the PSParentPath: Microsoft.PowerShell.Security\Certificate::LocalMachine\Root.
•The Certificate request self-signature ok and labs/week-04/submissions/install-validate/test-signed.crt: OK.

---

## Explanation
Explain why the results matter.

- The test root CA self-signed because ot was self-created, recogniozed by immediately by the .key, .crt, and root already in the trust store. These items were identified by the file name and icon in the output.
- The changed noticed in the system is the local Trust Store kept the root CA in the certificate manager.
- In an enterprise environment, the one responsible for PKI’s controls what root CAs are installed on employee machines.
- If an attacker can install a root CA on a device it opens the entireenterpise to annoying breeches of security for every department, in every way.

---

## Challenges / Troubleshooting
No issues were encountered and allcommand lines were resolved.

---

## Artifacts
- test-root-ca.crt
- test-signed.crt
- test-signed.csr
