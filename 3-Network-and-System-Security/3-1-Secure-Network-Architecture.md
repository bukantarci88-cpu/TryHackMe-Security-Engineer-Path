# Eng 3.1. Secure Network Architecture

#### **Task 1 - Introduction**

A resilient enterprise network design integrates high-availability redundancy, performance optimization, and strict network segmentation to prevent lateral movement during a breach and isolate untrusted devices from critical infrastructure assets.

#### **Task 2 - Network Segmentation**

**The Need for Secure Segmentation:** Virtual Local Area Networks employ layer-two 802.1q frame tagging to logically segregate network traffic and isolate endpoints, though basic VLAN boundaries alone are insufficient to completely halt lateral movement from compromised devices in BYOD scenarios.

**Routing Between VLANs:** Router on a Stick (ROAS) is an inter-VLAN routing design that uses a single physical trunk link and router subinterfaces to enable communication between logically isolated VLANs, eliminating the need for dedicated physical hardware connections per network segment.

<img width="221" height="450" alt="image" src="https://github.com/user-attachments/assets/4b5e075c-2be6-4fe4-9fa0-71ec0c1ec8c9" />


**Answer the questions below:** 

> How many trunks are present in this configuration?
> 

4 (bridges on the pictures) 

> What is the VLAN tag ID for interface eth12?
> 

30 (check port eth12 on the picture) 

#### **Task 3 - Common Secure Network Architecture**

| **Zone** | **Explanation** | **Examples** |
| --- | --- | --- |
| External | All devices and entities outside of our network or asset control. | Devices connecting to a web server |
| DMZ (**d**e**m**ilitarized **z**one) | Separates untrusted networks or devices from internal resources. | BYOD, remote users/guests, public servers |
| Trusted | Internal networks or devices. A device may be placed in the trusted zone if there is no confidential or sensitive information. | Workstations, B2B |
| Restricted | Any high-risk servers or databases. | Domain controllers, client information |
| Management | Any devices or services dedicated to network or other device management. This zone is less commonly seen and can be grouped with the audit zone. | Virtualization management, backup servers |
| Audit | Any devices or services dedicated to security or monitoring. This zone is less commonly seen and can be grouped with management. | SIEM, telemetry |

<img width="527" height="372" alt="image 1" src="https://github.com/user-attachments/assets/08b4cd1a-ea26-4d61-ae7b-fbc878f879c8" />


**Answer the questions below**

> From the above table, what zone would a user connecting to a public web server be in?
> 

External

> From the above table, what zone would a public web server be in?
> 

DMZ 

> From the above table, what zone would a core domain controller be placed in?
> 

Restricted

#### **Task 4 - Network Security Policies and Controls**

Network Access Control Lists (ACLs) utilize ordered sets of Access Control Entries (ACEs) defined by criteria such as source and destination addresses to govern packet routing and traffic filtering decisions at network boundaries.

**Answer the questions below**

> According to the corresponding ACL policy, will the first packet result in a drop or accept?
> 

accept

<img width="688" height="490" alt="image 2" src="https://github.com/user-attachments/assets/a143b9b9-8821-4dc7-b9ea-55178cc3d6b7" />


> According to the corresponding ACL policy, will the second packet result in a drop or accept?
> 

drop

<img width="684" height="450" alt="image 3" src="https://github.com/user-attachments/assets/0adfdaa9-326f-4e58-a6cd-1233fc883c9a" />


#### **Task 5 - Zone-Pair Policies and Filtering**

**Creating a Zone-Pair from Scratch:** Now that you have an understanding of how to create a basic zone-pair policy, launch the static site attached to this task by pressing the green ****View **Site** button. Use the table below to fill in the blanks provided in the static site.

| Source | Destination | Protocol | Action | Default Action |
| --- | --- | --- | --- | --- |
| DMZ | LAN | HTTP | Accept | Drop |
| DMZ | WAN | - | - | Drop |
| LAN | DMZ | ICMP | Accept | Drop |
| WAN | DMZ | - | - | Drop |

| Common Name | Interface | Default Action |
| --- | --- | --- |
| DMZ | eth0.10 | Drop |
| LAN | eth0.20 | Drop |
| WAN | eth0.30 | Drop |

**Answer the questions below**

> What is the flag found after filling in all blanks on the static site?
> 

THM{M05tly_53cure}

<img width="722" height="862" alt="image 4" src="https://github.com/user-attachments/assets/0217da65-6920-4ab1-aa47-24f704eeec16" />


#### **Task 6 - Validating Network Traffic**

**SSL/TLS Inspection:** SSL/TLS inspection employs a man-in-the-middle (MitM) proxy architecture to decrypt encrypted enterprise traffic, allowing Unified Threat Management (UTM) systems to inspect payloads for threats while introducing significant privacy concerns, computational overhead, and cryptographic trust management challenges.

**Answer the questions below**

> Does SSL inspection require a man-in-the-middle proxy?
> 

Y

> What platform processes data sent from an SSL proxy?
> 

Unified Threat Management

**Task 7 - Addressing Common Attacks**

**DHCP Snooping:** DHCP snooping is a layer-two switch security feature that acts as a firewall between trusted DHCP servers and untrusted hosts to mitigate rogue DHCP servers, validate lease traffic, and maintain a binding database for downstream security features.

- Any DHCP packet is received from outside of the network.
- The source MAC address and DHCP client hardware address do not match.
- A `DHCPRELEASE` or `DHCPDECLINE` packet is received on an untrusted interface that does not match an interface that the source address already has registered.
- A DHCP packet that includes a relay agent address that is not `0.0.0.0`

**Dynamic ARP Inspection:** Dynamic ARP Inspection secures layer-two domains by cross-referencing incoming ARP packets against trusted DHCP snooping binding databases, automatically intercepting and dropping frames with mismatched IP-to-MAC address pairs to thwart ARP spoofing and cache poisoning attacks.

the DHCP binding database provides the expected MAC and IP address pair of untrusted hosts; ARP inspection will compare the source IP address and MAC address to the binding pair; if they are mismatched, it will drop the packet.

**Answer the questions below**

> Where does DHCP snooping store leased IP addresses from untrusted hosts?
> 

DHCP Binding Database 

> Will a switch drop or accept a DHCPRELEASE packet?
> 

Drop 

> Does dynamic ARP inspection use the DHCP binding database?
> 

Y 

> Dynamic ARP inspection will match an IP address and what other packet detail?
> 

MAC Address
