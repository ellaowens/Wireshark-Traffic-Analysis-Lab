# Wireshark-Traffic-Analysis-Lab


**Objective:**
This lab focused on using Wireshark to monitor, analyze, and filter network traffic to gain insights into packet-level data. The key goals were to understand the differentiation of port resolutions, effectively apply filters, and demonstrate proficiency in network traffic analysis.
#

**Key Skills Demonstrated:**


Packet Capture and Analysis:
- Analyzed inbound and outbound traffic by inspecting a PCAP file.
- Differentiated between resolved and unresolved ports in packet details:
    - **Resolved Ports:** Wireshark maps port numbers to known service names (e.g., HTTP for port 80, HTTPS for port 443, SSH for port 22).
    - **Unresolved Ports:** Numeric port numbers are displayed when no associated service name is found (e.g., port 12345 without a name).

##

**Filtering Network Traffic:**

Filters are crucial for narrowing down specific types of traffic in Wireshark. Below are examples of how filters were applied during the lab:
 
- SMTP and ICMP Traffic:
  - Used the filter:

        tcp.port eq 25 or icmp


- Source IP Address:
  - Filtered all packets originating from a specific IP address (e.g., 10.10.60.1):

        ip.src == 10.10.60.1

- Destination IP Address:
  - Filtered packets sent to the IP 31.13.50.22:

        ip.dst == 31.13.50.22

- Specific Port Traffic:
  - Filtered packets using a specific port, such as HTTP traffic on port 80:

        tcp.port == 80

- SMTP Traffic Containing Specific Text:
  - Isolated SMTP packets containing the text “Ella:” in the payload using the filter:

        smtp && frame contains "Ella: "

- UDP Traffic from Multiple Source Ports:
  - Displayed packets originating from UDP source ports 53, 59015, and 63518:

        udp.srcport == 53 || udp.srcport == 59015 || udp.srcport == 63518

## 
**Additional Skills:**

Protocol Filtering:

Leveraged Wireshark's internal protocol database to filter by any supported protocol. A comprehensive list of protocols is accessible through:
View → Internals → Supported Protocols.

Using Reference Materials:
Utilized a Wireshark cheat sheet to ensure precise syntax for display filters.

##
**Outcomes and Reflection:**

This lab demonstrated the ability to use Wireshark as a powerful tool for network traffic analysis. By understanding how to effectively filter traffic based on IPs, ports, protocols, and payload content, I improved my skills in network troubleshooting, cybersecurity investigations, and packet-level analysis.

##
<img width="604" alt="image" src="https://github.com/user-attachments/assets/30fcbe67-8b69-4014-aecb-2c5ad1df107f">

<img width="605" alt="image" src="https://github.com/user-attachments/assets/691207f0-fe08-44a5-a10a-cd5637b1a4b9">

