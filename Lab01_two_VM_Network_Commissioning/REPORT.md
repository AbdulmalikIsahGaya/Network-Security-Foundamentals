## Network Configuration and Connectivity Report

**Student Name:** Abdulmalik Isah Gaya  
**Student ID:** C11/26/FCDF/17171  
**Date:** October 5, 2026  
**Operating System:** Kali Linux 6.18.12+kali-amd64  
**Host Name:** Kali  

---

## 1. Overview

This report documents the configuration, testing, and troubleshooting of the network environment used in the Advanced Web Application Security Labs. The lab involved the OPNsense firewall and the Linux client VM, with the goal of establishing working communication between the firewall, internal LAN, and external network.

The network design included:
- OPNsense firewall as the gateway and security appliance
- Client machine connected to the internal network segment
- NAT interface for connectivity to an external network
- Internal LAN segment for secure communication between lab systems

---

## 2. Initial System State

At the beginning of the exercise, both virtual machines were shut down:
- `icdfa-nslab-firewall`
- `icdfa-nslab-client`

The firewall and client machines were then opened in VMware and reconfigured as follows:

### Firewall Configuration
- Adapter 1: Connected to external network (NAT)
- Adapter 2: Connected to internal network segment (`ICDFA-LAN`)
- Verified: Cable connected option enabled

### Client Configuration
- Adapter 1: Connected to internal network segment (`ICDFA-LAN`)
- Verified: Cable connected option enabled

---

## 3. Problem Identified During Firewall Startup

After powering on the firewall, the OPNsense console was checked. It was confirmed that:
- LAN interface was marked as active
- WAN interface was not marked as active

This suggested that the firewall was not properly attached to the correct network segment for the internal lab network.

To validate the issue, the following command was used on the firewall:

```bash
ip -4 -br address
