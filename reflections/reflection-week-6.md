Week 6 Reflection

##What did you learn this week?

This week's focus was geared towards a PKI engineer applying a skill set gained from the prior weeks of training. Analyzing a PKI failure and implementing OpenSSL commands to operate with a PKI Incident Diagnosis & Troubleshooting skillset.

##What concept was most challenging?

##This week’s concept wasn’t as challenging as the OpenSSL commands. For example, certain changes were required to the command to collect the write output 
(openssl s_client -connect wrong.host.badssl.com:443 -servername wrong.host.badssl.com </dev/null 2>/dev/null | openssl x509 -outform PEM > mismatch_cert.pem
(The above line is for Linux = the line below is for OpenSSL/Windows.)
openssl s_client -connect wrong.host.badssl.com:443 -servername wrong.host.badssl.com $null 2>$null | openssl x509 -outform PEM > mismatch_cert.pem0.


##Where does this concept appear in real-world systems?
Knowing how to identify what a TLS Validation failure means and where in the chain of trust it breaks becomes important when solving what is missing. When handshake-failures occur on a wide scale it is important to understand the symptoms and the applicable solutions to remove an enterprise-wide outage.

##How would you explain this topic to a non-technical audience?
In a PKI, a failure is like arriving at the door, and security won't let you in because your badge is missing a barcode and cannot be verified. Once security identifies, trust, and verifies the new  barcode, then you are allowed to enter the building.

##What questions remain?
Is there such a thing as all PKI outages not happening because of a solid fail-safe system?  
