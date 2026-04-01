
# Lab 01 — Convert Certificate Formats

## Overview
This week, we investigated  .der, .pem, and pfx packages. Diving deeper into how .pem is aligned to .crt and .cer outlines PKI diversity of certificate generation, regeneration, and distribution. 


---

## Environment
- Operating System: Win 11
- Terminal Used: OpenSSL (Embedded in PowerShell)
- OpenSSL Version: OpenSSL 3.6.1 27 Jan 2026 (Library: OpenSSL 3.6.1 27 Jan 2026)

— 

## Steps Performed

1. The lab began with entering the command [openssl s_client -connect google.com:443 -showcerts].
---
Certificate chain
 0 s:CN=*.google.com
   i:C=US, O=Google Trust Services, CN=WR2
   a:PKEY: EC, (prime256v1); sigalg: sha256WithRSAEncryption
   v:NotBefore: Mar  9 08:36:15 2026 GMT; NotAfter: Jun  1 08:36:14 2026 GMT
-----BEGIN CERTIFICATE-----
MIIOODCCDSCgAwIBAgIRAJ2c7jsU0d1hEMyhbSTO6C8wDQYJKoZIhvcNAQELBQAw
OzELMAkGA1UEBhMCVVMxHjAcBgNVBAoTFUdvb2dsZSBUcnVzdCBTZXJ2aWNlczEM
MAoGA1UEAxMDV1IyMB4XDTI2MDMwOTA4MzYxNVoXDTI2MDYwMTA4MzYxNFowFzEV
MBMGA1UEAwwMKi5nb29nbGUuY29tMFkwEwYHKoZIzj0CAQYIKoZIzj0DAQcDQgAE
6V5DDGIt9EJbakUtp1hZIrlSZas6meUSWrh0tHyzJ7oSFLTVkhdKf1zr3ePPBi/p
rnHil3DYUWTlFCjwbTURQ6OCDCQwggwgMA4GA1UdDwEB/wQEAwIHgDATBgNVHSUE
DDAKBggrBgEFBQcDATAMBgNVHRMBAf8EAjAAMB0GA1UdDgQWBBTJYRLN28MX79cg
nXTyqrg+DQV2sDAfBgNVHSMEGDAWgBTeGx7teRXUPjckwyG77DQ5bUKyMDBYBggr
BgEFBQcBAQRMMEowIQYIKwYBBQUHMAGGFWh0dHA6Ly9vLnBraS5nb29nL3dyMjAl
BggrBgEFBQcwAoYZaHR0cDovL2kucGtpLmdvb2cvd3IyLmNydDCCCfgGA1UdEQSC
Ce8wggnrggwqLmdvb2dsZS5jb22CFiouYXBwZW5naW5lLmdvb2dsZS5jb22CCSou
YmRuLmRldoIVKi5vcmlnaW4tdGVzdC5iZG4uZGV2ghIqLmNsb3VkLmdvb2dsZS5j
b22CGCouY3Jvd2Rzb3VyY2UuZ29vZ2xlLmNvbYIYKi5kYXRhY29tcHV0ZS5nb29n
bGUuY29tggsqLmdvb2dsZS5jYYILKi5nb29nbGUuY2yCDiouZ29vZ2xlLmNvLmlu
gg4qLmdvb2dsZS5jby5qcIIOKi5nb29nbGUuY28udWuCDyouZ29vZ2xlLmNvbS5h
coIPKi5nb29nbGUuY29tLmF1gg8qLmdvb2dsZS5jb20uYnKCDyouZ29vZ2xlLmNv
bS5jb4IPKi5nb29nbGUuY29tLm14gg8qLmdvb2dsZS5jb20udHKCDyouZ29vZ2xl
LmNvbS52boILKi5nb29nbGUuZGWCCyouZ29vZ2xlLmVzggsqLmdvb2dsZS5mcoIL
Ki5nb29nbGUuaHWCCyouZ29vZ2xlLml0ggsqLmdvb2dsZS5ubIILKi5nb29nbGUu
cGyCCyouZ29vZ2xlLnB0gg8qLmdvb2dsZWFwaXMuY26CDCouZ3N0YXRpYy5jboIQ
Ki5nc3RhdGljLWNuLmNvbYIPZ29vZ2xlY25hcHBzLmNughEqLmdvb2dsZWNuYXBw
cy5jboIRZ29vZ2xlYXBwcy1jbi5jb22CEyouZ29vZ2xlYXBwcy1jbi5jb22CDGdr
ZWNuYXBwcy5jboIOKi5na2VjbmFwcHMuY26CEmdvb2dsZWRvd25sb2Fkcy5jboIU
Ki5nb29nbGVkb3dubG9hZHMuY26CEHJlY2FwdGNoYS5uZXQuY26CEioucmVjYXB0
Y2hhLm5ldC5jboIQcmVjYXB0Y2hhLWNuLm5ldIISKi5yZWNhcHRjaGEtY24ubmV0
ggt3aWRldmluZS5jboINKi53aWRldmluZS5jboIRYW1wcHJvamVjdC5vcmcuY26C
EyouYW1wcHJvamVjdC5vcmcuY26CEWFtcHByb2plY3QubmV0LmNughMqLmFtcHBy
b2plY3QubmV0LmNughdnb29nbGUtYW5hbHl0aWNzLWNuLmNvbYIZKi5nb29nbGUt
YW5hbHl0aWNzLWNuLmNvbYIXZ29vZ2xlYWRzZXJ2aWNlcy1jbi5jb22CGSouZ29v
Z2xlYWRzZXJ2aWNlcy1jbi5jb22CEWdvb2dsZXZhZHMtY24uY29tghMqLmdvb2ds
ZXZhZHMtY24uY29tghFnb29nbGVhcGlzLWNuLmNvbYITKi5nb29nbGVhcGlzLWNu
LmNvbYIVZ29vZ2xlb3B0aW1pemUtY24uY29tghcqLmdvb2dsZW9wdGltaXplLWNu
LmNvbYISZG91YmxlY2xpY2stY24ubmV0ghQqLmRvdWJsZWNsaWNrLWNuLm5ldIIY
Ki5mbHMuZG91YmxlY2xpY2stY24ubmV0ghYqLmcuZG91YmxlY2xpY2stY24ubmV0
gg5kb3VibGVjbGljay5jboIQKi5kb3VibGVjbGljay5jboIUKi5mbHMuZG91Ymxl
Y2xpY2suY26CEiouZy5kb3VibGVjbGljay5jboIRZGFydHNlYXJjaC1jbi5uZXSC
EyouZGFydHNlYXJjaC1jbi5uZXSCHWdvb2dsZXRyYXZlbGFkc2VydmljZXMtY24u
Y29tgh8qLmdvb2dsZXRyYXZlbGFkc2VydmljZXMtY24uY29tghhnb29nbGV0YWdz
ZXJ2aWNlcy1jbi5jb22CGiouZ29vZ2xldGFnc2VydmljZXMtY24uY29tghdnb29n
bGV0YWdtYW5hZ2VyLWNuLmNvbYIZKi5nb29nbGV0YWdtYW5hZ2VyLWNuLmNvbYIY
Z29vZ2xlc3luZGljYXRpb24tY24uY29tghoqLmdvb2dsZXN5bmRpY2F0aW9uLWNu
LmNvbYIkKi5zYWZlZnJhbWUuZ29vZ2xlc3luZGljYXRpb24tY24uY29tghZhcHAt
bWVhc3VyZW1lbnQtY24uY29tghgqLmFwcC1tZWFzdXJlbWVudC1jbi5jb22CC2d2
dDEtY24uY29tgg0qLmd2dDEtY24uY29tggtndnQyLWNuLmNvbYINKi5ndnQyLWNu
LmNvbYILMm1kbi1jbi5uZXSCDSouMm1kbi1jbi5uZXSCFGdvb2dsZWZsaWdodHMt
Y24ubmV0ghYqLmdvb2dsZWZsaWdodHMtY24ubmV0ggxhZG1vYi1jbi5jb22CDiou
YWRtb2ItY24uY29tghkqLmdlbWluaS5jbG91ZC5nb29nbGUuY29tghRnb29nbGVz
YW5kYm94LWNuLmNvbYIWKi5nb29nbGVzYW5kYm94LWNuLmNvbYIeKi5zYWZlbnVw
Lmdvb2dsZXNhbmRib3gtY24uY29tgg0qLmdzdGF0aWMuY29tghQqLm1ldHJpYy5n
c3RhdGljLmNvbYIKKi5ndnQxLmNvbYIRKi5nY3BjZG4uZ3Z0MS5jb22CCiouZ3Z0
Mi5jb22CDiouZ2NwLmd2dDIuY29tghAqLnVybC5nb29nbGUuY29tghYqLnlvdXR1
YmUtbm9jb29raWUuY29tggsqLnl0aW1nLmNvbYIKYWkuYW5kcm9pZIILYW5kcm9p
ZC5jb22CDSouYW5kcm9pZC5jb22CEyouZmxhc2guYW5kcm9pZC5jb22CBGcuY26C
BiouZy5jboIEZy5jb4IGKi5nLmNvggZnb28uZ2yCCnd3dy5nb28uZ2yCFGdvb2ds
ZS1hbmFseXRpY3MuY29tghYqLmdvb2dsZS1hbmFseXRpY3MuY29tggpnb29nbGUu
Y29tghJnb29nbGVjb21tZXJjZS5jb22CFCouZ29vZ2xlY29tbWVyY2UuY29tgghn
Z3BodC5jboIKKi5nZ3BodC5jboIKdXJjaGluLmNvbYIMKi51cmNoaW4uY29tggh5
b3V0dS5iZYILeW91dHViZS5jb22CDSoueW91dHViZS5jb22CEW11c2ljLnlvdXR1
YmUuY29tghMqLm11c2ljLnlvdXR1YmUuY29tghR5b3V0dWJlZWR1Y2F0aW9uLmNv
bYIWKi55b3V0dWJlZWR1Y2F0aW9uLmNvbYIPeW91dHViZWtpZHMuY29tghEqLnlv
dXR1YmVraWRzLmNvbYIFeXQuYmWCByoueXQuYmWCGmFuZHJvaWQuY2xpZW50cy5n
b29nbGUuY29tghMqLmFuZHJvaWQuZ29vZ2xlLmNughIqLmNocm9tZS5nb29nbGUu
Y26CFiouZGV2ZWxvcGVycy5nb29nbGUuY26CFSouYWlzdHVkaW8uZ29vZ2xlLmNv
bTATBgNVHSAEDDAKMAgGBmeBDAECATA2BgNVHR8ELzAtMCugKaAnhiVodHRwOi8v
Yy5wa2kuZ29vZy93cjIvNzVyNFp5QTN2QTAuY3JsMIIBBgYKKwYBBAHWeQIEAgSB
9wSB9ADyAHcA0W6ppWgHfmY1oD83pd28A6U8QRIU1IgY9ekxsyPLlQQAAAGc0fRk
PAAABAMASDBGAiEAr372fSSEFYSQJJFRL9HreUQEVyTZib/1mrWsq+isINMCIQCl
LJTMLSDng4GyzEvfYhbzLPVZOjldnt9HeZNz0JCygwB3AA5XlLzzrqk+MxssmQez
95Dfm8I9cTIl3SGpJaxhxU4hAAABnNH0Y2IAAAQDAEgwRgIhANSKaQcySfyYLYuL
pkjDFpzgdlQQcbDQF1Ov47Cyyy8pAiEA0EeOv3Ssvnfd2bA68DPW648Bnz92Ep1+
YMDN3Ui+DF8wDQYJKoZIhvcNAQELBQADggEBADiZ26gxb+5vw7kn47E/wXokvXr4
ZVzpIlOQkVxg0Pn9mE+DGcWiEa1d7/+4CdGdYntCFJsWM90eshG51b3q1c4fPygg
McyzaR7K4Le4LWZLhanI8U86ZFmhH1Sw2OHJ8FVqKoarFnI4J2zmTpfMSqSwGEmU
JcrpRNlu7K7i7zC0qlwpB073EKQOdkwg7PYPr7peHV4EgZb2tBzrknLA8/RnACtL
J9Jez2kj7T2Te4LT3EMfBoUYT4Qy7yXDH0YA8yLjOxR6IuUxqK3Fgqcnm5BwSfZa
BpzSI24J1m+NzlRaFumqmtfrrOuVorhx88TUHEsEETzaK6oQON8SEhXi518=
-----END CERTIFICATE-----
 1 s:C=US, O=Google Trust Services, CN=WR2
   i:C=US, O=Google Trust Services LLC, CN=GTS Root R1
   a:PKEY: RSA, 2048 (bit); sigalg: sha256WithRSAEncryption
   v:NotBefore: Dec 13 09:00:00 2023 GMT; NotAfter: Feb 20 14:00:00 2029 GMT
