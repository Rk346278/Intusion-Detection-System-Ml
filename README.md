Overview
This project implements a Machine Learning-based Network Intrusion Detection System (IDS) that detects anomalous network behavior using flow-level traffic analysis.
The system captures network traffic (live or from PCAP), converts packets into flow-level behavioral features using five-tuple logic, and applies an Isolation Forest model to identify suspicious flows.
This approach enables behavior-based anomaly detection without relying on predefined attack signatures.
Key Features
Live network packet capture support
PCAP file analysis support
Five-tuple flow identification:
Source IP
Destination IP
Source Port
Destination Port
Protocol
Flow-level behavioral feature engineering
Feature scaling using StandardScaler
Unsupervised anomaly detection using Isolation Forest
Suspicious IP and port reporting
Basic anomaly visualization
How It Works
1. Packet Capture
Captures traffic using Scapy (sniff)
Or reads traffic from a PCAP file (rdpcap)
2. Flow Creation
Packets are grouped into flows using five-tuple identification:
(src_ip, dst_ip, src_port, dst_port, protocol)
3. Feature Engineering
For each flow, the system extracts:
Packet count
Total bytes
Average packet size
Flow duration
Packets per second
Destination port
These features represent communication behavior rather than packet content.
4. Feature Scaling
Numerical features are scaled using StandardScaler to normalize feature ranges.
5. Anomaly Detection
An Isolation Forest model is trained to detect abnormal traffic patterns.
Flows that are isolated faster (shorter path length in trees) are marked as anomalies.
Output
The system provides:
Total flows analyzed
Number of anomalous flows
Top suspicious source IPs
Top suspicious destination ports
Histogram visualization of anomaly distribution
Tech Stack
Python
Scapy
Pandas
NumPy
Scikit-learn
Matplotlib
