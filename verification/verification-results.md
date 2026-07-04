# Verification Results

This document summarizes the verification performed for the Enterprise Campus Network with Branch Connectivity project.

## 1. VLAN and Inter-VLAN Routing

Verified that end devices received correct IP addressing and could communicate through their default gateways.

| Device | VLAN | Expected Network | Status |
|---|---:|---|---|
| IT-PC | 10 | 192.168.10.0/24 | Passed |
| HR-PC | 20 | 192.168.20.0/24 | Passed |
| SALES-PC | 30 | 192.168.30.0/24 | Passed |
| GUEST-PC | 40 | 192.168.40.0/24 | Passed |
| HQ-SERVER | 50 | 192.168.50.0/24 | Passed |
| BR-PC1 / BR-PC2 | 60 | 192.168.60.0/24 | Passed |

## 2. HSRP Gateway Redundancy

HSRP was configured on DSW1 and DSW2 for redundant default gateway services.

| VLAN | Virtual Gateway | Active Device | Standby Device | Status |
|---|---|---|---|---|
| VLAN 10 | 192.168.10.1 | DSW1 | DSW2 | Passed |
| VLAN 20 | 192.168.20.1 | DSW1 | DSW2 | Passed |
| VLAN 30 | 192.168.30.1 | DSW2 | DSW1 | Passed |
| VLAN 40 | 192.168.40.1 | DSW2 | DSW1 | Passed |
| VLAN 50 | 192.168.50.1 | DSW1 | DSW2 | Passed |
| VLAN 99 | 192.168.99.1 | DSW1 | DSW2 | Passed |

## 3. OSPF Routing

OSPF Area 0 was configured across the distribution layer, edge router, and branch router.

Verified OSPF neighbors:

| Device | Neighbor Relationship | Status |
|---|---|---|
| DSW1 to EDGE-R1 | FULL | Passed |
| DSW2 to EDGE-R1 | FULL | Passed |
| EDGE-R1 to BR-R1 | FULL | Passed |

## 4. Default Route Propagation

EDGE-R1 has a static default route toward ISP-R1 and advertises the default route into OSPF.

Verified that DSW1, DSW2, and BR-R1 learned the default route through OSPF.

Status: Passed

## 5. NAT / Internet Access

NAT overload was configured on EDGE-R1.

Inside networks were translated to the EDGE-R1 public interface address.

Verified internet connectivity to the simulated public server:

| Source | Destination | Status |
|---|---|---|
| HQ VLANs | 198.51.100.10 | Passed |
| Branch VLAN 60 | 198.51.100.10 | Passed |

## 6. DHCP

DHCP pools were configured for user VLANs.

| VLAN | DHCP Server | Status |
|---|---|---|
| VLAN 10 | DSW1 | Passed |
| VLAN 20 | DSW1 | Passed |
| VLAN 30 | DSW1 | Passed |
| VLAN 40 | DSW1 | Passed |
| VLAN 60 | BR-R1 | Passed |

## 7. SSH Management

SSH was configured for device management.

VTY access was restricted to the IT VLAN.

| Management Source | Result |
|---|---|
| IT VLAN | Allowed |
| Non-IT VLANs | Restricted |

Status: Passed

## 8. Port Security

Port security with sticky MAC learning was configured on access ports.

| Switch | Ports | Status |
|---|---|---|
| ASW1 | IT, HR, Server ports | Passed |
| ASW2 | Sales, Guest ports | Passed |
| BR-SW1 | Branch PC ports | Passed |

## 9. Monitoring Services

NTP, Syslog, and SNMP were configured for infrastructure monitoring.

| Service | Server / Community | Status |
|---|---|---|
| NTP | 192.168.50.10 | Passed |
| Syslog | 192.168.50.10 | Passed |
| SNMP | CampusRO | Passed |

## 10. Summary

The lab successfully demonstrates an enterprise-style campus and branch network using VLAN segmentation, redundant gateways, dynamic routing, NAT, DHCP, SSH management, access-layer security, and basic monitoring services.
