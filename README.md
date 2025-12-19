# Cisco Static Routing Campus Network

## Project Description
This project is a simulation of **static routing implementation in a multi-subnet campus network** using **Cisco Packet Tracer**.  
The main purpose of this project is to understand static routing concepts, network segmentation, and inter-subnet communication in a campus environment.

The network is divided into several logical areas:
- Computer Laboratory
- IT Room
- Lecturer Room

---

## Network Topology Design
.

### Network Segments:
- **Computer Lab** → 192.168.1.0/24  
- **IT Room** → 192.168.2.0/24  
- **Lecturer Room** → 192.168.3.0/24  
- **Inter-router Link** → 10.10.10.0/24  

This topology represents a simple but realistic campus network design.

---

## IP Addressing Scheme
### Router R1
| Interface | IP Address | Subnet Mask |
|---------|-----------|-------------|
| G0/1 | 192.168.1.1 | 255.255.255.0 |
| G0/2 | 192.168.2.1 | 255.255.255.0 |
| G0/0 | 10.10.10.1 | 255.255.255.0 |

### Router R2
| Interface | IP Address | Subnet Mask |
|---------|-----------|-------------|
| G0/0 | 10.10.10.2 | 255.255.255.0 |
| G0/1 | 192.168.3.1 | 255.255.255.0 |

### End Devices (Examples)
| Device | IP Address | Default Gateway |
|------|-----------|----------------|
| Lab PC | 192.168.1.11 | 192.168.1.1 |
| IT PC | 192.168.2.2 | 192.168.2.1 |
| Lecturer PC | 192.168.3.30 | 192.168.3.1 |
