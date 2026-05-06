# Lab 01: Environment Verification & VM Connectivity Check

**Student Name: Alex B.
**Date Completed: 5/5/26
**Phase:** 2 | **Week:** 9  
**Submission Path:** `labs/week-09/lab-01-environment-verification.md`

---

## Step 1 – VM Startup & Login

**VMs started in correct order (DC01 → PKI-SRV01 → Root-CA):**
- [ X ] Yes
- [ ] No — describe what happened:

**Login credentials used:**

| VM | Account Used | Login Successful? |
|----|-------------|-------------------|
| DC01 | CORP\pki.admin | Yes / No |
| PKI-SRV01 | CORP\pki.admin | Yes / No |
| Root-CA | .\Administrator | Yes / No |

**Notes / issues encountered:**

Password for Root-CA is incorrect.

---

## Step 2 – VM Connectivity Test

**Command run on PKI-SRV01:**

```powershell
Test-Connection -ComputerName DC01 -Count 2
```

**Output received:
Source        Destination     IPV4Address      IPV6Address                Bytes    Time(ms)
------        -----------     -----------      -----------                              -----    --------
PKI-SRV01     DC01            192.168.10.10                                             32       3
PKI-SRV01     DC01            192.168.10.10                                             32       1



```

**DC01 responded successfully:**
- [X] Yes
- [ ] No — troubleshooting steps taken:

---

## Step 3 – CertSvc Service Status

**Command run on PKI-SRV01:**

```powershell
Get-Service -Name CertSvc
```

**Output received:

```
Status   Name       DisplayName
------   ----               -----------
Running  CertSvc  Active Directory Certificate Services

```

**CertSvc status shown:   Active Directory Certificate Services

**Service was Running:**
- [X] Yes
- [ ] No — action taken:

---

## Step 4 – Certification Authority Console

**Steps completed on PKI-SRV01:**
- [X] Opened certsrv.msc via Run dialog
- [X] Confirmed CA name visible: CVI Issuing CA 1
- [X] Confirmed CA status: Running
- [X] Expanded left pane — folders visible (Revoked Certificates, Issued Certificates, etc.)

**Screenshot or description of what you observed in certsrv.msc:**

```

```

---

## Step 5 – Certificate Log File Path

**Command run on PKI-SRV01:**

```powershell
Get-ChildItem "C:\Windows\System32\CertLog"
```

**Output received:**

```
Mode                 LastWriteTime         Length	 Name
----                 -------------        		 ------ 	----
-a----          5/5/2026   8:17 PM        1048576 CVI Issuing CA 1.edb
-a----          5/5/2026   8:17 PM          16384 CVI Issuing CA 1.jfm
-a----          5/5/2026   8:17 PM           8192 edb.chk
-a----          5/5/2026   8:18 PM        1048576 edb.log
-a----         4/25/2026   7:45 PM        1048576 edbres00001.jrs
-a----         4/25/2026   7:45 PM        1048576 edbres00002.jrs
-a----         4/25/2026   7:45 PM        1048576 edbtmp.log
-a----          5/5/2026   8:17 PM          20480 tmp.edb

```

**Files found in CertLog:**

| File Name | Approximate Size |
|-----------|-----------------|
|CVI Issuing CA 1.edb |1048576 |
|CVI Issuing CA 1.jfm |16384 |
|edb.chk |8192 |
|edb.log |1048576 |
|edbres00001.jrs |1048576 |
|edbres00002.jrs |1048576 |
|edbtmp.log |1048576 |
|tmp.edb |20480 |
---

## Reflection

**One thing that went well during this lab:**

```
One thing that stood out was how flawless the VM deployments were.
```

**One thing that was confusing or unexpected:**

```
To date the password for the Root-CA, but I’m sure it will be a simply fix.
```

---

## Submission Checklist

- [X] All five steps completed
- [X] All command outputs pasted
- [X] Reflection section filled in
- [X] File saved as `lab-01-environment-verification.md`
- [X] File committed to my portfolio repo under `labs/week-09/`