-----BEGIN CERTIFICATE-----
MIIFCzCCAvOgAwIBAgIQf/AFoHxM3tEArZ1mpRB7mDANBgkqhkiG9w0BAQsFADBH
MQswCQYDVQQGEwJVUzEiMCAGA1UEChMZR29vZ2xlIFRydXN0IFNlcnZpY2VzIExM
QzEUMBIGA1UEAxMLR1RTIFJvb3QgUjEwHhcNMjMxMjEzMDkwMDAwWhcNMjkwMjIw
MTQwMDAwWjA7MQswCQYDVQQGEwJVUzEeMBwGA1UEChMVR29vZ2xlIFRydXN0IFNl
cnZpY2VzMQwwCgYDVQQDEwNXUjIwggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEK
AoIBAQCp/5x/RR5wqFOfytnlDd5GV1d9vI+aWqxG8YSau5HbyfsvAfuSCQAWXqAc
+MGr+XgvSszYhaLYWTwO0xj7sfUkDSbutltkdnwUxy96zqhMt/TZCPzfhyM1IKji
aeKMTj+xWfpgoh6zySBTGYLKNlNtYE3pAJH8do1cCA8Kwtzxc2vFE24KT3rC8gIc
LrRjg9ox9i11MLL7q8Ju26nADrn5Z9TDJVd06wW06Y613ijNzHoU5HEDy01hLmFX
xRmpC5iEGuh5KdmyjS//V2pm4M6rlagplmNwEmceOuHbsCFx13ye/aoXbv4r+zgX
FNFmp6+atXDMyGOBOozAKql2N87jAgMBAAGjgf4wgfswDgYDVR0PAQH/BAQDAgGG
MB0GA1UdJQQWMBQGCCsGAQUFBwMBBggrBgEFBQcDAjASBgNVHRMBAf8ECDAGAQH/
AgEAMB0GA1UdDgQWBBTeGx7teRXUPjckwyG77DQ5bUKyMDAfBgNVHSMEGDAWgBTk
rysmcRorSCeFL1JmLO/wiRNxPjA0BggrBgEFBQcBAQQoMCYwJAYIKwYBBQUHMAKG
GGh0dHA6Ly9pLnBraS5nb29nL3IxLmNydDArBgNVHR8EJDAiMCCgHqAchhpodHRw
Oi8vYy5wa2kuZ29vZy9yL3IxLmNybDATBgNVHSAEDDAKMAgGBmeBDAECATANBgkq
hkiG9w0BAQsFAAOCAgEARXWL5R87RBOWGqtY8TXJbz3S0DNKhjO6V1FP7sQ02hYS
TL8Tnw3UVOlIecAwPJQl8hr0ujKUtjNyC4XuCRElNJThb0Lbgpt7fyqaqf9/qdLe
SiDLs/sDA7j4BwXaWZIvGEaYzq9yviQmsR4ATb0IrZNBRAq7x9UBhb+TV+PfdBJT
DhEl05vc3ssnbrPCuTNiOcLgNeFbpwkuGcuRKnZc8d/KI4RApW//mkHgte8y0YWu
ryUJ8GLFbsLIbjL9uNrizkqRSvOFVU6xddZIMy9vhNkSXJ/UcZhjJY1pXAprffJB
vei7j+Qi151lRehMCofa6WBmiA4fx+FOVsV2/7R6V2nyAiIJJkEd2nSi5SnzxJrl
Xdaqev3htytmOPvoKWa676ATL/hzfvDaQBEcXd2Ppvy+275W+DKcH0FBbX62xevG
iza3F4ydzxl6NJ8hk8R+dDXSqv1MbRT1ybB5W0k8878XSOjvmiYTDIfyc9acxVJr
Y/cykHipa+te1pOhv7wYPYtZ9orGBV5SGOJm4NrB3K1aJar0RfzxC3ikr7Dyc6Qw
qDTBU39CluVIQeuQRgwG3MuSxl7zRERDRilGoKb8uY45JzmxWuKxrfwT/478JuHU
/oTxUFqOl2stKnn7QGTq8z29W+GgBLCXSBxC9epaHM0myFH/FJlniXJfHeytWt0=
-----END CERTIFICATE-----
 2 s:C=US, O=Google Trust Services LLC, CN=GTS Root R1
   i:C=BE, O=GlobalSign nv-sa, OU=Root CA, CN=GlobalSign Root CA
   a:PKEY: RSA, 4096 (bit); sigalg: sha256WithRSAEncryption
   v:NotBefore: Jun 19 00:00:42 2020 GMT; NotAfter: Jan 28 00:00:42 2028 GMT
