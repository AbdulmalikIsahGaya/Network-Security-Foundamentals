# PROFESSIONAL REPORT
## IPv4 Addressing Foundations - Assignment 1

**Student Name:** Abdulmalik Isah Gaya  
**Student ID:** C11/26/FCDF/17171  
**Group:** TEAM04  
**Course:** Advanced Web Application Security Labs  
**Date:** September 25, 2026

---

## Executive Summary

This report documents a comprehensive analysis of IPv4 addressing foundations, covering core networking concepts, classful address identification, network analysis, and practical troubleshooting scenarios. The assignment demonstrates proficiency in understanding IP address structures, network configuration, and real-world problem-solving in network administration.

---

## 1. Introduction

IPv4 (Internet Protocol version 4) remains a critical component of modern networking infrastructure despite the emergence of IPv6. Understanding IPv4 addressing is fundamental for network administrators, security professionals, and IT practitioners. This assignment explores key concepts including address structure, classification schemes, and practical implementation scenarios.

---

## 2. Part A: Core Concepts Analysis

### 2.1 IPv4 Address Definition and Uniqueness

**Definition:** An IPv4 address is a 32-bit logical address represented as four decimal octets separated by dots (e.g., 192.168.1.10). Each octet represents 8 bits, providing a total addressing space of 2³² (approximately 4.3 billion addresses).

**Uniqueness Requirement:** On the same network segment, each device must maintain a unique IPv4 address. If two devices use identical IP addresses, a conflict occurs (IP conflict), resulting in:
- Packet delivery errors
- Network communication failures
- Disrupted service availability
- Unpredictable routing behavior

This requirement is fundamental to the protocol's design and is enforced through network configuration standards and protocols like DHCP.

### 2.2 Flat vs. Hierarchical Addressing

| Aspect | Flat Addressing | Hierarchical Addressing |
|--------|-----------------|------------------------|
| **Structure** | Single undifferentiated namespace | Divided into network and host portions |
| **Routing** | Difficult to scale; requires full lookup tables | Efficient; enables prefix-based routing |
| **Example** | MAC Address (00-1A-2B-3C-4D-5E) | IPv4 Address (192.168.10.0/24) |
| **Use Case** | Local network layer (LAN) | Wide area networking (WAN) |

Hierarchical addressing enables efficient routing by allowing network routers to forward packets based on network prefixes rather than maintaining individual device mappings.

### 2.3 Static vs. Dynamic IP Addressing

| Characteristic | Static Addressing | Dynamic Addressing |
|----------------|-------------------|-------------------|
| **Configuration** | Manually assigned | Automatically assigned |
| **Persistence** | Permanent (no changes) | Temporary; may change |
| **Protocol** | Manual/Configuration file | DHCP (Dynamic Host Configuration Protocol) |
| **Use Cases** | Servers, printers, routers | Client computers, mobile devices |
| **Administration** | High maintenance burden | Low maintenance overhead |

**DHCP Protocol:** The Dynamic Host Configuration Protocol automates IP address assignment, reducing administrative overhead and minimizing configuration errors in large networks.

### 2.4 Classful vs. Classless Addressing

**Classful Addressing:**
- Uses predefined address classes (A, B, C, D, E)
- Fixed subnet masks determined by first octet value
- Inflexible; causes IP address waste
- Legacy approach; largely obsolete

**Classless Addressing:**
- Implements Variable Length Subnet Masks (VLSM)
- Allows arbitrary network/host split
- Efficient address utilization
- Modern standard approach

**CIDR Definition:** Classless Inter-Domain Routing is a notation and methodology for allocating IP addresses and performing routing more efficiently than classful addressing. Notation: `a.b.c.d/prefix_length` (e.g., 192.168.1.0/24)

### 2.5 IPv4 Configuration Requirements

For successful internet-based name resolution and communication, four critical configuration items are required:

1. **IP Address:** Unique identifier for the device on the network
2. **Subnet Mask:** Defines the network and host portions of the address
3. **Default Gateway:** Router address for off-network traffic routing
4. **DNS Server Address:** Enables hostname-to-IP resolution (e.g., 8.8.8.8)

---

## 3. Part B: Classful Address Identification

The following table presents classful address identification with network/host patterns and default subnet masks:

| IPv4 Address | Class | Pattern | Default Subnet Mask |
|---|---|---|---|
| 23.14.6.9 | A | N.H.H.H | 255.0.0.0 |
| 145.80.12.200 | B | N.N.H.H | 255.255.0.0 |
| 198.51.100.27 | C | N.N.N.H | 255.255.255.0 |
| 9.200.10.1 | A | N.H.H.H | 255.0.0.0 |
| 188.44.9.72 | B | N.N.H.H | 255.255.0.0 |

**Classification Rules:**
- **Class A:** First octet 1-126 (0xxxxxxx binary)
- **Class B:** First octet 127-191 (10xxxxxx binary)
- **Class C:** First octet 192-223 (110xxxxx binary)

---

## 4. Part C: Network and Broadcast Address Analysis

### 4.1 Address 34.72.6.19 (Class A)

