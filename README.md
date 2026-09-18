# IST2045-Network-lab
# Secure Campus Inter-Connectivity and Network Services

CAT II project for **IST 2045: Introduction to Computer Networks**, USIU-Africa (2025/2026 Academic Year, Summer Semester).

This project designs and builds a two-site campus network (Science Block and Library) in Cisco Packet Tracer, covering VLSM subnetting, VLANs with inter-VLAN routing, dynamic routing with OSPF, and network services (DHCP + ACLs).

## Topology Overview

- **Science Block**: 1 router (2911 + HWIC-2T), 1 switch (2960), 6 PCs across 3 VLANs
  - VLAN 10 – Faculty (static IPs)
  - VLAN 20 – Labs (DHCP)
  - VLAN 30 – IoT (DHCP)
- **Library**: 1 router (2911 + HWIC-2T), 1 switch (2960), 4 PCs across 2 VLANs
  - VLAN 40 – Students
  - VLAN 50 – Management
- Sites connected via a **Serial DCE WAN link**
- **OSPF (Area 0)** routes between sites
- **Loopback interface** on R-Library simulates a reachable internet address (203.0.113.1)
- **ACL 100** on R-Library blocks Student VLAN → Management VLAN traffic while permitting everything else

## Tasks Covered

| Task | Description | Marks |
|---|---|---|
| 1 | VLSM Design — subnetting 172.16.0.0 by host requirements | 10 |
| 2 | Switching, VLANs, and Inter-VLAN Routing | 10 |
| 3 | Dynamic Routing with OSPF | 10 |
| 4 | Network Services and ACLs (DHCP + access control) | 10 |

## Verification / Evidence

The report documents the following checks (with screenshots):
- `show vlan brief` and `show interfaces trunk` on SW-Science
- `show ip route` on both routers, confirming OSPF (`O`) routes to the remote site
- Successful Student ↔ Faculty ping (full path across the WAN link)
- DHCP-assigned IP on a Labs PC
- Failed Student → Management ping (ACL enforcement) and successful Student → Loopback ping (internet-permit rule)
- `tracert` showing the hop across the serial WAN link

## Repo Contents

| File | Description |
|---|---|
| `Complete_Build_Guide.md` | Step-by-step build instructions: device placement, cabling, and full configuration commands for both sites |
| `CATII_GROUP2_LABWORK.pkt` | Cisco Packet Tracer file with the complete working network |
| `CATII_IST2045_GROUP2_REPORT.docx` | Full written report with design rationale, configurations, and verification screenshots |

## Requirements

- [Cisco Packet Tracer](https://www.netacad.com/courses/packet-tracer) to open the `.pkt` file
- Microsoft Word (or a compatible viewer) to open the report

## Group

Group 2 — IST 2045, USIU-Africa
