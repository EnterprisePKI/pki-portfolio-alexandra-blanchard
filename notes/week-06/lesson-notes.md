Week 6 Lesson Notes — PKI Incident Diagnosis & Troubleshooting

##1. Core Concept
A PKI Engineer well equipped in OpenSSL troubleshooting skills involves being able to analyze if certs are actually present, if the identity is correct, if the chain is complete and trusted, and if the cert is expired or revoked. 

##2. Why It Matters
The concept matters in real enterprise environments because the engineer must know if the problem is the cert or the deployment of the cert. 

##3. Technical Breakdown
Trust implications
Are found in Web and CDN delivery, API gateways, cloud load balancers, enterprise SSO &IAM, email security, payments, healthcare, and so on.


##4. Common Misconceptions
Misconception 1- PKI problems are just certificate problems.
Misconception 2- TLS issues only happen on websites.

##5. Where This Shows Up
Internal enterprise systems
The first misconception is relevant to deployment and chain problems, not the assumption  of broken cryptography. The second misconception becomes a reality when API gateways, device onboarding, or SSO signing certs are no longer working.  

