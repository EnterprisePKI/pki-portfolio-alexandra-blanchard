# My PKI Toolkit
**CVI PKI Career Pathway — Phase 1 Foundations**
Completed: April 2026

---

## About This Document

The PKI Toolkit is a collection of commands used from weeks 1 to 6 that were submitted. Referencing the toolkit will be advantageous for the upcoming phases.

---

## Core Command-Line Tools

openssl x509

What it does:
Reads and prints X.509 certificate details (subject, issuer, dates, SAN, EKU, AIA/OCSP, CRL, etc.).

When to use it:

You have a .pem/.crt and need to see what it actually contains.
You’re troubleshooting SAN/EKU/expiry/issuer chain details.

Example command from my labs:

openssl x509 -in leaf_cert.pem -noout -text

What the output tells you:

Identity: Subject + SAN (what hostnames it’s valid for)
Trust: Issuer + AIA (who signed it / where intermediates + OCSP live)
Time: Not Before / Not After (expired or not)
Allowed use: Key Usage + EKU (serverAuth vs clientAuth)
openssl s_client

What it does:
Opens a live TLS connection to a server and shows what certificate chain the server actually presents.

When to use it:

You need to confirm what cert the server/CDN/load balancer is serving right now.
You’re diagnosing an incomplete chain, hostname mismatch, or TLS version/cipher behavior.

Example command from my labs:

'' | openssl s_client -connect github.com:443 -servername github.com -showcerts 2>$null

What the output tells you:

Presented chain: leaf + intermediates (often not the root)
Verify result: “unable to verify first certificate” indicates missing intermediates/trust anchor
TLS negotiation: protocol, cipher suite, and handshake notes
openssl req

What it does:
Creates and inspects CSRs (Certificate Signing Requests).

When to use it:

You’re generating a CSR to request a cert from a CA.
You want to confirm the CSR contains the correct Subject + SAN before issuance.

Example command from my labs:

openssl req -in test_csr.pem -noout -text

What the output tells you:

Subject fields you asked the CA to certify (CN/O/OU/etc.)
Public key details (RSA size / EC curve)
Requested SANs (critical for modern browsers)
Proof-of-possession (CSR signature proves you control the private key)
openssl verify

What it does:
Verifies a certificate chain against a trust anchor (root) and optional intermediates.

When to use it:

You’re confirming leaf→intermediate→root chain correctness.
You’re debugging “unknown issuer / incomplete chain” failures.

Example command from my labs:

openssl verify -CAfile root.pem -untrusted intermediate.pem server.pem

What the output tells you:

server.pem: OK → chain is complete and trusted
error 20 → missing issuer/intermediate
error 7 → wrong issuer (signature failure)
error 10 → certificate expired
error 18 → self-signed but not trusted
openssl ocsp

What it does:
Queries an OCSP responder for revocation status of a specific certificate (good/revoked/unknown).

When to use it:

You need real-time revocation status for a leaf cert.
You’re validating that the OCSP URL from AIA works and responses verify.

Example command from my labs:

openssl ocsp -issuer issuer_cert.pem -cert leaf_cert.pem -url $OCSP_URL -resp_text -no_nonce

What the output tells you:

leaf_cert.pem: good / revoked / unknown
This Update / Next Update (freshness window)
Responder Error: unauthorized (6) often means wrong issuer, nonce policy, or responder constraints
openssl pkcs12

What it does:
Creates or extracts PKCS#12 (.pfx/.p12) bundles that can contain a private key + cert + chain.

When to use it:

You need to import into Windows/IIS some enterprise apps or device stores.
You need to package leaf + private key + intermediates into one file.

Example command from my labs:

openssl pkcs12 -export -out bundle.pfx -inkey server.key -in server.crt -certfile intermediate.pem

What the output tells you:

If the export succeeds, your bundle contains the right materials for import
If import fails later, it’s often due to a missing chain, a wrong password, or key mismatch
---

## Network and Inspection Tools

curl.exe

What it does:
Makes HTTP/HTTPS requests and prints response headers/body (great for CDN/proxy detection).

When to use it:

You want to see HTTP headers (server, cache, CDN hints, redirects).
You need a quick “is the website responding and how?”

Example command from my labs:

