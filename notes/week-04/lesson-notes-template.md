Week 4 Lesson Notes — Certificate Formats and Trust Stores

1. Core Concept
Certificate operations convert to build out a full chain when verifying with OpenSSL. A certificate conversion is a change control meant to preserve information. 

2. Why It Matters
Knowing how to convert a certificate between formats invites the process to convert, re-parse fields, and verify round-trip integrity. When Active Directory deployment is being pushed to different computer models across an organization, it requires the skill of certificate conversion for each system.


3. Technical Breakdown
Components

Convert a certificate
Locate and inspect the trust store
Install a self-signed root CA
Remove the test root CA


4. Common Misconceptions
Misconception 1- PEM, DER, and PFX are different kinds of certificates.
Misconception 2- If a certificate is valid, the system will trust it.

5. Where This Shows Up
In cloud environments, PEM is most common in cloud load balancers, DER can be found in Java, and PFX shows up when importing certs into Windows. Windows enterprise integration will require a package with cert + key + chin into a PFX package.
