# Week 01 Mini Lab — Trust Chain Validation

## Screenshot Evidence

assets/screenshots/week-01/trust-chain-validation.png

![Trust Chain Validation](../../assets/screenshots/week-01/trust-chain-validation.png)


## Website Information

**Website inspected:**  
(https://www.jpmorganchase.com/)

---

## Certificate Chain Breakdown

**Leaf (Server) Certificate**  
cws-main-akamai.jpmorgan.com

**Intermediate Certificate Authority**
DNS Certification Authority Authorization (CAA) Policy found for this domain.
(CAA creates a DNS mechanism that enables domain name owners to whitelist CAs that are allowed to issue certificates for their hostnames. It operates via a new DNS resource record (RR) called CAA (type 257)-https://blog.qualys.com/product-tech/2017/03/13/caa-mandated-by-cabrowser-forum?_ga=2.74040722.1089718678.1773037566-810447417.1773037566)

**Root Certificate Authority (Trust Anchor)**
	DigiCert Global Root G2

---

## Trust Anchor Verification

The Root CA is marked as trusted by the system because
Windows 

---

## Observations

Document three observations about the certificate.

### Observation 1
Operating a digital trust using a production system algorithm in the chain of trust is what I observed. Next, analyze the process of inventory to see how the path begins from the main domain. As it proceeded to the server, it was moved to the CA, where it ended at the trust store, Global Root G2.

### Observation 2
The evidence of verification was self-signed and followed the CAA policy. 

### Observation 3
As for the browser trust jpmorganchase.com utilizes:
Forward Secrecy	Yes (with most browsers), and also identified "This site works only in browsers with SNI support.

---
## Reflection
- The Root certificate is called a trust anchor because parsing SAN confirms gostnames and blocks the SAN if anything is missing or wrong.
Therefore, verifying  contract identity to solidify the handshake taking place. Within a strict PKI environment (a financial system, for example)
The Root certificate adds security of CAA for additional security and removal of any mishaps that could happen on the CA's end.
- 
- Validation of the certificate chain is like managing logistics. Confirming who issued it, who vouches for the invoice, and what policy constraints it entails.
- The details of the validation walk look like this:
1	Sent by server	cws-main-akamai.jpmorgan.com
2	Sent by server	DigiCert EV RSA CA G2
3	In trust store	DigiCert Global Root G2   Self-signed
  
- If the Root CA were not trusted, the validation conditions would no longer be evaluated.
