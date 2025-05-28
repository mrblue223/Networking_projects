# Simple Office Networking Project

This repository outlines the design and configuration for a simple office network, featuring two departments: ACCOUNTS and DELIVERY. The project focuses on practical application of IP addressing, subnetting, and basic network device configuration to ensure inter-departmental connectivity.

## Network Design Objectives

The primary goals for this network design are:

* Each department (ACCOUNTS and DELIVERY) must contain at least two PCs.
* Appropriate network hardware (switches and a router) will be used.
* All devices will be configured with suitable IP addresses, subnet masks, and default gateways using the `192.168.40.0` network address.
* All devices will be connected using the correct cabling.
* Connectivity will be tested to ensure PCs in the DELIVERY department can ping PCs in the ACCOUNTS department.

## Subnetting the `192.168.40.0/24` Network

To accommodate the two departments, the `192.168.40.0/24` network has been subnetted[cite: 2]. This is achieved by borrowing 1 bit from the host portion of the IP address, resulting in a `/25` subnet mask of `255.255.255.128`[cite: 3]. Each subnet will provide 126 usable host IP addresses[cite: 4].

### Subnet 1: ACCOUNTS Department

* **Network ID:** `192.168.40.0/25` [cite: 5]
* **Subnet Mask:** `255.255.255.128` [cite: 5]
* **Usable Host IP Range:** `192.168.40.1` to `192.168.40.126` [cite: 5]
* **Broadcast ID:** `192.168.40.127` [cite: 5]

### Subnet 2: DELIVERY Department

* **Network ID:** `192.168.40.128/25` [cite: 5]
* **Subnet Mask:** `255.255.255.128` [cite: 5]
* **Usable Host IP Range:** `192.168.40.129` to `192.168.40.254` [cite: 5]
* **Broadcast ID:** `192.168.40.255` [cite: 5]

## Network Implementation Details

### 1. Departmental PC Requirements

* **ACCOUNTS Department:** Two or more PCs will be assigned IP addresses from the `192.168.40.1` to `192.168.40.126` range[cite: 5].
* **DELIVERY Department:** Two or more PCs will be assigned IP addresses from the `192.168.40.129` to `192.168.40.254` range[cite: 6].

### 2. Network Hardware

* **Switches:** One network switch is designated per department to connect the internal PCs[cite: 7]. A 24-port Fast Ethernet switch is recommended as sufficient for small to medium-sized departments[cite: 8].
* **Router:** A single router is essential to connect the ACCOUNTS and DELIVERY subnets[cite: 9, 10].

### 3. IP Address Configuration Example

#### Router Configuration:

* **Interface for ACCOUNTS (e.g., G0/0):**
    * IP Address: `192.168.40.1` (Default gateway for ACCOUNTS PCs)
    * Subnet Mask: `255.255.255.128`
* **Interface for DELIVERY (e.g., G0/1):**
    * IP Address: `192.168.40.129` [cite: 11] (Default gateway for DELIVERY PCs)
    * Subnet Mask: `255.255.255.128`

#### ACCOUNTS Department PCs (Example: PC-ACC-01, PC-ACC-02):

* **PC-ACC-01:**
    * IP Address: `192.168.40.2`
    * Subnet Mask: `255.255.255.128`
    * Default Gateway: `192.168.40.1`
* **PC-ACC-02:**
    * IP Address: `192.168.40.3` [cite: 12]
    * Subnet Mask: `255.255.255.128`
    * Default Gateway: `192.168.40.1`

#### DELIVERY Department PCs (Example: PC-DEL-01, PC-DEL-02):

* **PC-DEL-01:**
    * IP Address: `192.168.40.130`
    * Subnet Mask: `255.255.255.128`
    * Default Gateway: `192.168.40.129`
* **PC-DEL-02:**
    * IP Address: `192.168.40.131` [cite: 13]
    * Subnet Mask: `255.255.255.128`
    * Default Gateway: `192.168.40.129`

### 4. Cabling

* **PCs to Switches:** Use straight-through Ethernet cables[cite: 14].
* **Switches to Router:** Use straight-through Ethernet cables[cite: 14].

### 5. Connectivity Testing

To verify inter-departmental communication:

1.  From any PC in the DELIVERY department (e.g., `192.168.40.130`), open the command prompt or terminal[cite: 15].
2.  Ping a PC in the ACCOUNTS department (e.g., `192.168.40.2`) using the command: `ping 192.168.40.2`[cite: 16].
3.  A successful ping confirms that the router is correctly routing traffic between the two subnets and all configurations are accurate[cite: 16].
