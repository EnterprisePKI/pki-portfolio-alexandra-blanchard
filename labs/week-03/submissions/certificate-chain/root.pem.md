-----BEGIN CERTIFICATE-----
MIIDRjCCAsugAwIBAgIQGp6v7G3o4ZtcGTFBto2Q3TAKBggqhkjOPQQDAzCBiDEL
MAkGA1UEBhMCVVMxEzARBgNVBAgTCk5ldyBKZXJzZXkxFDASBgNVBAcTC0plcnNl
eSBDaXR5MR4wHAYDVQQKExVUaGUgVVNFUlRSVVNUIE5ldHdvcmsxLjAsBgNVBAMT
JVVTRVJUcnVzdCBFQ0MgQ2VydGlmaWNhdGlvbiBBdXRob3JpdHkwHhcNMjEwMzIy
MDAwMDAwWhcNMzgwMTE4MjM1OTU5WjBfMQswCQYDVQQGEwJHQjEYMBYGA1UEChMP
U2VjdGlnbyBMaW1pdGVkMTYwNAYDVQQDEy1TZWN0aWdvIFB1YmxpYyBTZXJ2ZXIg
QXV0aGVudGljYXRpb24gUm9vdCBFNDYwdjAQBgcqhkjOPQIBBgUrgQQAIgNiAAR2
+pmpbiDt+dd34wc7qNs9Xzjoq1WmVk/WSOrsfy2qw7LFeeyZYX8QeccCWvkEN/U0
NSt3zn8gj1KjAIns1aeibVvjS5KToID1AZTc8GgHHs3u/iVStSBDHBv+6xnOQ6Oj
ggEgMIIBHDAfBgNVHSMEGDAWgBQ64QmG1M8ZwpZ2dEl23OA1xmNjmjAdBgNVHQ4E
FgQU0SLaTFnxS18mOKqd1u7rDcP7qWEwDgYDVR0PAQH/BAQDAgGGMA8GA1UdEwEB
/wQFMAMBAf8wHQYDVR0lBBYwFAYIKwYBBQUHAwEGCCsGAQUFBwMCMBEGA1UdIAQK
MAgwBgYEVR0gADBQBgNVHR8ESTBHMEWgQ6BBhj9odHRwOi8vY3JsLnVzZXJ0cnVz
dC5jb20vVVNFUlRydXN0RUNDQ2VydGlmaWNhdGlvbkF1dGhvcml0eS5jcmwwNQYI
KwYBBQUHAQEEKTAnMCUGCCsGAQUFBzABhhlodHRwOi8vb2NzcC51c2VydHJ1c3Qu
Y29tMAoGCCqGSM49BAMDA2kAMGYCMQCMCyBit99vX2ba6xEkDe+YO7vC0twjbkv9
PKpqGGuZ61JZryjFsp+DFpEclCVy4noCMQCwvZDXD/m2Ko1HA5Bkmz7YQOFAiNDD
49IWa2wdT7R3DtODaSXH/BiXv8fwB9su4tU=
-----END CERTIFICATE-----

 openssl x509 -in lab/03-week-03-certificate-anatomy/submissions/certificate-chain/root.pem -text -noout
Certificate:
    Data:
        Version: 3 (0x2)
        Serial Number:
            1a:9e:af:ec:6d:e8:e1:9b:5c:19:31:41:b6:8d:90:dd
        Signature Algorithm: ecdsa-with-SHA384
        Issuer: C=US, ST=New Jersey, L=Jersey City, O=The USERTRUST Network, CN=USERTrust ECC Certification Authority
        Validity
            Not Before: Mar 22 00:00:00 2021 GMT
            Not After : Jan 18 23:59:59 2038 GMT
        Subject: C=GB, O=Sectigo Limited, CN=Sectigo Public Server Authentication Root E46
        Subject Public Key Info:
            Public Key Algorithm: id-ecPublicKey
                Public-Key: (384 bit)
                pub:
                    04:76:fa:99:a9:6e:20:ed:f9:d7:77:e3:07:3b:a8:
                    db:3d:5f:38:e8:ab:55:a6:56:4f:d6:48:ea:ec:7f:
                    2d:aa:c3:b2:c5:79:ec:99:61:7f:10:79:c7:02:5a:
                    f9:04:37:f5:34:35:2b:77:ce:7f:20:8f:52:a3:00:
                    89:ec:d5:a7:a2:6d:5b:e3:4b:92:93:a0:80:f5:01:
                    94:dc:f0:68:07:1e:cd:ee:fe:25:52:b5:20:43:1c:
                    1b:fe:eb:19:ce:43:a3
                ASN1 OID: secp384r1
                NIST CURVE: P-384
        X509v3 extensions:
            X509v3 Authority Key Identifier:
                3A:E1:09:86:D4:CF:19:C2:96:76:74:49:76:DC:E0:35:C6:63:63:9A
            X509v3 Subject Key Identifier:
                D1:22:DA:4C:59:F1:4B:5F:26:38:AA:9D:D6:EE:EB:0D:C3:FB:A9:61
            X509v3 Key Usage: critical
                Digital Signature, Certificate Sign, CRL Sign
            X509v3 Basic Constraints: critical
                CA:TRUE
            X509v3 Extended Key Usage:
                TLS Web Server Authentication, TLS Web Client Authentication
            X509v3 Certificate Policies:
                Policy: X509v3 Any Policy
            X509v3 CRL Distribution Points:
                Full Name:
                  URI:http://crl.usertrust.com/USERTrustECCCertificationAuthority.crl

            Authority Information Access:
                OCSP - URI:http://ocsp.usertrust.com
    Signature Algorithm: ecdsa-with-SHA384
    Signature Value:
        30:66:02:31:00:8c:0b:20:62:b7:df:6f:5f:66:da:eb:11:24:
        0d:ef:98:3b:bb:c2:d2:dc:23:6e:4b:fd:3c:aa:6a:18:6b:99:
        eb:52:59:af:28:c5:b2:9f:83:16:91:1c:94:25:72:e2:7a:02:
        31:00:b0:bd:90:d7:0f:f9:b6:2a:8d:47:03:90:64:9b:3e:d8:
        40:e1:40:88:d0:c3:e3:d2:16:6b:6c:1d:4f:b4:77:0e:d3:83:
        69:25:c7:fc:18:97:bf:c7:f0:07:db:2e:e2:d5
