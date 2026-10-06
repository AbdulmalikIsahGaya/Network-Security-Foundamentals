## Project Title
Network Configuration, Connectivity Validation, and Firewall Troubleshooting in a Virtualized Security Lab

## Overview
This project documents the setup, troubleshooting, and validation of a lab environment designed for advanced web application security training. The environment includes an OPNsense firewall, a Linux client VM, and an internal lab network used to test connectivity, routing, DNS resolution, and general network behavior.

The focus of this exercise was to:
- configure the virtual network correctly,
- troubleshoot missing connectivity,
- verify the firewall and client machine are on the same LAN segment,
- confirm ICMP and DNS communication,
- validate basic routing and access through the OPNsense firewall.

---

## Student Information
- Student Name: Abdulmalik Isah Gaya
- Student ID: C11/26/FCDF/17171
- Operating System: Kali Linux 6.18.12+kali-amd64
- Hostname: Kali
- Date: October 6, 2026

---

## Lab Objective
To establish a functional network environment in which:
- the firewall is reachable from the client,
- the client can communicate with the firewall on the internal LAN,
- the firewall can support routing and network access,
- basic protocols such as ARP, ICMP, and DNS are functional.

---

## Network Architecture

The lab uses a simple virtualized network topology composed of:
- OPNsense firewall as the gateway/security appliance
- Internal network segment: `ICDFA-LAN`
- NAT/WAN interface for external connectivity
- Linux client VM connected to the internal network

```text
External Network (NAT / WAN)
             |
             v
     +------------------+
     | OPNsense Firewall|
     | 10.10.10.1/24    |
     +------------------+
             |
             |
      +------v------+
      | ICDFA-LAN   |
      | Internal    |
      | Network     |
      +------|------+
             |
             v
     +------------------+
     | Linux Client VM  |
     | 10.10.10.10/24   |
     +------------------+
