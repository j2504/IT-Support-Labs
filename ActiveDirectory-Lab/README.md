# 🖥 Active Directory Lab

## 🎯 Objective
Deploy a Windows Server domain controller in a virtual lab, configure Active Directory Domain Services (AD DS), create and manage users/groups, and apply Group Policy Objects (GPOs) — mirroring the IBM IT Support course environment.

---

## 🛠 Tools & Environment
- **Virtualization:** Oracle VirtualBox 7.x
- **Server OS:** Windows Server 2022 Evaluation
- **Client OS:** Windows 10 Pro Evaluation
- **Roles/Features:** Active Directory Domain Services, DNS Server
- **Network:** Internal VirtualBox network for domain communication

---

## 📝 Steps

### 1. Prepare the Environment
1. Download Windows Server 2022 and Windows 10 ISOs from Microsoft Evaluation Center.
2. Create two VMs in VirtualBox:
   - **Server-DC01**: 2 vCPU, 4GB RAM, 60GB disk
   - **Client-PC01**: 2 vCPU, 2GB RAM, 40GB disk
3. Configure both VMs on the same **Internal Network** in VirtualBox.

---

### 2. Install & Configure AD DS
1. On **Server-DC01**, open **Server Manager** → *Add Roles and Features*.
2. Select **Active Directory Domain Services** and **DNS Server**.
3. After installation, click the yellow flag in Server Manager → *Promote this server to a domain controller*.
4. Create a new forest:
   - **Root domain name:** `lab.local`
   - Set DSRM password.
5. Restart the server to complete promotion.

---

### 3. Create Organizational Units (OUs)
1. Open **Active Directory Users and Computers**.
2. Create OUs:
   - `Lab Users`
   - `Lab Computers`
   - `IT Dept`
3. Move the default **Administrator** account into `IT Dept`.

---

### 4. Add Users & Groups
1. In `Lab Users`, create:
   - `John Smith` (IT Support)
   - `Jane Doe` (HR)
2. Create a **Security Group**: `IT_Admins`.
3. Add `John Smith` to `IT_Admins`.

---

### 5. Apply Group Policy Objects (GPOs)
1. Open **Group Policy Management**.
2. Create a new GPO: `PasswordPolicy`.
3. Configure:
   - Minimum password length: 10
   - Password must meet complexity requirements: Enabled
4. Link GPO to the domain.

---

### 6. Join Client to Domain
1. On **Client-PC01**, set DNS to the IP of **Server-DC01**.
2. Join domain: `lab.local`.
3. Restart and log in as `John Smith`.

---

## 📸 Screenshots
*(Replace placeholders with your actual screenshots)*
- `01-Server-Manager-ADDS.png` — Installing AD DS role
- `02-Domain-Controller-Promotion.png` — Promote to DC wizard
- `03-OU-Structure.png` — OU layout in ADUC
- `04-User-Creation.png` — New user wizard
- `05-GPO-Settings.png` — Password policy configuration
- `06-Client-Domain-Join.png` — Successful domain join

---

## 📚 Key Takeaways
- Learned how to deploy and configure AD DS in a virtual lab.
- Practiced creating OUs, users, groups, and applying GPOs.
- Understood the importance of DNS in domain environments.
- Gained hands-on experience joining a client machine to a domain.

---

## 🔖 References
- [Microsoft AD DS Overview](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/get-started/virtual-dc/active-directory-domain-services-overview)
- [IBM IT Support Course](https://www.youtube.com/watch?v=BNbPsiCGQzw)