-----BEGIN CERTIFICATE-----
MIIFYjCCBEqgAwIBAgIQd70NbNs2+RrqIQ/E8FjTDTANBgkqhkiG9w0BAQsFADBX
MQswCQYDVQQGEwJCRTEZMBcGA1UEChMQR2xvYmFsU2lnbiBudi1zYTEQMA4GA1UE
CxMHUm9vdCBDQTEbMBkGA1UEAxMSR2xvYmFsU2lnbiBSb290IENBMB4XDTIwMDYx
OTAwMDA0MloXDTI4MDEyODAwMDA0MlowRzELMAkGA1UEBhMCVVMxIjAgBgNVBAoT
GUdvb2dsZSBUcnVzdCBTZXJ2aWNlcyBMTEMxFDASBgNVBAMTC0dUUyBSb290IFIx
MIICIjANBgkqhkiG9w0BAQEFAAOCAg8AMIICCgKCAgEAthECix7joXebO9y/lD63
ladAPKH9gvl9MgaCcfb2jH/76Nu8ai6Xl6OMS/kr9rH5zoQdsfnFl97vufKj6bwS
iV6nqlKr+CMny6SxnGPb15l+8Ape62im9MZaRw1NEDPjTrETo8gYbEvs/AmQ351k
KSUjB6G00j0uYODP0gmHu81I8E3CwnqIiru6z1kZ1q+PsAewnjHxgsHA3y6mbWwZ
DrXYfiYaRQM9sHmklCitD38m5agI/pboPGiUU+6DOogrFZYJsuB6jC511pzrp1Zk
j5ZPaK49l8KEj8C8QMALXL32h7M1bKwYUH+E4EzNktMg6TO8UpmvMrUpsyUqtEj5
cuHKZPfmghCN6J3Cioj6OGaK/GP5Afl4/Xtcd/p2h/rs37EOeZVXtL0m79YB0esW
CruOC7XFxYpVq9Os6pFLKcwZpDIlTirxZUTQAs6qzkm06p98g7BAe+dDq6dso499
iYH6TKX/1Y7DzkvgtdizjkXPdsDtQCv9Uw+wp9U7DbGKogPeMa3Md+pvez7W35Ei
Eua++tgy/BBjFFFy3l3WFpO9KWgz7zpm7AeKJt8T11dleCfeXkkUAKIAf5qoIbap
sZWwpbkNFhHax2xIPEDgfg1azVY80ZcFuctL7TlLnMQ/0lUTbiSw1nH69MG6zO0b
9f6BQdgAmD06yK56mDcYBZUCAwEAAaOCATgwggE0MA4GA1UdDwEB/wQEAwIBhjAP
BgNVHRMBAf8EBTADAQH/MB0GA1UdDgQWBBTkrysmcRorSCeFL1JmLO/wiRNxPjAf
BgNVHSMEGDAWgBRge2YaRQ2XyolQL30EzTSo//z9SzBgBggrBgEFBQcBAQRUMFIw
JQYIKwYBBQUHMAGGGWh0dHA6Ly9vY3NwLnBraS5nb29nL2dzcjEwKQYIKwYBBQUH
MAKGHWh0dHA6Ly9wa2kuZ29vZy9nc3IxL2dzcjEuY3J0MDIGA1UdHwQrMCkwJ6Al
oCOGIWh0dHA6Ly9jcmwucGtpLmdvb2cvZ3NyMS9nc3IxLmNybDA7BgNVHSAENDAy
MAgGBmeBDAECATAIBgZngQwBAgIwDQYLKwYBBAHWeQIFAwIwDQYLKwYBBAHWeQIF
AwMwDQYJKoZIhvcNAQELBQADggEBADSkHrEoo9C0dhemMXoh6dFSPsjbdBZBiLg9
NR3t5P+T4Vxfq7vqfM/b5A3Ri1fyJm9bvhdGaJQ3b2t6yMAYN/olUazsaL+yyEn9
WprKASOshIArAoyZl+tJaox118fessmXn1hIVw41oeQa1v1vg4Fv74zPl6/AhSrw
9U5pCZEt4Wi4wStz6dTZ/CLANx8LZh1J7QJVj2fhMtfTJr9w4z30Z209fOU0iOMy
+qduBmpvvYuR7hZL6Dupszfnw0Skfths18dG9ZKb59UhvmaSGZRVbNQpsg3BZlvi
d0lIKO2d1xozclOzgjXPYovJJIultzkMu34qQb9Sz/yilrbCgj8=
-----END CERTIFICATE-----
---
Server certificate
subject=CN=*.google.com
issuer=C=US, O=Google Trust Services, CN=WR2
---
No client certificate CA names sent
Peer signing digest: SHA256
Peer signature type: ecdsa_secp256r1_sha256
Negotiated TLS1.3 group: X25519MLKEM768
---
SSL handshake has read 7724 bytes and written 1621 bytes
Verification error: unable to get local issuer certificate
---
New, TLSv1.3, Cipher is TLS_AES_256_GCM_SHA384
Protocol: TLSv1.3
Server public key is 256 bit
This TLS version forbids renegotiation.
Compression: NONE
Expansion: NONE
No ALPN negotiated
Early data was not sent
Verify return code: 20 (unable to get local issuer certificate)
---

