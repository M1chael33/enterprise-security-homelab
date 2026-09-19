# Active Directory & Core Infrastructure

## Domain Controller

I installed Windows Server 2025 and configured it as `project-x-dc` with the static address:

```
10.0.0.5/24
```

I created the Active Directory forest:

```
corp.project-x-dc.com
```

with the NetBIOS domain:

```
CORP
```

## Roles I Configured

I installed and configured:

- Active Directory Domain Services
- DNS
- DHCP
- IIS
- File and Storage Services

## DNS and DHCP

I used the domain controller as the internal DNS server for domain-joined systems and configured DNS forwarding for outside name resolution when needed.

I created a DHCP scope covering:

```
10.0.0.100 - 10.0.0.200
```

with the lab gateway at `10.0.0.1` and the domain controller as the DNS server.

## Windows Client

I installed a Windows 11 Enterprise workstation and joined it to the CORP domain. I practiced domain authentication, remote administration, WinRM, and RDP-related configuration.

## Linux Client

I joined an Ubuntu workstation to Active Directory using Samba and Winbind. I configured:

- realm and Kerberos settings
- Samba ADS security mode
- Winbind
- NSS integration
- PAM home directory creation
- SSH

I verified that domain users could be resolved and authenticated from Linux.

## What I Learned

This portion gave me practical experience with the infrastructure a SOC analyst is expected to understand. It also made later attack activity easier to interpret because I knew how the environment was supposed to behave before I attacked it.
