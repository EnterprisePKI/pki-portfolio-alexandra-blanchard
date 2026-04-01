# Week X Lesson Notes — [Topic Title]

## 1. Core Concept

Explain the foundational concept clearly and practically.

---

## 2. Why It Matters

How this concept appears in real enterprise environments.


m trust store by default. This should be noted in your write-up — it is not a failure, but it does reflect an important distinction between OpenSSL trust and the Windows trust store.




. The lab began with entering the command [openssl s_client -connect google.com:443 -showcerts] with the input as [Connecting to 2607:f8b0:400a:800::200e
CONNECTED(000001FC)
depth=2 C=US, O=Google Trust Services LLC, CN=GTS Root R1
verify error:num=20:unable to get local issuer certificate
verify return:1
depth=1 C=US, O=Google Trust Services, CN=WR2
verify return:1
depth=0 CN=*.google.com
verify return:1

---

## 3. Technical Breakdown

- Definition
- Components
- Flow
- Trust implications

---

## 4. Common Misconceptions

- Misconception 1
- Misconception 2

---

## 5. Where This Shows Up

- Web security
- Internal enterprise systems
- Cloud environments
- DevOps workflows

---

## Mental Model

Short summary that ties the week back to:

Identity + Trust + Verification
