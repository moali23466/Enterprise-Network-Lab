# Enterprise Network Lab

## Overview
This lab demonstrates a fully functional enterprise network using Packet Tracer, simulating a realistic corporate environment with:

- **3-tier hierarchical network**: Access, Core, and Edge layers
- **VLAN segmentation** with inter-VLAN routing
- **HSRP (Hot Standby Router Protocol)** for gateway redundancy
- **DHCP, DNS, and NAT** for internal and external connectivity
- **ACLs** to enforce Guest VLAN restrictions
- **STP tuning** for predictable redundant paths
- **Internet simulation** via a dedicated ISP router and loopback (8.8.8.8)

---

## Network Topology

![Network Topology](network-topology.png)


- Core switches connect access switches and the edge router
- Edge router connects to ISP router simulating the Internet
- VLANs assigned per department: HR, Finance, Engineering, Guest, Servers, Admin

---

## VLAN & IP Plan

Refer to [`docs/IP_and_VLAN_plan.md`](docs/IP_and_VLAN_plan.md) for:

- VLAN IDs and purposes
- Subnets and gateways
- DHCP pools
- HSRP virtual IPs
- ACL rules

---

## Key Configurations

All device configs are included in the [`configs/`](configs/) folder:

- `core_sw1.cfg` & `core_sw2.cfg` → VLANs, SVIs, HSRP
- `router1.cfg` → NAT, default routes, ACLs, DHCP relay
- `isp.cfg` → Simulated Internet router and loopback (8.8.8.8)

---

## Test Results

### NAT & Internet Connectivity

From PC1 (VLAN 10):

```text
C:\> ping 8.8.8.8
Reply from 8.8.8.8: bytes=32 time<1ms TTL=253
