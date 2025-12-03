🔒 Secure Multi-Branch Enterprise Network Design

use this FILE = COHNDNE242F-012_Network_Project v6.0 final.pkt

Module: Network Security / Network Engineering

Tool Used: Cisco Packet Tracer 8.2

📖 Project Overview

This project demonstrates the design and implementation of a secure enterprise network connecting a Main Branch Office (Headquarters) and a Sub Branch Office over a simulated WAN.

The architecture utilizes Cisco ASA 5506-X Firewalls to establish a secure Site-to-Site IPSec VPN, ensuring encrypted communication between departments across the public internet. The network allows for secure resource sharing while maintaining strict isolation through VLANs and security hardening.

🏗️ Network Topology

1. Main Branch (Left Side)

Gateway: Cisco ISR 4321 Router (Router-on-a-Stick configuration).

Security: Cisco ASA 5506-X Firewall (Perimeter security).

Switching: Cisco 2960 Switch with Port Security.

VLANs:

VLAN 10: Accounting (192.168.10.0/24) + Wireless Access.

VLAN 20: Sales (192.168.20.0/24).

VLAN 30: Customer Care (192.168.30.0/24).

Wireless: WPA2-PSK Enterprise WiFi for Accounting laptops.

2. Sub Branch (Right Side)

Gateway: Cisco ISR 4321 Router.

Security: Cisco ASA 5506-X Firewall.

Network: Single LAN (192.168.50.0/24) representing 20 users.

3. WAN / Internet

ISP Router: Simulates the internet backbone routing traffic between the two public IP addresses of the firewalls.

⚙️ Key Configurations & Technologies

🔐 Security Features

Site-to-Site IPSec VPN: Encrypted tunnel between Main Branch and Sub Branch using IKEv1 (AES/SHA).

NAT Exemption: Configured to allow internal private IP communication across the VPN without translation.

Port Security: Enabled on switches to prevent unauthorized device connections (Max 2 MAC addresses, Violation: Shutdown).

Interface Hardening: All unused switch ports are administratively shut down.

Device Hardening: Secure passwords (enable secret) and encrypted configuration.

📡 Connectivity

Inter-VLAN Routing: Configured on the Main Router to allow communication between different departments.

Static Routing: Default routes configured on Firewalls and Routers to direct traffic to the ISP.




🔑 Access Credentials

(For testing purposes only)

Enable Secret / Privileged Exec: senira

Console Password: cisco12345

VTY / Telnet Password: cisco12345

VPN Pre-Shared Key: seniraVPN

WiFi Password (SSID: Accounting-WiFi): seniraWiFi





🧪 How to Test the Network

1. Verify VPN Connectivity

Open PC-Acct (Main Branch).

Open the Command Prompt.

Ping the Sub Branch PC:

ping 192.168.50.10


Result: You should receive a reply (The first request may time out due to ARP/VPN negotiation).

2. Verify VPN Encryption

Open the ASA-Main CLI.

Run the command:

show crypto ipsec sa


Result: Check the #pkts encaps and #pkts decaps counters. They should be greater than 0.

3. Verify Port Security

Open SW1-Main CLI.

Run the command:

show port-security interface fa0/1


Result: Status should be Secure-up and Violation Mode Shutdown.

📂 Installation

Ensure you have Cisco Packet Tracer 8.2 or newer installed.

Download the .pkt file from this repository.

Open the file and allow the network to converge (wait for green lights).
