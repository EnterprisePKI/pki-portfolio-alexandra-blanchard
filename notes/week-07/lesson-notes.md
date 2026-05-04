Week 7 Lesson Notes — PKI in Enterprise Environments & Your Career Path

##1. Core Concept
Connecting weeks 1 to 6, to operate as an independent PKI engineer in real-time. Operating and applying every skill set learned through each week. Ragom frp, pulling a live cert to produce a certificate profile.

##2. Why It Matters
In a real enterprise environment, everything that can go wrong will go wrong. Understanding the nuance of misconceptions versus PKI’s reality is what makes this skill set important and relevant within an organization.

##3. Technical Breakdown
Flow
In an enterprise infrastructure, knowing the flow/process of the following is relevant as a PKI Engineer.
Diagnosing PKI failures by separating identity errors from trust eros.
Understanding SAN breaks identity, but missing intermediate elements breaks trust.
Or how AES protects the payload, PKI is set up to solidify the handshake, while governance is in place to protect the company. 


##4. Common Misconceptions
Misconception 1- Hashing and signing certificates are the same thing.
Misconception 2- if it works across one OS and one browser, it will work across all trust stores. 

##5. Where This Shows Up
Internal enterprise systems

It is quite possible for a chain to verify on a laptop but fail during deployment. To curtail the process, the production involves a process where the same network path is tested with the same TLS layer and the same trust anchors.
