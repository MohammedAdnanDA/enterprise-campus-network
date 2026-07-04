# Enterprise Campus Network with Branch Connectivity

## Project Overview

This project is a Cisco Packet Tracer enterprise network simulation designed to model a small-to-medium business network with a redundant HQ campus, branch connectivity, internet edge, NAT, centralized services, monitoring, and access-layer security.

The project demonstrates practical CCNA-level networking skills using switching, routing, redundancy, segmentation, security controls, and monitoring services.

## Topology Summary

The network includes:

* Two HQ distribution multilayer switches: DSW1 and DSW2
* Two HQ access switches: ASW1 and ASW2
* One edge router: EDGE-R1
* One branch router: BR-R1
* One branch access switch: BR-SW1
* One internal server: HQ-SERVER
* One ISP router: ISP-R1
* One public server: PUBLIC-SERVER
* End-user PCs across IT, HR, Sales, Guest, and Branch networks

## VLAN and IP Addressing

| VLAN | Name          | Subnet          | Purpose                      |
| ---- | ------------- | --------------- | ---------------------------- |
| 10   | IT            | 192.168.10.0/24 | IT users                     |
| 20   | HR            | 192.168.20.0/24 | HR users                     |
| 30   | SALES         | 192.168.30.0/24 | Sales users                  |
| 40   | GUEST         | 192.168.40.0/24 | Guest users                  |
| 50   | SERVER        | 192.168.50.0/24 | Internal server network      |
| 60   | BRANCH        | 192.168.60.0/24 | Branch users                 |
| 99   | MGMT          | 192.168.99.0/24 | Network device management    |
| 999  | NATIVE/UNUSED | No routed IP    | Native VLAN and unused ports |

## Key Features Implemented

### Layer 2 Switching

* VLAN segmentation for different departments
* Access port configuration for endpoint devices
* Trunk links between access and distribution switches
* EtherChannel between DSW1 and DSW2
* STP root bridge design for predictable Layer 2 forwarding
* Native VLAN changed to VLAN 999
* Unused ports moved to VLAN 999 and administratively shut down

### Layer 3 Routing

* Inter-VLAN routing using SVIs on multilayer switches
* HSRP gateway redundancy between DSW1 and DSW2
* OSPF dynamic routing between HQ, edge, and branch devices
* Default route from EDGE-R1 to ISP-R1
* Default route advertisement into OSPF for internal networks

### Branch Connectivity

* Branch LAN connected through BR-R1
* OSPF used to exchange routes between branch and HQ
* Branch users able to reach HQ resources and internet services

### Internet Edge and NAT

* ISP router and public server simulation
* Serial WAN link between EDGE-R1 and ISP-R1
* NAT overload/PAT configured on EDGE-R1
* Internal private IP addresses translated to EDGE-R1 public-facing IP

### DHCP

* DHCP configured for HQ user VLANs
* DHCP configured for branch users
* HQ-SERVER configured with a static IP address

### Security

* Guest VLAN restricted from accessing internal corporate VLANs
* Guest VLAN allowed to access external/public server
* SSH enabled for secure device management
* VTY access restricted to IT VLAN only
* Port security configured with sticky MAC addresses
* PortFast and BPDU Guard enabled on endpoint ports
* Unused ports disabled and placed in VLAN 999

### Monitoring and Management

* NTP configured using HQ-SERVER as the internal time source
* Syslog forwarding configured to HQ-SERVER
* SNMP read-only community configured using `CampusRO`
* Management VLAN configured for switch administration

## Verification Performed

The following verification tests were completed:

* VLAN-to-VLAN connectivity
* HSRP active/standby gateway roles
* OSPF neighbor relationships
* OSPF route learning
* Default route propagation
* Branch-to-HQ connectivity
* Internet access through NAT
* Guest VLAN access restriction
* SSH management access
* Port security sticky MAC learning
* NTP synchronization
* Syslog forwarding
* SNMP configuration

## Skills Demonstrated

* Cisco switching and routing
* VLANs and trunking
* EtherChannel
* STP root bridge planning
* Inter-VLAN routing
* HSRP redundancy
* OSPF dynamic routing
* DHCP configuration
* NAT/PAT
* ACL-based network segmentation
* SSH management security
* Port security
* NTP, Syslog, and SNMP
* Enterprise network troubleshooting and verification

## Repository Structure

```text
enterprise-campus-network/
│
├── README.md
├── packet-tracer-file/
│   └── enterprise-campus-network.pkt
│
├── configs/
│   ├── DSW1.txt
│   ├── DSW2.txt
│   ├── EDGE-R1.txt
│   ├── BR-R1.txt
│   ├── ASW1.txt
│   ├── ASW2.txt
│   └── BR-SW1.txt
│
├── verification/
│   └── verification-results.md
│
└── screenshots/
    └── topology.png
```

## Project File

The Cisco Packet Tracer `.pkt` file is included in the `packet-tracer-file/` folder.

## Tools Used

* Cisco Packet Tracer
* Cisco IOS CLI
* GitHub for project documentation and version control

README.md
packet-tracer-file/
screenshots/
configs/
verification/
