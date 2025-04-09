# CodeAlpha_NIDS
# Snort NIDS Project: ICMP & HTTP Traffic Detection

This project demonstrates a basic setup of a Network Intrusion Detection System (NIDS)using Snort to detect ICMP (ping) and HTTP (web) traffic. The system is deployed in a virtual lab using Ubuntu and Kali Linux.

---

# Project Objective

- Detect and alert on ICMP (ping) packets
- Detect and alert on HTTP requests
- Gain hands-on experience with Snort rule creation and traffic analysis

---

# Tools Used

- Ubuntu 22.04 LTS(Snort installed)
- Kali Linux(attacker machine)
- Apache2 Web Server
- Snort v3
- VirtualBox

---

# Lab Setup

Component        Configuration 

Host OS      -    Ubuntu 22.04 LTS                        
Attacker OS  -  Kali Linux                              
Network      -  Host-only Adapter (192.168.56.0/24)     
Interface    -  enp0s3 (on Ubuntu)                    

---

# Snort Configuration Steps

1. Install Snort and Apache2 on Ubuntu
2. Configure rules in /etc/snort/rules/local.rules
3. Run Snort in console mode:

sudo snort -A console -q -c /etc/snort/snort.conf -i enp0s3


4. Use Kali Linux to generate traffic


# Custom Snort Rules

* ICMP Detection Rule:**

alert icmp any any -> any any (msg: "ICMP packet detected"; sid:1000001; rev:1;)


*HTTP Detection Rule:**

alert tcp any any -> any 80 (msg:"HTTP request detected"; sid:1000004; rev:1;)-------[HTTP port is 80]

---

Testing the Rules

-From Kali Linux

| Traffic Type | Command                      | Expected Result in Snort 
|--------------|-------------------------------------|-------------------------
| ICMP         | ping <Ubuntu-IP>             | ICMP packet detected
| HTTP         | curl http://<Ubuntu-IP>      | HTTP request detected   




# Conclusion

This project successfully demonstrates Snort's capability to detect ICMP and HTTP traffic using custom rules. It serves as a foundational step toward building more advanced intrusion detection systems.
