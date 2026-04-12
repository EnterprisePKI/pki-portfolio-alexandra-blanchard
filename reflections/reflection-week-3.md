Week 3 Reflection


Learning how to identify core fields of an X.509 certificate and the differences between root, intermediate, and leaf certificates.

Understanding the concept of API’s, digital signatures, and the looming TLS failures if the certificate lacks what's required under PCI DSS v4.0.

Once inside the Thales Luna HSM, the certified fields operate in real-world systems as follows:

Subject Key Identifier is known as CKA ID
Subject Common Name is listed as CKA Label
Key Usage/EKU is stored as CKA Certificate Category                     
Issuer Hash is listed as an OUID
And the Public Key/Curve operates in the crypto module as ECDSA or RSA.

The best way to explain this topic to a non-technical audience would be to draw on the activity of travel. For example, as you travel to the airport, your passport (x.509) gets you to the airport counter, where the book is signed and allows you to move to the gate. At the gate, your passport book is validated by the information received from the front counter. Once each field is validated, the book is now scanned, in order for you to enter the plane. 

This week, I wonder what the X.509 certs look like on the mobile end?
