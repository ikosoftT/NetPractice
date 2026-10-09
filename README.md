*This project has been created as part of the 42 curriculum by yikoubaz.*

# NetPractice

![42 School](https://img.shields.io/badge/42-School-000000?style=for-the-badge)
![Networking](https://img.shields.io/badge/Networking-TCP%2FIP-blue?style=for-the-badge)
![Status](https://img.shields.io/badge/Levels-10%2F10-brightgreen?style=for-the-badge)

## Description

**NetPractice** is a practical networking project developed as part of the **42 School curriculum**. Its primary objective is to introduce fundamental computer networking concepts through interactive exercises involving IP addressing, subnetting, routing, and network configuration.

The project consists of **10 progressively challenging levels**, each presenting a simulated network with configuration problems that must be resolved to establish proper communication between devices.

Unlike traditional programming projects, NetPractice focuses on understanding network architecture, diagnosing connectivity problems, and applying TCP/IP networking principles.

### Learning Objectives

- Understand IPv4 addressing and network communication.
- Calculate subnet masks, network addresses, and broadcast addresses.
- Identify valid host address ranges.
- Configure default gateways and routing tables.
- Understand how routers and switches forward network traffic.
- Apply CIDR notation and subnetting techniques.
- Diagnose connectivity issues using network diagrams and logs.
- Understand the OSI model and TCP/IP protocol suite.

## Networking Concepts

### 1. TCP/IP Addressing

TCP/IP is a collection of communication protocols used to connect devices across networks.

An IPv4 address is a 32-bit identifier represented using four decimal octets.

Example:

`192.168.1.10`

Each IPv4 address consists of two logical parts:

- **Network portion:** Identifies the network to which a device belongs.
- **Host portion:** Identifies the device within that network.

The subnet mask determines how many bits belong to each portion.

### 2. Subnet Masks and CIDR

A subnet mask separates the network portion of an IPv4 address from its host portion.

CIDR (Classless Inter-Domain Routing) represents the number of network bits using prefix notation.

| CIDR | Subnet Mask | Usable Hosts |
|---|---|---|
| /8 | 255.0.0.0 | 16,777,214 |
| /16 | 255.255.0.0 | 65,534 |
| /24 | 255.255.255.0 | 254 |
| /25 | 255.255.255.128 | 126 |
| /26 | 255.255.255.192 | 62 |
| /27 | 255.255.255.224 | 30 |
| /28 | 255.255.255.240 | 14 |
| /30 | 255.255.255.252 | 2 |

For conventional IPv4 subnets with network and broadcast addresses reserved:

**Usable hosts = 2^(32 − prefix) − 2**

The `/31` and `/32` prefixes are special cases and do not follow this conventional host-count formula.

### 3. Network and Broadcast Addresses

Every conventional IPv4 subnet contains:

- **Network address:** Identifies the subnet.
- **First usable host:** First assignable host address.
- **Last usable host:** Last assignable host address.
- **Broadcast address:** Used to address all hosts on the subnet.

Example:

```text
IP Address:        192.168.1.130/26
Subnet Mask:       255.255.255.192

Network Address:   192.168.1.128
First Usable Host: 192.168.1.129
Last Usable Host:  192.168.1.190
Broadcast Address: 192.168.1.191
Next Subnet:       192.168.1.192/26
```

### 4. Default Gateway

A default gateway is a router address used by a host to send packets toward destinations outside its directly connected networks.

For example:

```text
Host IP:         192.168.1.10
Subnet Mask:     255.255.255.0
Default Gateway: 192.168.1.1
```

When the host needs to communicate with a remote network, it forwards the packet to its configured gateway.

The gateway must be reachable through a directly connected network.

### 5. Routers and Switches

**Switches** primarily operate at OSI Layer 2 and forward Ethernet frames using MAC addresses.

**Routers** operate at OSI Layer 3 and forward IP packets between different networks using routing tables.

| Feature | Switch | Router |
|---|---|---|
| Primary OSI Layer | Layer 2 | Layer 3 |
| Main Addressing | MAC | IP |
| Main Function | Connect devices within a LAN | Connect different networks |
| Forwarding Basis | MAC address table | Routing table |

### 6. Routing Tables

A routing table determines where packets should be forwarded to reach their destinations.

A route generally contains:

- Destination network
- Subnet mask or CIDR prefix
- Next-hop gateway or outgoing interface

Example:

```text
Destination       Gateway
192.168.1.0/24    Directly connected
10.0.0.0/8        192.168.1.254
0.0.0.0/0         192.168.1.1
```

The route `0.0.0.0/0` represents the default route.

Routers normally use **longest prefix matching** to select the most specific matching route.

### 7. OSI Model

The OSI model describes network communication through seven conceptual layers.

| Layer | Name | Examples |
|---|---|---|
| 7 | Application | HTTP, DNS |
| 6 | Presentation | Encoding, encryption |
| 5 | Session | Session management |
| 4 | Transport | TCP, UDP |
| 3 | Network | IPv4, ICMP |
| 2 | Data Link | Ethernet, MAC |
| 1 | Physical | Cables, electrical signals |

NetPractice primarily emphasizes Layer 3 addressing and routing, while also introducing the roles of switches and network interfaces.

## Instructions

### Requirements

- A computer running Linux, macOS, or another compatible operating system.
- A modern web browser.
- A terminal.
- Python 3, if manual server startup is necessary.
- The NetPractice training files provided by 42.

No compilation is required.

### 1. Download NetPractice

Download the project archive from the 42 intranet project page and extract it into a directory.

### 2. Launch the Training Interface

Navigate to the extracted directory and execute:

```bash
./run.sh
```

If execution permission is missing:

```bash
chmod +x run.sh
./run.sh
```

The script launches a local web server and opens the training interface in your browser.

**Alternative method:**

If the script does not work, start the server manually from the extracted directory:

```bash
python3 -m http.server 49242
```

Then navigate to:

```text
http://localhost:49242
```

### 3. Enter Your Login

Enter the following login in the training interface:

```text
yikoubaz
```

This is essential because the personal training configuration is associated with the login.

The evaluation tab can also generate randomized configurations for practice.

### 4. Solve the Exercises

Each level displays a network diagram containing devices, network interfaces, addresses, and routing information.

To solve a level:

1. Read the connectivity objectives.
2. Analyze the network topology.
3. Identify incorrect or missing IP configurations.
4. Calculate the appropriate subnet addresses and masks.
5. Configure gateways and routing tables when necessary.
6. Click **Check again** to validate the configuration.
7. Examine the logs if connectivity tests fail.
8. Correct the configuration until every objective succeeds.

Only the editable fields in the interface should be modified.

### 5. Export Your Configurations

After successfully completing each level:

1. Click **Get my config**.
2. Download the exported configuration file.
3. Save the file in the root of your Git repository.
4. Repeat for all 10 levels.

Do not forget to export each configuration before moving to the next level.

### 6. Submission

The Git repository must contain:

- `README.md`
- 10 exported configuration files, one for each level.

All 10 configuration files must be placed at the **repository root**.

Example repository structure:

```text
NetPractice/
├── README.md
├── level1.json
├── level2.json
├── level3.json
├── level4.json
├── level5.json
├── level6.json
├── level7.json
├── level8.json
├── level9.json
└── level10.json
```

The filenames above are illustrative. Preserve the actual filenames generated by the NetPractice interface.

Only files present in the submitted Git repository will be considered during evaluation.

## Troubleshooting

### Invalid IP Address

Verify that:

- Each IPv4 octet is between 0 and 255.
- The address is valid for the configured subnet.
- The address is not a reserved network or broadcast address when a conventional host address is required.

### Incorrect Subnet Mask

Check that communicating interfaces belong to the appropriate subnet and that the mask is consistent with the network topology.

### Missing Gateway

When communication must cross different networks, ensure that a suitable route exists and that the next-hop gateway is reachable.

### Routing Failure

Inspect the routing tables and verify:

- Destination network and mask.
- Correct next-hop gateway.
- Reachability of the next hop.
- Return-path connectivity.
- Longest-prefix route selection.

### Failed Connectivity Tests

Read the logs displayed at the bottom of the training interface. They provide information about invalid configurations and unreachable destinations.

## Resources

### Official Documentation

- [RFC 791 — Internet Protocol](https://www.rfc-editor.org/rfc/rfc791)
- [RFC 4632 — Classless Inter-domain Routing (CIDR)](https://www.rfc-editor.org/rfc/rfc4632)
- [RFC 1812 — Requirements for IPv4 Routers](https://www.rfc-editor.org/rfc/rfc1812)
- [RFC 3021 — Using 31-Bit Prefixes on IPv4 Point-to-Point Links](https://www.rfc-editor.org/rfc/rfc3021)
- [Cisco Networking Documentation](https://www.cisco.com/c/en/us/support/index.html)

### Learning Resources

- [Practical Networking — Subnetting](https://www.practicalnetworking.net/stand-alone/subnetting-mastery/)
- [Cloudflare — What Is the OSI Model?](https://www.cloudflare.com/learning/ddos/glossary/open-systems-interconnection-model-osi/)
- [Cloudflare — What Is TCP/IP?](https://www.cloudflare.com/learning/ddos/glossary/tcp-ip/)
- [Computer Networking — freeCodeCamp](https://www.freecodecamp.org/news/tag/computer-networking/)

### Networking Topics Studied

The following concepts are relevant to this project:

- TCP/IP addressing and IPv4 fundamentals.
- Binary representation of IPv4 addresses.
- Subnet masks and CIDR notation.
- Network and broadcast addresses.
- First and last usable host addresses.
- Subnet calculations and address ranges.
- Default gateways.
- Routers and switches.
- Static routing and routing tables.
- Longest prefix matching.
- Network topology and connectivity.
- OSI layers and TCP/IP architecture.
- Network troubleshooting and packet forwarding.

### AI Usage

AI tools, including ChatGPT, were used as learning and documentation aids.

The assistance included:

- Explaining theoretical networking concepts such as IPv4 addressing, subnet masks, CIDR, and routing.

## Author

**yikoubaz**

42 / 1337 School — NetPractice

---

*Understanding how packets travel through a network is the foundation of networking, systems engineering, and cybersecurity.*