curl.exe -sIL https://www.salesforce.com | Select-String -Pattern '^(server:|via:|x-cache:|cf-ray:|x-amz)' -CaseSensitive:$false

What the output tells you:

server: often hints CDN/provider (AkamaiGHost, Cloudflare, CloudFront, etc.)
via: indicates proxies/cache layers in the path
x-cache: shows cache HIT/MISS behavior
cf-ray: indicates Cloudflare and the POP
x-amz-* indicates AWS/CloudFront involvement
ping

What it does:
Checks basic network reachability using ICMP.

When to use it:

You suspect a host is offline or unreachable from your network.
You want a fast “can I reach it at all?” test (note: ICMP may be blocked).

Example command from my labs:

ping github.com

What the output tells you:

Success + latency (ms) suggests the host/network path is reachable
Failure can mean a host down, a routing issue, or an ICMP blocked (not always TLS-related)
tracert (Windows) / traceroute (Linux/macOS)

What it does:
Shows the network hops between you and the destination.

When to use it:

You suspect routing issues, regional blocks, or a proxy/VPN altering paths.
You want to see where packets stop (e.g., corporate firewall).

Example command from my labs:

tracert github.com

What the output tells you:

Each hop is a router along the path
Timeouts show where traffic may be blocked or deprioritized
Useful for “why can’t my OCSP/CRL endpoint be reached?”
mtr (Linux/macOS/WSL)

What it does:
Combines ping + traceroute continuously to show loss and latency over time.

When to use it:

You have intermittent connectivity or packet loss affecting TLS handshakes.
You need evidence that a mid-path network hop is unstable.

Example command from my labs:

mtr -rw github.com

What the output tells you:

Packet loss by hop (where reliability breaks)
Latency trends (jitter) that can cause TLS timeouts and OCSP failures
Get-ChildItem (PowerShell)

What it does:
Lists files/folders—PowerShell equivalent of ls.

When to use it:

You’re getting “No such file” from OpenSSL and need to confirm what’s actually there.
You want to verify naming (e.g., .pem vs .pem.txt) and sizes.

Example command from my labs:

Get-ChildItem -Force *.pem | Select-Object Name,Length

What the output tells you:

Confirms the certificate files exist in your current directory
File size hints: a real PEM cert is usually ~1–3 KB; empty/invalid files stand out fast
Invoke-WebRequest (PowerShell)

What it does:
PowerShell-native HTTP client (often aliased as curl in PowerShell).

When to use it:

You want structured headers without relying on curl syntax.
You need to download an intermediate cert from CA Issuers URI.

Example command from my labs:

Invoke-WebRequest -Uri "http://crt.comodoca.com/COMODORSADomainValidationSecureServerCA.crt" -OutFile intermediate.der

What the output tells you:

The file was downloaded (check size + timestamp)
You can then convert DER→PEM with OpenSSL and complete your chain verification workflow
Select-String (PowerShell)

What it does:
PowerShell’s built-in “grep”—searches text streams for patterns and can show context.

When to use it:

You need to pull specific lines from OpenSSL output (SAN, AIA, verify codes).
You’re filtering headers from curl/OpenSSL without Bash tools.

Example command from my labs:

openssl x509 -in leaf_cert.pem -noout -text | Select-String -Pattern 'Subject Alternative Name' -Context 0,5

What the output tells you:

Shows SAN entries (DNS names), which determine whether browsers accept the cert for a hostname
-Context gives the extra lines beneath the matching header, like grep -A5



---

## Reference and Analysis Services

### SSL Labs SSL Server Test
<img width="1138" height="690" alt="SSL Labs Analysis" src="https://github.com/user-attachments/assets/3e981c27-c58f-4cf6-957a-6695d48d468f" />


### crt.sh — Certificate Transparency Search
<img width="307" height="122" alt="crt sh" src="https://github.com/user-attachments/assets/185803e4-05f3-4b09-af69-a7144ae285a7" />


---

## Phase 1 Skills Summary

I’ve worked on live certificates, identified TLS terminations, analyzed certificates in
every layer, and determined how they align with their corresponding OpenSSL commands. Another skill set developed over the 
last few weeks involved modifying every command to set it up to provide the correct output. Improving the ability to debug via capturing, parsing, validating, remediating, and/or re-validating eliminates surprises and supports a trust proof certificate deployment.