mkdir -p labs/week-04/submissions/convert-formats

---
Post-Handshake New Session Ticket arrived:
SSL-Session:
    Protocol  : TLSv1.3
    Cipher    : TLS_AES_256_GCM_SHA384
    Session-ID: C5DC1343650319C8780F7D403A854A803BBF2A285D03DDC0E987364F20EADD27
    Session-ID-ctx:
    Resumption PSK: FC7EDF896008E61DEACCA20AE96D322A0569DB51B95D6C80364D6CFEDCD679D07890722DB169E7F576B78A8D422FB665
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 172800 (seconds)
    TLS session ticket:
    0000 - 02 7a 70 58 23 00 29 9b-0c dc 13 1b 93 f5 3a 6a   .zpX#.).......:j
    0010 - e7 98 cb 39 db 1c 1e 06-2c 20 28 35 2a f1 5f ac   ...9...., (5*._.
    0020 - ee 2a 06 6d 15 ca a8 25-e8 aa 81 95 bd c9 db 4e   .*.m...%.......N
    0030 - 7b a7 d5 6d 21 53 c5 53-7b 89 8f c7 9b 40 da cc   {..m!S.S{....@..
    0040 - 12 90 3e 33 71 b0 46 6a-94 b3 77 4a 73 76 c4 48   ..>3q.Fj..wJsv.H
    0050 - fa 85 47 84 80 a9 43 f4-3b ac aa 4b 6b 50 17 f6   ..G...C.;..KkP..
    0060 - f6 e3 20 9f 4c cd 26 3d-3a 91 87 5f 47 7f da 5f   .. .L.&=:.._G.._
    0070 - e2 09 42 1a 3c 42 c5 07-8f 6b 8e c4 a0 d2 37 8c   ..B.<B...k....7.
    0080 - 11 eb c0 be d5 c5 98 69-51 93 ac c1 56 41 3e dd   .......iQ...VA>.
    0090 - e3 99 51 9d d6 3d 80 5a-a2 b8 d3 95 5b 6e 39 fd   ..Q..=.Z....[n9.
    00a0 - 95 d1 5f 54 64 ac 45 7c-2a 79 74 fd 4e b0 26 a5   .._Td.E|*yt.N.&.
    00b0 - 22 7b 98 03 6d e4 ba b8-a5 11 68 53 2b 6c 8e f2   "{..m.....hS+l..
    00c0 - 56 eb f8 a7 c0 ad a2 d2-27 2b 21 87 43 fa 81 96   V.......'+!.C...
    00d0 - 1b 58 9f 0e c0 7c 15 5b-43 18 9b 3a e1 fe ef 57   .X...|.[C..:...W
    00e0 - 3c de c0 e6 60 2b f4 17-72 be 06 53 45 41 8a ff   <...`+..r..SEA..
    00f0 - e6 11 9f 70 46 c4                                 ...pF.

    Start Time: 1774809809
    Timeout   : 7200 (sec)
    Verify return code: 20 (unable to get local issuer certificate)
    Extended master secret: no
    Max Early Data: 14336
---
read R BLOCK
---
Post-Handshake New Session Ticket arrived:
SSL-Session:
    Protocol  : TLSv1.3
    Cipher    : TLS_AES_256_GCM_SHA384
    Session-ID: 68DBB51B0E4EA6174815AE6273465BBE196D1FFF21D2BDAEAF67EF8DDFB4414B
    Session-ID-ctx:
    Resumption PSK: A6DFE277FC84DC99D7BA942DF28B15A17E64B31EEF721E8FAC6B2E6EE4CE7EF93C52BB3F452B6E09FD8F854B6450D2E4
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 172800 (seconds)
    TLS session ticket:
    0000 - 02 7a 70 58 23 00 29 9b-0c dc 13 1b 93 f5 3a 6a   .zpX#.).......:j
    0010 - d1 15 5c 48 e2 89 b2 cb-ce 42 04 48 52 cb 24 5d   ..\H.....B.HR.$]
    0020 - d0 89 e5 cf 23 2c 9b 64-a0 e7 70 97 00 f1 7f 15   ....#,.d..p.....
    0030 - 72 99 bb 93 20 f6 a9 14-f4 ec 6d f9 4c 95 10 e0   r... .....m.L...
    0040 - e9 c9 c4 6a 8f b5 11 b9-fc 1d e0 0c 38 37 ff 64   ...j........87.d
    0050 - a6 77 30 91 8d 35 03 4e-6f c7 03 09 34 11 8b 47   .w0..5.No...4..G
    0060 - 96 8c 53 da 9d 30 d9 3a-00 e7 0e 57 96 5a 2d 40   ..S..0.:...W.Z-@
    0070 - b8 c2 69 7c 3f f3 33 b3-2d c9 c2 f0 d0 fd 39 b3   ..i|?.3.-.....9.
    0080 - 80 54 58 47 9d 80 dd 42-8a a3 14 3e a5 52 c1 52   .TXG...B...>.R.R
    0090 - 9e 8f a1 0c 98 3f a4 81-93 e1 9b 69 54 eb 86 eb   .....?.....iT...
    00a0 - 2b 30 c8 d8 d0 40 6f d3-6a dc 6e 7e 5e c5 54 c1   +0...@o.j.n~^.T.
    00b0 - c2 2d 7a d4 e3 fe 40 12-4b f6 73 24 8e d2 25 4f   .-z...@.K.s$..%O
    00c0 - b7 75 d0 97 7f 6c 25 ba-eb a1 d3 10 82 a2 16 65   .u...l%........e
    00d0 - d8 c2 a1 9d 20 90 bb 5f-f3 8e b1 7b 7f c0 e5 e2   .... .._...{....
    00e0 - 8f 07 23 d8 04 f1 12 38-d1 0f e0 53 45 41 43 da   ..#....8...SEAC.
    00f0 - 85 a1 b6 bb dc aa                                 ......

    Start Time: 1774809809
    Timeout   : 7200 (sec)
    Verify return code: 20 (unable to get local issuer certificate)
    Extended master secret: no
    Max Early Data: 14336
---
read R BLOCK
HTTP/1.0 400 Bad Request
Content-Type: text/html; charset=UTF-8
Referrer-Policy: no-referrer
Content-Length: 1555
Date: Sun, 29 Mar 2026 18:43:30 GMT

<!DOCTYPE html>
<html lang=en>
  <meta charset=utf-8>
  <meta name=viewport content="initial-scale=1, minimum-scale=1, width=device-width">
  <title>Error 400 (Bad Request)!!1</title>
  <style>
    *{margin:0;padding:0}html,code{font:15px/22px arial,sans-serif}html{background:#fff;color:#222;padding:15px}body{margin:7% auto 0;max-width:390px;min-height:180px;padding:30px 0 15px}* > body{background:url(//www.google.com/images/errors/robot.png) 100% 5px no-repeat;padding-right:205px}p{margin:11px 0 22px;overflow:hidden}ins{color:#777;text-decoration:none}a img{border:0}@media screen and (max-width:772px){body{background:none;margin-top:0;max-width:none;padding-right:0}}#logo{background:url(//www.google.com/images/branding/googlelogo/1x/googlelogo_color_150x54dp.png) no-repeat;margin-left:-5px}@media only screen and (min-resolution:192dpi){#logo{background:url(//www.google.com/images/branding/googlelogo/2x/googlelogo_color_150x54dp.png) no-repeat 0% 0%/100% 100%;-moz-border-image:url(//www.google.com/images/branding/googlelogo/2x/googlelogo_color_150x54dp.png) 0}}@media only screen and (-webkit-min-device-pixel-ratio:2){#logo{background:url(//www.google.com/images/branding/googlelogo/2x/googlelogo_color_150x54dp.png) no-repeat;-webkit-background-size:100% 100%}}#logo{display:inline-block;height:54px;width:150px}
  </style>
  <a href=//www.google.com/><span id=logo aria-label=Google></span></a>
  <p><b>400.</b> <ins>ThatΓÇÖs an error.</ins>
  <p>Your client has issued a malformed or illegal request.  <ins>ThatΓÇÖs all we know.</ins>
40110000:error:0A000126:SSL routines::unexpected eof while reading:ssl\record\rec_layer_s3.c:703:
40110000:error:0A000197:SSL routines:SSL_shutdown:shutdown while in init:ssl\ssl_lib.c:2804:]
2. Next, the command [labs/week-04/submissions/convert-formats/leaf_cert.pem] produced an embedded file [-----BEGIN CERTIFICATE-----
MIIONTCCDR2gAwIBAgIRALJP+TqZdfpnCkWkeE86zGUwDQYJKoZIhvcNAQELBQAw
OzELMAkGA1UEBhMCVVMxHjAcBgNVBAoTFUdvb2dsZSBUcnVzdCBTZXJ2aWNlczEM
MAoGA1UEAxMDV1IyMB4XDTI2MDIwMjA4MzYzOFoXDTI2MDQyNzA4MzYzN1owFzEV
MBMGA1UEAwwMKi5nb29nbGUuY29tMFkwEwYHKoZIzj0CAQYIKoZIzj0DAQcDQgAE
2cn+FWG4mw7AfiS5XeXhRjdisXdsuW+caz07OL6qWKs+7jfJhxQqNe6fa45kgx4M
x6Vd34/4boHWqg9oeSGWM6OCDCEwggwdMA4GA1UdDwEB/wQEAwIHgDATBgNVHSUE
DDAKBggrBgEFBQcDATAMBgNVHRMBAf8EAjAAMB0GA1UdDgQWBBSmcwknwyFVF7vn
fDhd7QVRJQBUtjAfBgNVHSMEGDAWgBTeGx7teRXUPjckwyG77DQ5bUKyMDBYBggr
BgEFBQcBAQRMMEowIQYIKwYBBQUHMAGGFWh0dHA6Ly9vLnBraS5nb29nL3dyMjAl
BggrBgEFBQcwAoYZaHR0cDovL2kucGtpLmdvb2cvd3IyLmNydDCCCfgGA1UdEQSC
Ce8wggnrggwqLmdvb2dsZS5jb22CFiouYXBwZW5naW5lLmdvb2dsZS5jb22CCSou
YmRuLmRldoIVKi5vcmlnaW4tdGVzdC5iZG4uZGV2ghIqLmNsb3VkLmdvb2dsZS5j
b22CGCouY3Jvd2Rzb3VyY2UuZ29vZ2xlLmNvbYIYKi5kYXRhY29tcHV0ZS5nb29n
bGUuY29tggsqLmdvb2dsZS5jYYILKi5nb29nbGUuY2yCDiouZ29vZ2xlLmNvLmlu
gg4qLmdvb2dsZS5jby5qcIIOKi5nb29nbGUuY28udWuCDyouZ29vZ2xlLmNvbS5h
coIPKi5nb29nbGUuY29tLmF1gg8qLmdvb2dsZS5jb20uYnKCDyouZ29vZ2xlLmNv
bS5jb4IPKi5nb29nbGUuY29tLm14gg8qLmdvb2dsZS5jb20udHKCDyouZ29vZ2xl
LmNvbS52boILKi5nb29nbGUuZGWCCyouZ29vZ2xlLmVzggsqLmdvb2dsZS5mcoIL
Ki5nb29nbGUuaHWCCyouZ29vZ2xlLml0ggsqLmdvb2dsZS5ubIILKi5nb29nbGUu
cGyCCyouZ29vZ2xlLnB0gg8qLmdvb2dsZWFwaXMuY26CDCouZ3N0YXRpYy5jboIQ
Ki5nc3RhdGljLWNuLmNvbYIPZ29vZ2xlY25hcHBzLmNughEqLmdvb2dsZWNuYXBw
cy5jboIRZ29vZ2xlYXBwcy1jbi5jb22CEyouZ29vZ2xlYXBwcy1jbi5jb22CDGdr
ZWNuYXBwcy5jboIOKi5na2VjbmFwcHMuY26CEmdvb2dsZWRvd25sb2Fkcy5jboIU
Ki5nb29nbGVkb3dubG9hZHMuY26CEHJlY2FwdGNoYS5uZXQuY26CEioucmVjYXB0
Y2hhLm5ldC5jboIQcmVjYXB0Y2hhLWNuLm5ldIISKi5yZWNhcHRjaGEtY24ubmV0
ggt3aWRldmluZS5jboINKi53aWRldmluZS5jboIRYW1wcHJvamVjdC5vcmcuY26C
EyouYW1wcHJvamVjdC5vcmcuY26CEWFtcHByb2plY3QubmV0LmNughMqLmFtcHBy
b2plY3QubmV0LmNughdnb29nbGUtYW5hbHl0aWNzLWNuLmNvbYIZKi5nb29nbGUt
YW5hbHl0aWNzLWNuLmNvbYIXZ29vZ2xlYWRzZXJ2aWNlcy1jbi5jb22CGSouZ29v
Z2xlYWRzZXJ2aWNlcy1jbi5jb22CEWdvb2dsZXZhZHMtY24uY29tghMqLmdvb2ds
ZXZhZHMtY24uY29tghFnb29nbGVhcGlzLWNuLmNvbYITKi5nb29nbGVhcGlzLWNu
LmNvbYIVZ29vZ2xlb3B0aW1pemUtY24uY29tghcqLmdvb2dsZW9wdGltaXplLWNu
LmNvbYISZG91YmxlY2xpY2stY24ubmV0ghQqLmRvdWJsZWNsaWNrLWNuLm5ldIIY
Ki5mbHMuZG91YmxlY2xpY2stY24ubmV0ghYqLmcuZG91YmxlY2xpY2stY24ubmV0
gg5kb3VibGVjbGljay5jboIQKi5kb3VibGVjbGljay5jboIUKi5mbHMuZG91Ymxl
Y2xpY2suY26CEiouZy5kb3VibGVjbGljay5jboIRZGFydHNlYXJjaC1jbi5uZXSC
EyouZGFydHNlYXJjaC1jbi5uZXSCHWdvb2dsZXRyYXZlbGFkc2VydmljZXMtY24u
Y29tgh8qLmdvb2dsZXRyYXZlbGFkc2VydmljZXMtY24uY29tghhnb29nbGV0YWdz
ZXJ2aWNlcy1jbi5jb22CGiouZ29vZ2xldGFnc2VydmljZXMtY24uY29tghdnb29n
bGV0YWdtYW5hZ2VyLWNuLmNvbYIZKi5nb29nbGV0YWdtYW5hZ2VyLWNuLmNvbYIY
Z29vZ2xlc3luZGljYXRpb24tY24uY29tghoqLmdvb2dsZXN5bmRpY2F0aW9uLWNu
LmNvbYIkKi5zYWZlZnJhbWUuZ29vZ2xlc3luZGljYXRpb24tY24uY29tghZhcHAt
bWVhc3VyZW1lbnQtY24uY29tghgqLmFwcC1tZWFzdXJlbWVudC1jbi5jb22CC2d2
dDEtY24uY29tgg0qLmd2dDEtY24uY29tggtndnQyLWNuLmNvbYINKi5ndnQyLWNu
LmNvbYILMm1kbi1jbi5uZXSCDSouMm1kbi1jbi5uZXSCFGdvb2dsZWZsaWdodHMt
Y24ubmV0ghYqLmdvb2dsZWZsaWdodHMtY24ubmV0ggxhZG1vYi1jbi5jb22CDiou
YWRtb2ItY24uY29tghkqLmdlbWluaS5jbG91ZC5nb29nbGUuY29tghRnb29nbGVz
YW5kYm94LWNuLmNvbYIWKi5nb29nbGVzYW5kYm94LWNuLmNvbYIeKi5zYWZlbnVw
Lmdvb2dsZXNhbmRib3gtY24uY29tgg0qLmdzdGF0aWMuY29tghQqLm1ldHJpYy5n
c3RhdGljLmNvbYIKKi5ndnQxLmNvbYIRKi5nY3BjZG4uZ3Z0MS5jb22CCiouZ3Z0
Mi5jb22CDiouZ2NwLmd2dDIuY29tghAqLnVybC5nb29nbGUuY29tghYqLnlvdXR1
YmUtbm9jb29raWUuY29tggsqLnl0aW1nLmNvbYIKYWkuYW5kcm9pZIILYW5kcm9p
ZC5jb22CDSouYW5kcm9pZC5jb22CEyouZmxhc2guYW5kcm9pZC5jb22CBGcuY26C
BiouZy5jboIEZy5jb4IGKi5nLmNvggZnb28uZ2yCCnd3dy5nb28uZ2yCFGdvb2ds
ZS1hbmFseXRpY3MuY29tghYqLmdvb2dsZS1hbmFseXRpY3MuY29tggpnb29nbGUu
Y29tghJnb29nbGVjb21tZXJjZS5jb22CFCouZ29vZ2xlY29tbWVyY2UuY29tgghn
Z3BodC5jboIKKi5nZ3BodC5jboIKdXJjaGluLmNvbYIMKi51cmNoaW4uY29tggh5
b3V0dS5iZYILeW91dHViZS5jb22CDSoueW91dHViZS5jb22CEW11c2ljLnlvdXR1
YmUuY29tghMqLm11c2ljLnlvdXR1YmUuY29tghR5b3V0dWJlZWR1Y2F0aW9uLmNv
bYIWKi55b3V0dWJlZWR1Y2F0aW9uLmNvbYIPeW91dHViZWtpZHMuY29tghEqLnlv
dXR1YmVraWRzLmNvbYIFeXQuYmWCByoueXQuYmWCGmFuZHJvaWQuY2xpZW50cy5n
b29nbGUuY29tghMqLmFuZHJvaWQuZ29vZ2xlLmNughIqLmNocm9tZS5nb29nbGUu
Y26CFiouZGV2ZWxvcGVycy5nb29nbGUuY26CFSouYWlzdHVkaW8uZ29vZ2xlLmNv
bTATBgNVHSAEDDAKMAgGBmeBDAECATA2BgNVHR8ELzAtMCugKaAnhiVodHRwOi8v
Yy5wa2kuZ29vZy93cjIvb1E2bnlyOEYwbTAuY3JsMIIBAwYKKwYBBAHWeQIEAgSB
9ASB8QDvAHUAFoMtq/CpJQ8P8DqlRf/Iv8gj0IdL9gQpJ/jnHzMT9foAAAGcHbYd
+gAABAMARjBEAiBMc/39XLmnLubvldKj/1SBb5x3kEPFmA/YEO6po+BOFAIgS/fO
G6/MZOnqhwFLw7qwlnJM++Ns59pMzvMsoriAp1YAdgCWl2S/VViXrfdDh2g3CEJ3
6fA61fak8zZuRqQ/D8qpxgAAAZwdth4GAAAEAwBHMEUCIQDPGMVaWob4fqLrw1Qp
wHUwg+jheiTHRa97pm6+P5q3OQIgDmwQfpegjPUve7yiKEbCIQQKMw7leq3/7rFk
U+Xxj+YwDQYJKoZIhvcNAQELBQADggEBAI5JQeZ7ZLh7oiks3QxSYd2686DyVODZ
k4fnzMSypK8h+0fh8PsSEURp2JOwe+pJL3rZr3DDl0Tdp2RIYagBpNM2/9BXgOPS
IPPPWcs8w68ruuRxEXqFvtUMSBkAdZ5VonEPH31Eh/vUC1fH5RKO2LMm1SS4eHGr
FejQgkD7P6nBwoEPPHetcWa39/13WuuYqlk1YckWlSw/OrhWAUY7iFJl/o5/igbC
12/tmue8h5YWNpY+7wtbXgVWKRXrMpOItYfsHDXKSowN10fz8MZ5f6htSwph/VMp
CIBpJbtiGf6KhDNNsDt/FWjnxaDNRcXLlEuMULxmQnF0ZIAEOfuVafQ=
-----END CERTIFICATE-----]
3. The next command [openssl x509 -in labs/week-04/submissions/convert-formats/leaf_cert.pem -text -noout] produced [Certificate:
    Data:
        Version: 3 (0x2)
        Serial Number:
            b2:4f:f9:3a:99:75:fa:67:0a:45:a4:78:4f:3a:cc:65
        Signature Algorithm: sha256WithRSAEncryption
        Issuer: C=US, O=Google Trust Services, CN=WR2
        Validity
            Not Before: Feb  2 08:36:38 2026 GMT
            Not After : Apr 27 08:36:37 2026 GMT
        Subject: CN=*.google.com
        Subject Public Key Info:
            Public Key Algorithm: id-ecPublicKey
                Public-Key: (256 bit)
                pub:
                    04:d9:c9:fe:15:61:b8:9b:0e:c0:7e:24:b9:5d:e5:
                    e1:46:37:62:b1:77:6c:b9:6f:9c:6b:3d:3b:38:be:
                    aa:58:ab:3e:ee:37:c9:87:14:2a:35:ee:9f:6b:8e:
                    64:83:1e:0c:c7:a5:5d:df:8f:f8:6e:81:d6:aa:0f:
                    68:79:21:96:33
                ASN1 OID: prime256v1
                NIST CURVE: P-256
        X509v3 extensions:
            X509v3 Key Usage: critical
                Digital Signature
            X509v3 Extended Key Usage:
                TLS Web Server Authentication
            X509v3 Basic Constraints: critical
                CA:FALSE
            X509v3 Subject Key Identifier:
                A6:73:09:27:C3:21:55:17:BB:E7:7C:38:5D:ED:05:51:25:00:54:B6
            X509v3 Authority Key Identifier:
                DE:1B:1E:ED:79:15:D4:3E:37:24:C3:21:BB:EC:34:39:6D:42:B2:30
            Authority Information Access:
                OCSP - URI:http://o.pki.goog/wr2
                CA Issuers - URI:http://i.pki.goog/wr2.crt
            X509v3 Subject Alternative Name:
                DNS:*.google.com, DNS:*.appengine.google.com, DNS:*.bdn.dev, DNS:*.origin-test.bdn.dev, DNS:*.cloud.google.com, DNS:*.crowdsource.google.com, DNS:*.datacompute.google.com, DNS:*.google.ca, DNS:*.google.cl, DNS:*.google.co.in, DNS:*.google.co.jp, DNS:*.google.co.uk, DNS:*.google.com.ar, DNS:*.google.com.au, DNS:*.google.com.br, DNS:*.google.com.co, DNS:*.google.com.mx, DNS:*.google.com.tr, DNS:*.google.com.vn, DNS:*.google.de, DNS:*.google.es, DNS:*.google.fr, DNS:*.google.hu, DNS:*.google.it, DNS:*.google.nl, DNS:*.google.pl, DNS:*.google.pt, DNS:*.googleapis.cn, DNS:*.gstatic.cn, DNS:*.gstatic-cn.com, DNS:googlecnapps.cn, DNS:*.googlecnapps.cn, DNS:googleapps-cn.com, DNS:*.googleapps-cn.com, DNS:gkecnapps.cn, DNS:*.gkecnapps.cn, DNS:googledownloads.cn, DNS:*.googledownloads.cn, DNS:recaptcha.net.cn, DNS:*.recaptcha.net.cn, DNS:recaptcha-cn.net, DNS:*.recaptcha-cn.net, DNS:widevine.cn, DNS:*.widevine.cn, DNS:ampproject.org.cn, DNS:*.ampproject.org.cn, DNS:ampproject.net.cn, DNS:*.ampproject.net.cn, DNS:google-analytics-cn.com, DNS:*.google-analytics-cn.com, DNS:googleadservices-cn.com, DNS:*.googleadservices-cn.com, DNS:googlevads-cn.com, DNS:*.googlevads-cn.com, DNS:googleapis-cn.com, DNS:*.googleapis-cn.com, DNS:googleoptimize-cn.com, DNS:*.googleoptimize-cn.com, DNS:doubleclick-cn.net, DNS:*.doubleclick-cn.net, DNS:*.fls.doubleclick-cn.net, DNS:*.g.doubleclick-cn.net, DNS:doubleclick.cn, DNS:*.doubleclick.cn, DNS:*.fls.doubleclick.cn, DNS:*.g.doubleclick.cn, DNS:dartsearch-cn.net, DNS:*.dartsearch-cn.net, DNS:googletraveladservices-cn.com, DNS:*.googletraveladservices-cn.com, DNS:googletagservices-cn.com, DNS:*.googletagservices-cn.com, DNS:googletagmanager-cn.com, DNS:*.googletagmanager-cn.com, DNS:googlesyndication-cn.com, DNS:*.googlesyndication-cn.com, DNS:*.safeframe.googlesyndication-cn.com, DNS:app-measurement-cn.com, DNS:*.app-measurement-cn.com, DNS:gvt1-cn.com, DNS:*.gvt1-cn.com, DNS:gvt2-cn.com, DNS:*.gvt2-cn.com, DNS:2mdn-cn.net, DNS:*.2mdn-cn.net, DNS:googleflights-cn.net, DNS:*.googleflights-cn.net, DNS:admob-cn.com, DNS:*.admob-cn.com, DNS:*.gemini.cloud.google.com, DNS:googlesandbox-cn.com, DNS:*.googlesandbox-cn.com, DNS:*.safenup.googlesandbox-cn.com, DNS:*.gstatic.com, DNS:*.metric.gstatic.com, DNS:*.gvt1.com, DNS:*.gcpcdn.gvt1.com, DNS:*.gvt2.com, DNS:*.gcp.gvt2.com, DNS:*.url.google.com, DNS:*.youtube-nocookie.com, DNS:*.ytimg.com, DNS:ai.android, DNS:android.com, DNS:*.android.com, DNS:*.flash.android.com, DNS:g.cn, DNS:*.g.cn, DNS:g.co, DNS:*.g.co, DNS:goo.gl, DNS:www.goo.gl, DNS:google-analytics.com, DNS:*.google-analytics.com, DNS:google.com, DNS:googlecommerce.com, DNS:*.googlecommerce.com, DNS:ggpht.cn, DNS:*.ggpht.cn, DNS:urchin.com, DNS:*.urchin.com, DNS:youtu.be, DNS:youtube.com, DNS:*.youtube.com, DNS:music.youtube.com, DNS:*.music.youtube.com, DNS:youtubeeducation.com, DNS:*.youtubeeducation.com, DNS:youtubekids.com, DNS:*.youtubekids.com, DNS:yt.be, DNS:*.yt.be, DNS:android.clients.google.com, DNS:*.android.google.cn, DNS:*.chrome.google.cn, DNS:*.developers.google.cn, DNS:*.aistudio.google.com
            X509v3 Certificate Policies:
                Policy: 2.23.140.1.2.1
            X509v3 CRL Distribution Points:
                Full Name:
                  URI:http://c.pki.goog/wr2/oQ6nyr8F0m0.crl

            CT Precertificate SCTs:
                Signed Certificate Timestamp:
                    Version   : v1 (0x0)
                    Log ID    : 16:83:2D:AB:F0:A9:25:0F:0F:F0:3A:A5:45:FF:C8:BF:
                                C8:23:D0:87:4B:F6:04:29:27:F8:E7:1F:33:13:F5:FA
                    Timestamp : Feb  2 09:36:40.442 2026 GMT
                    Extensions: none
                    Signature : ecdsa-with-SHA256
                                30:44:02:20:4C:73:FD:FD:5C:B9:A7:2E:E6:EF:95:D2:
                                A3:FF:54:81:6F:9C:77:90:43:C5:98:0F:D8:10:EE:A9:
                                A3:E0:4E:14:02:20:4B:F7:CE:1B:AF:CC:64:E9:EA:87:
                                01:4B:C3:BA:B0:96:72:4C:FB:E3:6C:E7:DA:4C:CE:F3:
                                2C:A2:B8:80:A7:56
                Signed Certificate Timestamp:
                    Version   : v1 (0x0)
                    Log ID    : 96:97:64:BF:55:58:97:AD:F7:43:87:68:37:08:42:77:
                                E9:F0:3A:D5:F6:A4:F3:36:6E:46:A4:3F:0F:CA:A9:C6
                    Timestamp : Feb  2 09:36:40.454 2026 GMT
                    Extensions: none
                    Signature : ecdsa-with-SHA256
                                30:45:02:21:00:CF:18:C5:5A:5A:86:F8:7E:A2:EB:C3:
                                54:29:C0:75:30:83:E8:E1:7A:24:C7:45:AF:7B:A6:6E:
                                BE:3F:9A:B7:39:02:20:0E:6C:10:7E:97:A0:8C:F5:2F:
                                7B:BC:A2:28:46:C2:21:04:0A:33:0E:E5:7A:AD:FF:EE:
                                B1:64:53:E5:F1:8F:E6
    Signature Algorithm: sha256WithRSAEncryption
    Signature Value:
        8e:49:41:e6:7b:64:b8:7b:a2:29:2c:dd:0c:52:61:dd:ba:f3:
        a0:f2:54:e0:d9:93:87:e7:cc:c4:b2:a4:af:21:fb:47:e1:f0:
        fb:12:11:44:69:d8:93:b0:7b:ea:49:2f:7a:d9:af:70:c3:97:
        44:dd:a7:64:48:61:a8:01:a4:d3:36:ff:d0:57:80:e3:d2:20:
        f3:cf:59:cb:3c:c3:af:2b:ba:e4:71:11:7a:85:be:d5:0c:48:
        19:00:75:9e:55:a2:71:0f:1f:7d:44:87:fb:d4:0b:57:c7:e5:
        12:8e:d8:b3:26:d5:24:b8:78:71:ab:15:e8:d0:82:40:fb:3f:
        a9:c1:c2:81:0f:3c:77:ad:71:66:b7:f7:fd:77:5a:eb:98:aa:
        59:35:61:c9:16:95:2c:3f:3a:b8:56:01:46:3b:88:52:65:fe:
        8e:7f:8a:06:c2:d7:6f:ed:9a:e7:bc:87:96:16:36:96:3e:ef:
        0b:5b:5e:05:56:29:15:eb:32:93:88:b5:87:ec:1c:35:ca:4a:
        8c:0d:d7:47:f3:f0:c6:79:7f:a8:6d:4b:0a:61:fd:53:29:08:
        80:69:25:bb:62:19:fe:8a:84:33:4d:b0:3b:7f:15:68:e7:c5:
        a0:cd:45:c5:cb:94:4b:8c:50:bc:66:42:71:74:64:80:04:39:
        Fb:95:69:f4] 
Identifying Certificate Data, X509v3 extensions, Authority Information Access, X509v3 Subject Alternative Name, Certificate Policies, Distribution Points, CT Precertificate SCTs, and sha256 information allowed me to explore the difference between the .der and .pem naturally. 
4. Managing different conversion formats proved itself distinctly within the command [diff labs/week-04/submissions/convert-formats/leaf_cert.pem labs/week-04/submissions/convert-formats/leaf_cert_restored.pem] with an output [ 
InputObject                                                     SideIndicator
-----------                                                     -------------
labs/week-04/submissions/convert-formats/leaf_cert_restored.pem =>
labs/week-04/submissions/convert-formats/leaf_cert.pem          <=] displaying key transports suited to encrypt objects and indicators. The converted command [openssl genrsa -out labs/week-04/submissions/convert-formats/test_key.pem 2048] alongside [openssl req -new -x509 -key labs/week-04/submissions/convert-formats/test_key.pem -out labs/week-04/submissions/convert-formats/test_cert.pem -days 365 -subj "/CN=Week4-Lab-Test/O=CVI/C=US" and openssl pkcs12 -info -in labs/week-04/submissions/convert-formats/test_bundle.pfx -noout] with an output of password requirements for both export and import.

5. Finally, with an output encryption of information [MAC: sha256, Iteration 2048
MAC length: 32, salt length: 16
PKCS7 Encrypted data: PBES2, PBKDF2, AES-256-CBC, Iteration 2048, PRF hmacWithSHA256
Certificate bag
PKCS7 Data
Shrouded Keybag: PBES2, PBKDF2, AES-256-CBC, Iteration 2048, PRF hmacWithSHA256] providing additional details of the certificate's confidentiality.

---

## Results
Include the important outputs or findings from the lab.

- The .pem file provided the cert output in its original format, but the .der format provides a pop-up window with the details of the certificate, utilizing three tabs to deliver the information.
- The results of the .der file produced a Windows box of the certificate information.
- The conversions PEM → DER → PEM produced a binary code for DER, then back to readable side a file entitled .pemrestored displays the Windows-created certificate back to its original text editor file.
- Once the PFX was verified, the following output was displayed:
MAC: sha256, Iteration 2048
MAC length: 32, salt length: 16
PKCS7 Encrypted data: PBES2, PBKDF2, AES-256-CBC, Iteration 2048, PRF hmacWithSHA256
Certificate bag
PKCS7 Data
Shrouded Keybag: PBES2, PBKDF2, AES-256-CBC, Iteration 2048, PRF hmacWithSHA256

---

## Key Findings
Document the most important observations from the lab.

• The hash-based message authentication code with the SHA256.
• The alignment between PKCS7 Encrypted data and Shrouded Keybag verifies the Certificate bag.
• I noticed the cryptographic security mechanisms in concert throughout the cert transitions.

---

## Explanation
Explain why the results matter.

- The PFX requires a password to confirm the confidentiality of the private key. 
- Distributing symmetric keys generally comes in the form of a PEM file, which is used for Linux platforms, a DER file is used for Java applications, and a PFX file would be used for Windows.
Exposing private keys is harmful to all security infrastructures.

---

## Challenges / Troubleshooting
Error:
-in labs/week-04/submissions/convert-formats/leaf_cert.pem \
-in : The term '-in' is not recognized as the name of a cmdlet, function, script file, or operable program. Check the spelling of the name, or if a path was included,
verify that the path is correct and try again.
At line:1 char:3
+   -in labs/week-04/submissions/convert-formats/leaf_cert.pem \
+   ~~~
    + CategoryInfo          : ObjectNotFound: (-in:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException

Resolve:
The solution was tied to identifying the correct path of the submissions folder. Once the path was corrected all other commands outputted correctly.
---

