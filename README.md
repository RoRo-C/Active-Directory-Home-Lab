Enterprise Active Directory & Windows Server Home Lab

A virtualized client-server corporate network built in **Oracle VM VirtualBox** to practice Tier 1 and Tier 2 Desktop Support workflows, Active Directory administration, Group Policy enforcement, and PowerShell automation.

---

Lab Topology

| Hostname | Operating System | Role / Services | IP Configuration |
| :--- | :--- | :--- | :--- |
| **DC01** | Windows Server 2022 Standard | Active Directory Domain Services (AD DS), DNS Server, DHCP Server | Static: `10.10.10.10 /24` |
| **CLIENT01** | Windows 11 Pro | Domain-Joined Workstation (`corp.rochellelab.local`) | Dynamic via DC01 DHCP (`10.10.10.100–200`) |

- Network Adapter: VirtualBox Internal Network (`intnet`) to isolate lab DHCP/DNS services from the host home network.
- Domain Name: `corp.rochellelab.local`

---

## 📂 Organizational Unit (OU) & RBAC Structure

Designed a clean department-based OU hierarchy for delegated administration and targeted Group Policy deployment:

```text
corp.rochellelab.local
└── Corp_Users
    ├── IT_Support   (Security Group: GRP_IT_Support)
    ├── HR           (Security Group: GRP_HR)
    ├── Finance      (Security Group: GRP_Finance)
    └── Operations   (Security Group: GRP_Operations)