| Parameter | Value |
|-----------|-------|
| **Subnet Mask** | 255.0.0.0 |
| **Network Address** | 34.0.0.0 |
| **Broadcast Address** | 34.255.255.255 |
| **First Usable Host** | 34.0.0.1 |
| **Last Usable Host** | 34.255.255.254 |
| **Maximum Usable Hosts** | 16,777,214 |

### 4.2 Address 150.20.7.200 (Class B)

| Parameter | Value |
|-----------|-------|
| **Subnet Mask** | 255.255.0.0 |
| **Network Address** | 150.20.0.0 |
| **Broadcast Address** | 150.20.255.255 |
| **First Usable Host** | 150.20.0.1 |
| **Last Usable Host** | 150.20.255.254 |
| **Maximum Usable Hosts** | 65,534 |

### 4.3 Address 203.0.113.44 (Class C)

| Parameter | Value |
|-----------|-------|
| **Subnet Mask** | 255.255.255.0 |
| **Network Address** | 203.0.113.0 |
| **Broadcast Address** | 203.0.113.255 |
| **First Usable Host** | 203.0.113.1 |
| **Last Usable Host** | 203.0.113.254 |
| **Maximum Usable Hosts** | 254 |

---

## 5. Part D: Applied Troubleshooting Analysis

### Scenario Configuration
- **Workstation IP:** 201.110.213.28
- **Subnet Mask:** 255.255.255.0
- **Default Gateway:** 201.110.214.1
- **DNS Server:** 8.8.8.8

### 5.1 Network and Broadcast Address Determination

**Network Address:** 201.110.213.0  
**Broadcast Address:** 201.110.213.255

**Calculation:** Class C address with /24 mask; host bits (0) yield network address, host bits (255) yield broadcast address.

### 5.2 Default Gateway Validity Assessment

**Finding:** The configured default gateway is **INVALID**.

**Reasoning:**
- Workstation network: 201.110.213.0/24
- Gateway network: 201.110.214.0/24
- The gateway resides on a different network segment
- A valid gateway must be on the same network segment to be directly reachable
- This configuration prevents off-network communication

### 5.3 Valid Gateway Recommendation

**Valid Gateway Address:** 201.110.213.1

**Valid Range:** Any address from 201.110.213.1 to 201.110.213.254 (excluding 201.110.213.28)  
**Example Alternative:** 201.110.213.254

**Why Network/Broadcast Cannot Be Used:**
- **Network Address (201.110.213.0):** Identifies the network itself, not a device
- **Broadcast Address (201.110.213.255):** Reserved for network-wide broadcasts; cannot be assigned to individual devices
- Both addresses are reserved and have special functions in network layer operations

### 5.4 Communication Analysis with Incorrect Gateway

**Local Communication (WORKS):**
- Devices on 201.110.213.0/24 communicate directly using ARP (Address Resolution Protocol)
- Gateway bypass; direct layer 2 communication
- Examples: accessing 201.110.213.50, 201.110.213.100, etc.

**Remote Communication (FAILS):**
- Any destination outside 201.110.213.0/24 unreachable
- Includes: Internet resources, 8.8.8.8 DNS queries, other networks
- Packets destined for remote networks cannot be routed without a valid gateway
- Results in connectivity loss to external resources

### 5.5 Lab Addressing Recommendation

**Scenario:** 25 student computers requiring network configuration

**Recommendation:** Dynamic Addressing (DHCP)

**Justification:**
1. **Scalability:** Easy to manage 25+ devices centrally
2. **Conflict Prevention:** Automatic assignment eliminates manual configuration errors
3. **Administrative Efficiency:** Reduces IT staff workload significantly
4. **Flexibility:** Addresses can be reassigned as needed; supports device mobility
5. **Cost-Effective:** Lower operational overhead compared to static management

**Service Provider:** DHCP Server (Dynamic Host Configuration Protocol)
- Can be implemented via dedicated DHCP server
- Router-integrated DHCP (common in small networks)
- Centralized management system for large deployments

---

## 6. Key Findings and Conclusions

1. **Address Uniqueness:** Critical for proper network operation; prevents IP conflicts and routing errors
2. **Addressing Hierarchy:** Essential for scalable, efficient routing in complex networks
3. **Configuration Importance:** All four configuration items (IP, Mask, Gateway, DNS) are mandatory for complete connectivity
4. **Gateway Validation:** Gateway must reside on the same network segment as the host
5. **Addressing Strategy:** Dynamic addressing provides superior operational efficiency for client computers in educational and corporate environments

---

## 7. Recommendations for Network Administration

1. **Validation Procedures:** Always verify gateway addresses against calculated network ranges before deployment
2. **Documentation:** Maintain clear network topology documentation showing network segments and gateway assignments
3. **Monitoring:** Implement network monitoring to detect IP conflicts and misconfigurations
4. **Training:** Ensure IT staff understands classful and classless addressing concepts for troubleshooting
5. **Modern Standards:** Transition to CIDR notation and IPv6 for future-proof network design

---

## 8. References

- IPv4 Specification (RFC 791)
- CIDR Notation and Routing (RFC 4632)
- DHCP Protocol (RFC 2131)
- Subnetting Best Practices (RFC 1878)

---

**Report Prepared By:** Abdulmalik Isah Gaya  
**Date:** September 25, 2026  
**Institution:** Advanced Web Application Security Labs Program  
**Status:** Complete
