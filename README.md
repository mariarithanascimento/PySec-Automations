
> Hello!! Welcome to my portfolio project. Below you will find 7 automations created by me, all programmed in Python.  
> Each one has a brief description of its functionality and how to run it on your machine.  
> I hope you enjoy 😊

## `Project 1: DoS Blocker`

### Description:
The **DoS Blocker** monitors network traffic to identify and block Denial of Service (DoS) attacks. It analyzes the packet rate from specific IPs, and if the rate exceeds a defined threshold (40 packets per second), the IP is blocked using `iptables`.

### How to Run:
1. Make sure you have **Python** installed on your system, along with the necessary dependencies:
    ```bash
    pip install scapy
    ```

2. Run the script with superuser (root) privileges:
    ```bash
    sudo python3 dos_blocker.py
    ```

3. The script will start monitoring network traffic. When an IP sends packets beyond the limit, it will be blocked.

### Dependencies:
- `scapy` (a library for network packet capture)
- `iptables` (to block IPs directly on the system)

### Notes:
- The packet per second limit is set to 40 but can be changed by modifying the `THRESHOLD` constant.
- To monitor network traffic, root access is required.

## `Project 2: Mini Firewall`

### Description:
The **Mini Firewall** is a simple firewall that blocks IPs based on whitelist and blacklist files. It also detects the Nimda worm and blocks malicious IPs. Block events are logged into files.

### How to Run:
1. Create the IP list files (`whitelist.txt` and `blacklist.txt`) with the allowed and blocked IPs, respectively.

2. Install the required dependencies:
    ```bash
    pip install scapy
    ```

3. Run the script as a superuser (root):
    ```bash
    sudo python3 mini_firewall.py
    ```

4. The firewall starts monitoring network traffic, blocking malicious IPs and logging the events in the `logs` directory.

### Dependencies:
- `scapy` (a library for network packet analysis)
- `iptables` (to block IPs on the system)
- IP lists (`whitelist.txt` and `blacklist.txt`)

### Notes:
- The script detects the Nimda worm by analyzing HTTP traffic (port 80).
- Log files are automatically generated with timestamps, storing information about the block events.
- The packet per second limit is also set to 40 and can be changed in the `THRESHOLD` variable.

## `Project 3: Simulation`

### Description:
The **Simulation** is a simple firewall simulation that generates random IP addresses and checks whether they match predefined block rules. If the IP is on the blocklist, the action will be "block"; otherwise, the action will be "allow."

### How to Run:
1. Simply run the script without any special permissions:
    ```bash
    python3 simulation.py
    ```

2. The script generates 12 random IP addresses within the range `192.168.1.0 - 192.168.1.20` and checks the firewall rules for each IP, printing the corresponding action.

### Dependencies:
- There are no external dependencies.

### Notes:
- The firewall rules are defined in the `firewall_rules` dictionary, which can be modified as needed to include new IPs and actions.
- A random number between 0 and 9999 is generated along with each IP, simulating various events.

## `Project 4: OS Fingerprinting`

### Description:
The **OS Fingerprinting** scans a host to identify the operating system and services associated with different protocols and ports. It uses the `nmap` library to perform the scan and exports the results to a CSV file.

### How to Run:
1. Install the `nmap` library:
    ```bash
    pip install python-nmap
    ```

2. Run the script as a superuser (root):
    ```bash
    sudo python3 os_fingerprinting.py <host> -p <ports> -o <output_file.csv>
    ```

    - **host**: The target host IP address.
    - **ports**: The ports you want to scan (example: "22,80,443").
    - **output_file**: CSV file to save the results. If not specified, the default will be `scan_results.csv`.

### Dependencies:
- `python-nmap` (Python interface for Nmap)
- `nmap` (must be installed on the system)

## `Project 5: Ping Sweeper`

### Description:
The **Ping Sweeper** performs a ping sweep on a network to identify hosts that are online. It uses the ICMP protocol to send packets and verify if the hosts respond.

### How to Run:
1. Install the necessary dependencies:
    ```bash
    pip install scapy netaddr
    ```

2. Run the script:
    ```bash
    python3 ping_sweeper.py <network> <netmask>
    ```

    - **network**: The target network address (e.g., `192.168.1.0`).
    - **netmask**: The network mask (e.g., `24` for `255.255.255.0`).

3. The script will scan the network and list the hosts that are online.

### Dependencies:
- `scapy` (library for network packet manipulation)
- `netaddr` (for working with IP addresses and subnets)

## `Project 6: Port Scanner`

### Description:
The **Port Scanner** scans a network to identify active hosts and checks for open ports on each host. It uses `scapy` to send TCP packets and performs the port scan in parallel.

### How to Run:
1. Install the necessary dependencies:
    ```bash
    pip install scapy
    ```

2. Run the script:
    ```bash
    python3 port_scanner.py <network> <netmask>
    ```

    - **network**: The target network address (e.g., `192.168.1.0`).
    - **netmask**: The network mask (e.g., `24` for `255.255.255.0`).

3. The script will identify active hosts and list the open ports for each of them.

### Dependencies:
- `scapy` (library for network packet manipulation)

### Notes:
- The number of threads used in the scan is based on the number of CPUs available in the system.
- The scope of the port scan is from 1 to 1023, but can be adjusted in the code.

## `Project 7: Service Fingerprinting`

### Description:
The **Service Fingerprinting** performs a scan to identify service banners running on specific ports of a host. It attempts to connect to a service and returns the application banner, useful for detecting software versions.

### How to Run:
1. Run the script:
    ```bash
    python3 service_fingerprinting.py <ip> -p <ports>
    ```

    - **ip**: The target host IP address.
    - **ports**: List of ports to be scanned, separated by commas (e.g., "22,80,443").

2. The script will return the service banners identified on the specified ports.

### Dependencies:
- There are no external dependencies.

### Notes:
- If the service does not return a banner, the script will indicate that no banner was found.

---
This project brings together essential tools for network security, enabling everything from host detection to detailed identification of systems and services. With the use of `scapy` and `nmap`, it automates vulnerability scanning and strengthens the response to potential threats. These solutions make the process more agile and accurate, helping to protect critical infrastructures against attacks. As a result, the project becomes a valuable resource in network defense.