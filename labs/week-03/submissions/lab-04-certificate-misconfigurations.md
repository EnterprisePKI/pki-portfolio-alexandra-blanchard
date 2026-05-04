# Lab 04 — Detect Certificate Misconfigurations

## Overview
An infrastructure of operational resilience monitors misconfigurations to avoid TLS failures. Layering fallbacks by identifying failed validations in real-time.
---

## Scenario 1 — Missing Subject Alternative Name

**Would modern browsers trust this certificate?**
Trust certificates are reliant on a SAN extension, or the hostname validation will fail. 

**Analysis:**
TLS connection is tied to a working SAN and CN. if these are not established, the errors (Chrome: NET::ERR_CERT-COMMON_NAME_INVALID) will populate.
---

## Scenario 2 — Incorrect Extended Key Usage

**Would a browser accept this certificate for a web server?**
Extension enforcements requested via key usage guards against permissive or too restrictive certificates. TLS Web Server Authentication is required for HTTPS because a TLS is used for signing (i.e., a digital signature).

**Analysis:**
An output of:
X509v3 Key Usage: critical 
Digital Signature, Key Encipherment
Identifies the EKU as a mandatory enforcement of digital signatures and key encipherment when an RSA key exchange is present.  A website requires an EKU or it would fail with a “not valid for purpose” error message.
---

## Scenario 3 — Expired Certificate

**What happens if this certificate is used today?**
The validity period (Not After:  May 1, 2023) is not valid for today, and the secure connection has ended. The validity of a secure connection works only during the validity window.


**Analysis:**
A closed validity period causes browsers to respond with a hard stop. Browsers' chain of trust relies on predictable  lifecycle management involving monitored inventory, automation, validation rollouts, and ownership.  A user would see an error message displaying the following:
Chrome: NET::ERR_CERT-COMMON_NAME_INVALID).
---

## Scenario 4 — Missing Intermediate Certificate

**Can the browser build a complete trust chain?**
A certificate is not trusted if the issuer is unknown. A private connection is a secure connection in which the message of a security risk is not an issue for an end user. Once a browser is missing an intermediate certificate, the chain of trust is broken, but once the issuer is trusted and the authority is valid, the chain is now valid.

**Analysis:**
Trust is tied by the leaf certificate, which is tied to an intermediate certificate (a bridge between the leaf and root) and the root signing off on the certificate chain loop. A missing intermediate breaks the chain's trust. 
---

## Key Takeaway
What is the most important thing you learned about certificate misconfigurations from this lab?
Relying on the intermediate certificate to confirm a secure handshake is best practice when deploying a continuous chain of safety embedded in a full chain.
