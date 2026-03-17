-----BEGIN CERTIFICATE-----
MIIDXzCCAuagAwIBAgIQNuBZ7YiN1Xrt1XC2cn+b2jAKBggqhkjOPQQDAzBfMQsw
CQYDVQQGEwJHQjEYMBYGA1UEChMPU2VjdGlnbyBMaW1pdGVkMTYwNAYDVQQDEy1T
ZWN0aWdvIFB1YmxpYyBTZXJ2ZXIgQXV0aGVudGljYXRpb24gUm9vdCBFNDYwHhcN
MjEwMzIyMDAwMDAwWhcNMzYwMzIxMjM1OTU5WjBgMQswCQYDVQQGEwJHQjEYMBYG
A1UEChMPU2VjdGlnbyBMaW1pdGVkMTcwNQYDVQQDEy5TZWN0aWdvIFB1YmxpYyBT
ZXJ2ZXIgQXV0aGVudGljYXRpb24gQ0EgRFYgRTM2MFkwEwYHKoZIzj0CAQYIKoZI
zj0DAQcDQgAEaKGnbAUnBYljHDmn/yUhxe3TLxKYuyzc9VXoSaCEV5F73Fhfa/Si
/RMsmwTFW3R9s7J6JpYZFmu4do3vk/Vgl6OCAYEwggF9MB8GA1UdIwQYMBaAFNEi
2kxZ8UtfJjiqndbu6w3D+6lhMB0GA1UdDgQWBBQXmagEwW/kLXCoChA9A9PpGrgm
YzAOBgNVHQ8BAf8EBAMCAYYwEgYDVR0TAQH/BAgwBgEB/wIBADAdBgNVHSUEFjAU
BggrBgEFBQcDAQYIKwYBBQUHAwIwGwYDVR0gBBQwEjAGBgRVHSAAMAgGBmeBDAEC
ATBUBgNVHR8ETTBLMEmgR6BFhkNodHRwOi8vY3JsLnNlY3RpZ28uY29tL1NlY3Rp
Z29QdWJsaWNTZXJ2ZXJBdXRoZW50aWNhdGlvblJvb3RFNDYuY3JsMIGEBggrBgEF
BQcBAQR4MHYwTwYIKwYBBQUHMAKGQ2h0dHA6Ly9jcnQuc2VjdGlnby5jb20vU2Vj
dGlnb1B1YmxpY1NlcnZlckF1dGhlbnRpY2F0aW9uUm9vdEU0Ni5wN2MwIwYIKwYB
BQUHMAGGF2h0dHA6Ly9vY3NwLnNlY3RpZ28uY29tMAoGCCqGSM49BAMDA2cAMGQC
MFsKnBQDh64l+v+aUYWjDCJKQMxHUUGmcwAYDIjJ9pbRYItMCIx5xu0oUb6sIfTX
qQIwPddcsDE4KdeLu1hJdpHgdLvsHAK3vygyLGujMU9xBJCDackRT93VHEE0gppg
NqdV
-----END CERTIFICATE-----

 openssl x509 -in lab/03-week-03-certificate-anatomy/submissions/certificate-chain/intermediate.pem -text -noout
Certificate:
    Data:
        Version: 3 (0x2)
        Serial Number:
            36:e0:59:ed:88:8d:d5:7a:ed:d5:70:b6:72:7f:9b:da
        Signature Algorithm: ecdsa-with-SHA384
        Issuer: C=GB, O=Sectigo Limited, CN=Sectigo Public Server Authentication Root E46
        Validity
            Not Before: Mar 22 00:00:00 2021 GMT
            Not After : Mar 21 23:59:59 2036 GMT
        Subject: C=GB, O=Sectigo Limited, CN=Sectigo Public Server Authentication CA DV E36
        Subject Public Key Info:
            Public Key Algorithm: id-ecPublicKey
                Public-Key: (256 bit)
                pub:
                    04:68:a1:a7:6c:05:27:05:89:63:1c:39:a7:ff:25:
                    21:c5:ed:d3:2f:12:98:bb:2c:dc:f5:55:e8:49:a0:
                    84:57:91:7b:dc:58:5f:6b:f4:a2:fd:13:2c:9b:04:
                    c5:5b:74:7d:b3:b2:7a:26:96:19:16:6b:b8:76:8d:
                    ef:93:f5:60:97
                ASN1 OID: prime256v1
                NIST CURVE: P-256
        X509v3 extensions:
            X509v3 Authority Key Identifier:
                D1:22:DA:4C:59:F1:4B:5F:26:38:AA:9D:D6:EE:EB:0D:C3:FB:A9:61
            X509v3 Subject Key Identifier:
                17:99:A8:04:C1:6F:E4:2D:70:A8:0A:10:3D:03:D3:E9:1A:B8:26:63
            X509v3 Key Usage: critical
                Digital Signature, Certificate Sign, CRL Sign
            X509v3 Basic Constraints: critical
                CA:TRUE, pathlen:0
            X509v3 Extended Key Usage:
                TLS Web Server Authentication, TLS Web Client Authentication
            X509v3 Certificate Policies:
                Policy: X509v3 Any Policy
                Policy: 2.23.140.1.2.1
            X509v3 CRL Distribution Points:
                Full Name:
                  URI:http://crl.sectigo.com/SectigoPublicServerAuthenticationRootE46.crl

            Authority Information Access:
                CA Issuers - URI:http://crt.sectigo.com/SectigoPublicServerAuthenticationRootE46.p7c
                OCSP - URI:http://ocsp.sectigo.com
    Signature Algorithm: ecdsa-with-SHA384
    Signature Value:
        30:64:02:30:5b:0a:9c:14:03:87:ae:25:fa:ff:9a:51:85:a3:
        0c:22:4a:40:cc:47:51:41:a6:73:00:18:0c:88:c9:f6:96:d1:
        60:8b:4c:08:8c:79:c6:ed:28:51:be:ac:21:f4:d7:a9:02:30:
        3d:d7:5c:b0:31:38:29:d7:8b:bb:58:49:76:91:e0:74:bb:ec:
        1c:02:b7:bf:28:32:2c:6b:a3:31:4f:71:04:90:83:69:c9:11:
        4f:dd:d5:1c:41:34:82:9a:60:36:a7:55
