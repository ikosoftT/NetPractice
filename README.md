*This project has been created as part of the 42 curriculum by yikoubaz.*

# NetPractice

## Description

NetPractice is a practical introduction to computer networking in the 42 curriculum. The project consists of 10 simulated network exercises. Each level presents a broken topology and connectivity goals; the task is to configure the editable IP addresses, subnet masks, gateways, and routes so that the required hosts can communicate.

The exercises build an understanding of IPv4 addressing, subnetting, local communication through switches, and communication between networks through routers. The submitted work consists of the **10 configuration files exported from the training interface**, one per level.

## Instructions

### Start the training interface

1. Download the NetPractice archive from the project page and extract it to a directory.
2. From the extracted directory, run:

   ```sh
   ./run.sh
   ```

   The script starts a local server and opens the interface in your browser. There is no program to compile for the exercises.

3. If the script does not work, start a local server from the directory containing the training files:

   ```sh
   python3 -m http.server 49242
   ```

   Then open [http://localhost:49242](http://localhost:49242) in your browser. If that port is unavailable, choose another and use the same port in the URL.

### Complete and export each level

1. Enter **your 42 login** in the training interface to use your personal configuration. The **evaluation** tab can also generate random configurations for practice.
2. Read the goals at the top of the level. Change only the editable (unshaded) fields in the network diagram.
3. Select **Check again** and read the logs at the bottom of the page to diagnose any failed connection.
4. After a level succeeds, select **Get my config** to download its configuration **before moving to the next level**.
5. Repeat until you have exported **one file for each of the 10 levels**.

### Submission

Place `README.md` and **all 10 exported configuration files directly at the root of your Git repository**. Keep the exported filenames supplied by the interface, check that each file corresponds to a different level, and submit the repository through the usual 42 workflow. Only files present in the repository are evaluated.

During the peer evaluation, you must solve **three random levels under a time limit**. External tools are not allowed; the subject tolerates a simple calculator such as `bc`.

## Networking concepts studied

| Concept | Role in NetPractice |
| --- | --- |
| TCP/IP and IPv4 addressing | Identify hosts and router interfaces with valid, unique IP addresses. |
| Subnet masks and CIDR | Separate the network bits from the host bits and determine whether two addresses are on the same subnet. |
| Network, broadcast, and host addresses | Choose usable interface addresses within a subnet. |
| Switches | Connect hosts on the same local network without performing IP routing. |
| Routers | Forward packets between different IP networks through interfaces attached to those networks. |
| Default gateways | Give a host a reachable next hop for destinations outside its local subnet. |
| Routing tables and default routes | Choose a next hop for a destination, including a fallback route where appropriate. |
| OSI layers | Relate switching to the data link layer (Layer 2), IP routing to the network layer (Layer 3), and TCP/UDP to the transport layer (Layer 4). |

For example, `192.168.10.37/27` has the mask `255.255.255.224`. Its network is `192.168.10.32/27`, its broadcast address is `192.168.10.63`, and its usual usable host range is `192.168.10.33` through `192.168.10.62`. A host at `192.168.10.55/27` is in that same subnet, so those two hosts can communicate locally if the topology connects them.

## Approach to a level

1. Validate every IP address: four octets, each from `0` to `255`.
2. Use each address and mask to identify its subnet. Check that directly connected interfaces that must communicate have compatible subnet addresses and unique usable IPs.
3. For a destination outside a host's subnet, set the host's gateway to an IP address on its local subnet, typically the adjacent router interface.
4. Check every router interface against its attached network. Add routes or next hops needed to reach remote networks, and verify the return path as well.
5. Test with **Check again**, follow the diagnostic logs, and export the working configuration.

## Resources

- NetPractice subject, version 6.3 (available on the 42 project page) — project requirements, training workflow, export instructions, and evaluation rules.
- [Practical Networking — Subnetting Mastery](https://www.practicalnetworking.net/stand-alone/subnetting-mastery/) — CIDR notation, subnet ranges, host ranges, and calculation exercises.
- [Practical Networking — Network Fundamentals](https://www.practicalnetworking.net/classes/network-fundamentals/) — TCP/IP addressing, subnetting, switches, routers, packet flow, and OSI layers.
- [Cloudflare — What is a subnet?](https://www.cloudflare.com/learning/network-layer/what-is-a-subnet/) — introduction to subnets and subnet masks.
- [Cloudflare — What is a router?](https://www.cloudflare.com/learning/network-layer/what-is-a-router/) and [What is a network switch?](https://www.cloudflare.com/learning/network-layer/what-is-a-network-switch/) — roles of routers and switches.
- [RFC 791 — Internet Protocol](https://www.rfc-editor.org/info/rfc791/) — original technical reference for IPv4.

### Use of AI

AI was used to explain IPv4 addressing and subnet masks while working through a Level 1 example, and to draft and organize this README against the subject's requirements. The exported level configurations must be checked in the simulator and understood well enough to explain and reproduce during evaluation. Review this section if your actual use of AI changes.
