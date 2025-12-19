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
![Campus Network Topology](topology/campus-network-topology.png)


### Network Segments:
- **Computer Lab** → 192.168.1.0/24  
- **IT Room** → 192.168.2.0/24  
- **Lecturer Room** → 192.168.3.0/24  
- **Inter-router Link** → 10.10.10.0/24  

This topology represents a simple but realistic campus network design.

---

## IP Addressing Scheme
### Router R-1
| Interface | IP Address | Subnet Mask |
|---------|-----------|-------------|
| G0/1 | 192.168.1.1 | 255.255.255.0 |
| G0/2 | 192.168.2.1 | 255.255.255.0 |
| G0/0 | 10.10.10.1 | 255.255.255.0 |

### Router R-2
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

---

## Step-by-Step Router Configuration (Cisco CLI)

The following commands provide a complete and structured guide to configure static routing in this campus network topology.  
All configurations are performed using the Cisco IOS Command Line Interface.

---

### ==== Router-1 Setup ====


```
Router> enable
Router# configure terminal
Router(config)# hostname R-1
Router(config)# exit
```

### Secure Privileged Mode (Encryption)
```
R-1> enable
R-1# configure terminal
R-1(config)# enable secret [name password]
--- example: R-1(config)# enable secret admin123
```

### Configure Interface to Computer Lab
```
R-1> enable
R-1# configure terminal
R-1(config)# interface gig0/1
R-1(config-if)# ip address 192.168.1.1 255.255.255.0
R-1(config-if)# no shutdown
R-1(config-if)# exit
```

### Configure Interface to IT Room
```
R-1> enable
R-1# configure terminal
R-1(config)# interface gig0/2
R-1(config-if)# ip address 192.168.2.1 255.255.255.0
R-1(config-if)# no shutdown
R-1(config-if)# exit
```

### Configure Interface to Router-2
```
R-1> enable
R-1# configure terminal
R-1(config)# interface gig0/0
R-1(config-if)# ip address 10.10.10.1 255.255.255.0
R-1(config-if)# no shutdown
R-1(config-if)# exit
```

### Configure Static Route on Router-1
```
R-1> enable
R-1# configure terminal
R-1(config)# ip route 192.168.3.0 255.255.255.0 10.10.10.2
R-1(config)# exit
```

### ==== Router-2 Setup ====


### Configure Router Identity
```
Router> enable
Router# configure terminal
Router(config)# hostname R-2
Router(config)# exit
```

### Secure Privileged Mode (Encryption)
```
R-2> enable
R-2# configure terminal
R-2(config)# enable secret [name password]
--- example: R-1(config)# enable secret manajer123
```

### Configure Interface to Lecturer Room
```
R-2> enable
R-2# configure terminal
R-2(config)# interface gig0/1
R-2(config-if)# ip address 192.168.3.1 255.255.255.0
R-2(config-if)# no shutdown
R-2(config-if)# exit
```

### Configure Interface to Router-1
```
R-2> enable
R-2# configure terminal
R-2(config)# interface gig0/0
R-2(config-if)# ip address 10.10.10.2 255.255.255.0
R-2(config-if)# no shutdown
R-2(config-if)# exit
```

### Configure Static Routes on Router-2
```
R-2> enable
R-2# configure terminal
R-2(config)# ip route 192.168.1.0 255.255.255.0 10.10.10.1
R-2(config)# ip route 192.168.2.0 255.255.255.0 10.10.10.1
R-2(config)# exit
```

### Verification and Testing
```
R-1# show ip route
R-1# ping 192.168.2.2
R-1# ping 192.168.3.30
```








