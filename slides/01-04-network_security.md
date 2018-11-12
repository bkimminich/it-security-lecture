<!-- $theme: gaia -->

<!-- $size: 16:9 -->

<!-- page_number: true -->

<!-- footer: Copyright (c) by Bjoern Kimminich | Licensed under CC-BY-SA 4.0 -->

# Network Security

---

# [Wireshark](https://www.wireshark.org)

> Wireshark is the world’s foremost and widely-used network protocol analyzer. It lets you see what’s happening on your network at a microscopic level and is the de facto (and often de jure) standard across many commercial and non-profit enterprises, government agencies, and educational institutions. Wireshark development thrives thanks to the volunteer contributions of networking experts around the globe and is the continuation of a project started by Gerald Combs in 1998.

---

# Wireshark Features <small>(Excerpt)</small>

> * Deep inspection of hundreds of protocols
> * Live capture and offline analysis
> * Rich VoIP analysis
> * Live data can be read from Ethernet, IEEE 802.11, PPP/HDLC, ATM, Bluetooth, USB, Token Ring, Frame Relay, FDDI, and others (depending on your platform)
> * Decryption support for many protocols, including IPsec, ISAKMP, Kerberos, SNMPv3, SSL/TLS, WEP, and WPA/WPA2

---

# Exercise 4.1

1. Install Wireshark from <https://www.wireshark.org/#download>
2. Click _Start capturing packets_
3. Spend a few minutes surfing the Internet (the way you usually do)
4. Click _Stop capturing packets_
5. Use _File > Save as..._ to save your captured network traffic

---

# Exercise 4.2

1. Open your previously saved `.pcapng` file
2. Set `http` as a filter
3. Use _Find a packet_ to search for the _String_ `password` within the _Packet details_ (see screenshot below)

![Wireshark Filter for HTTP requests containing "password"](images/01-04-network_security/wireshark-filter.png)

---

<!-- *footer:  -->

![Wireshark found a password](images/01-04-network_security/wireshark-found-password.png)

---

# VPN

## (Virtual Private Network)

---

# WLAN

## (Wireless Local Area Network)

---

# Network Firewall

---

# IDS/IPS

## (Intrusion Detection/Prevention System)

---

# WAF

## (Web Application Firewall)

---

<!-- *footer: -->

# Web Application Firewall (WAF)

> A web application firewall (WAF) is an application firewall for HTTP applications. It applies a set of rules to an HTTP conversation. Generally, these rules cover common attacks such as cross-site scripting (XSS) and SQL injection.
>
> While proxies generally protect clients, WAFs protect servers. A WAF is deployed to protect a specific web application or set of web applications. A WAF can be considered a reverse proxy.
>
> WAFs may come in the form of an appliance, server plugin, or filter, and may be customized to an application. The effort to perform this customization can be significant and needs to be maintained as the application is modified. \[[^8]\]

[^8]: https://www.owasp.org/index.php/Web_Application_Firewall

---

<!-- *footer: Simple Web Application Firewall Architecture, 2018 M2farah, used under CC-BY-SA 4.0 -->

# WAF Deployment in the Network

![Simple Web Application Firewall Architecture](images/02-09-sdlc/WAF_Archi.png)

<small>:bulb: _An application should be able to protect itself! Use a WAF only as a secondary defense mechanism to achieve [Defense in Depth](#principle-of-defense-in-depth)! For legacy systems (with no feasible way to patch directly) a WAF can be the main protection mechanism._</small>

---

<!-- *footer: -->

# [Risk in the use of WAFs](https://www.owasp.org/index.php?title=Category:OWASP_Best_Practices:_Use_of_Web_Application_Firewalls)

* "Yet-another-proxy" (increased complexity of the IT infrastructure)
* Organisational tasks
* Training the WAF on each new release of the web application
* Testing
* False positives (which may have a significant business impact)
* More complex troubleshooting
* WAFs also have/generate errors
* Responsibility for system-wide error situations
* Cost-effectiveness

---

# WAF Modes

* **Blocking Mode**: Normal operational mode where the WAF blocks requests it identified as malicious.
* **Monitoring Mode**: The WAF logs alerts but does not block the corresponding requests.
* **Learning Mode**: The WAF learns from good traffic (e.g. by whitelisted IPs) what the normal use cases and input are.

:bulb: _Learning Mode might lead to false positives on new application releases when the WAF did not learn any traffic for new functionality._
