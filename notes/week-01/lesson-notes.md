Week 1 Lesson Notes — Digital Trust & Identity
1. Core Concept
Digital Trust & Identity are the fundamental components of PKI’s infrastructure. It involves a system involving a public key (public-facing), a private key (placed in safekeeping), along with the non-negotiable steps for encryption (for security), and a chain of trust for protocol. 

2. Why It Matters
In a stringent enterprise, where a strict certificate lifestyle is mandatory it top priority is to operate through cryptography, policy, and verification. Enterprises in industries such as Grid Operators, DOD, or Telecom services each depend greatly on the fundamental components of these weeks as it demands an ongoing, audit-level of attention. Missing the alignment of a cert's identity, authentication, or authorization can trigger regulatory fines and disrupt enterprise services.

3. Technical Breakdown
Definition
1. A digital trust encompasses the CIA (Confidentiality, Integrity, and Identity)  of a PKI networking system.
2. Identity is who the entity is, what it is, as it presents itself through the PKI system.
3. Authentication is expected as it validates through two pieces of information (i.e., identity and a key).
4. Authorization is what the entity has access to as it moves through the certificate lifecycle.
5. A private key must be kept safe since it is used to sign or decrypt information. 
6. A public key is safe enough for it to be used in the form of signature verification or encryption.
7. A digital certificate binds the public key to the subject, while also being verified by the Central Authority.
8. Encryption protects data in transit and at rest.  

Components
Digital Signature- Digitally signed by a CA
Encryption- Data conversion requiring a ciphertext to decode
Identity- Certificate Subject DN
Authentication- TLS handshake
Authorization- IAM policies



Flow
Public Key-used to verify digital signature
Private Key- is paired with the public key through a secret set of numbers
Encryption- private key decrypts server data
Identity- Presents itself as a certificate or username
Authentication- system verification takes place with a public or private key
Authorization- where permissions are blocked or permitted 


Trust implications
The risk involved if an identity is compromised is that it jeopardizes the entire chain of trust. If authorization is not validated, an enterprise will face a data breach. If authentication is not verifies then any identity can pass through and bypass permissions.

4. Common Misconceptions
Misconception 1: Automation will streamline all fail-safe measures without an assigned agent to oversee the system.
Misconception 2: PKI is assigned to a certain group of technical infrastructures.

5. Where This Shows Up
Web security- It still must identify itself to a CA to tell the surveillance system ti is reliable to continue its service.
Internal enterprise systems must honor the TLS handshake to fully operate in the correct group policy.
Cloud environments operate using short-lives cert to monitor traffic securely.
DevOps workflows  still operate under the need of having a hash assigned to the certs to allow the public and private key to operate behind the scene for trustworthy communication to take place. 

Identity + Trust + Verification
Identity is declared (CN), a trust anchor (CA) asserts the presented identity, and verification is enforced before the certificate can move up the chain.
