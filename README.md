# Wireshark Traffic Analysis Lab



**Objective:**
This lab focused on using Wireshark to monitor, analyze, and filter network traffic to gain insights into packet-level data. The key goals were to understand the differentiation of port resolutions, effectively apply filters by source/destination IPs, ports, and protocols, along with understanding how to resolve ports and analyze transaction IDs.
#

**Key Skills Demonstrated:**


Packet Capture and Analysis:
- Analyzed inbound and outbound traffic:

   - Inspected PCAP files to examine both incoming and outgoing network traffic.

- Differentiated between resolved and unresolved ports in packet details:
    - **Resolved Ports:** Wireshark maps port numbers to known service names (e.g., HTTP for port 80, HTTPS for port 443, SSH for port 22).
    - **Unresolved Ports:** Numeric port numbers are displayed when no associated service name is found (e.g., port 12345 without a name).

##

**Filtering Network Traffic:**

Filters are crucial for narrowing down specific types of traffic in Wireshark. Below are examples of how filters were applied during the lab:
 
- **SMTP and ICMP Traffic:** Used this filter to capture SMTP and ICMP traffic:

        tcp.port eq 25 or icmp

- **Source IP Address:** Filtered all packets originating from a specific IP address (e.g., 10.10.60.1):

        ip.src == 10.10.60.1

- **Destination IP Address:** Filtered packets sent to the IP 31.13.50.22:

        ip.dst == 31.13.50.22

- **Specific Port Traffic:** Isolated HTTP traffic on port 80:
  
        tcp.port == 80

- **SMTP Traffic Containing Specific Text:** Isolated SMTP packets containing the text “Ella:” in the payload:

        smtp && frame contains "Ella: "

- **UDP Traffic from Multiple Source Ports:** Displayed packets originating from UDP source ports 53, 59015, and 63518:

        udp.srcport == 53 || udp.srcport == 59015 || udp.srcport == 63518

##

**Combining Filters:**

- **Packets Sent from a Specific IP Excluding a Port:** Example filter to show packets sent from 10.6.5.102 not on port 80:

        ip.src == 10.6.5.102 && ! tcp.port == 80

<img width="961" alt="image" src="https://github.com/user-attachments/assets/71233020-6e7b-4849-9175-e7d619b352e0">

##

**Transaction ID Identification:**

- **Finding Transaction IDs:** Transaction IDs are typically found in DNS (Domain Name System) requests. To capture this, I used the filter:

        udp.dstport == 59485 && ip.dst == 10.6.5.102
I then selected the DNS packet and expanded it to view the transaction ID.

<img width="964" alt="image" src="https://github.com/user-attachments/assets/e4feb57f-e71d-4a1e-a206-7443b0d4bcb5">

##

**Web Traffic Filters:**

- **Display All Web Traffic:** Filtered HTTP or SSL traffic using:

          http.request || ssl.handshake.type == 1

- **Further Filters Using TCP Flags and Excluding Port 25:** Combined filters for specific TCP flags and exclusions:

          (http.request || ssl.handshake.type == 1) || (tcp.flags == 0x0002) && !(tcp.port == 25)

Alternately, the filter can also be written as:

        (http.request || ssl.handshake.type == 1) or (tcp.flags == 0x0002) and !(tcp.port == 25)


- **Filtering with DNS Traffic:** To include DNS traffic, I modified the filter as:

          (http.request || ssl.handshake.type == 1) || (tcp.flags == 0x0002 || dns) && !(tcp.port == 25)

##

**Wireshark Statistics and Analysis:**

Wireshark provides statistical tools that can help track key network metrics. These include insights into endpoints, conversations, and resolved addresses.

- Endpoint Statistics:

    - To find the amount of IPv4 endpoints in a capture file, I clicked on Statistics > Endpoints.

- Conversation Statistics:

    - To track IPv4 conversations in a capture file, I accessed Statistics > Conversations.

- Resolved Host Names:

    - To find the resolved host name of an IP address, I used Statistics > Resolved Addresses and typed the IP address in the host field.

<img width="615" alt="image" src="https://github.com/user-attachments/assets/2727b668-5163-4262-8fbc-b87097bbac7a">


##

**Packet Count Analysis:**

- **Packets Sent Between IP Addresses:** To find how many packets were exchanged between 10.1.10.101 and 185.236.202.244, I entered:

        ip.addr == 10.1.10.101 && ip.addr == 185.236.202.244

The packet count appears at the bottom of the Wireshark window.

<img width="962" alt="image" src="https://github.com/user-attachments/assets/5b802854-2cce-49cf-9ade-e62a427faff5">

- **Packets Sent AND Received from an IP:** To find packets sent and received from 185.236.212.255, I applied the filter:

        ip.addr == 185.236.202.244 && tcp.port == 443

##

**Time Display Format:**

Wireshark allows the display of packet timestamps in different formats for analysis. I used the following steps to adjust the time format:

1. Go to **View > Time Display Format.**
2. Select the desired time format (e.g., seconds, date, etc.).

<img width="966" alt="image" src="https://github.com/user-attachments/assets/ba141f63-cdd7-40e6-932d-d2067ba2a120"> 

## 
**Additional Skills:**

Protocol Filtering:

Leveraged Wireshark's internal protocol database to filter by any supported protocol. A comprehensive list of protocols is accessible through:
View → Internals → Supported Protocols.

Using Reference Materials:
Utilized a Wireshark cheat sheet to ensure precise syntax for display filters.

<img width="604" alt="image" src="https://github.com/user-attachments/assets/6b414d83-c653-4e93-9206-680546f79c24">

<img width="605" alt="image" src="https://github.com/user-attachments/assets/691207f0-fe08-44a5-a10a-cd5637b1a4b9">

##
**Outcomes and Reflection:**

This lab demonstrated my ability to use Wireshark as a powerful tool for network traffic analysis. By understanding how to effectively filter traffic based on IPs, ports, protocols, and payload content, I improved my skills in network troubleshooting, cybersecurity investigations, and packet-level analysis.





