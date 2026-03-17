
Scenario 1 — Missing Subject Alternative Name
A certificate contains the following information:

Subject: CN=example.com

However, the certificate does not contain a Subject Alternative Name (SAN) extension.

Question

Would modern browsers trust this certificate?

Analysis

Explain:

Why modern browsers require SAN
Why the Common Name alone is no longer sufficient
Scenario 2 — Incorrect Extended Key Usage
A certificate contains the following extension:

Extended Key Usage: Client Authentication

The certificate is being used on a web server for HTTPS.

Question
Would a browser accept this certificate for a web server?

Analysis
Explain:

What Extended Key Usage defines
Why the correct EKU is required for TLS servers
Scenario 3 — Expired Certificate
The certificate validity period shows:

Not Before: May 1 2022 Not After: May 1 2023

The current date is after May 1, 2023.

Question
What happens if this certificate is used today?

Analysis
Explain:

Why expiration causes TLS validation to fail
Why certificate lifecycle management is critical
Scenario 4 — Missing Intermediate Certificate
A server presents a certificate during a TLS handshake, but the intermediate certificate is not included in the chain.

Question
What error would a browser likely display?

Analysis
Explain:

How certificate chains establish trust
Why intermediate certificates must be provided by servers
Part 4 — Observations
Your misconfiguration-analysis.md file should explain:

Why each certificate configuration fails
What TLS validation rule is being violated
How the issue could be fixed
