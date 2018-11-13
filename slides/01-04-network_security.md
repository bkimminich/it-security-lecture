<!-- $theme: gaia -->

<!-- $size: 16:9 -->

<!-- page_number: true -->

<!-- footer: Copyright (c) by Bjoern Kimminich | Licensed under CC-BY-SA 4.0 -->

# Network Security

---

# OSI Network Layer Model
#### (repetition from [Technische Grundlagen der Informatik 2](https://www.nordakademie.de/bewerber/studienangebote/angewandte-informatik-bsc/studienplan/?tx_nacurriculum_nacurriculum%5Bid%5D=352&tx_nacurriculum_nacurriculum%5Bdate%5D=&tx_nacurriculum_nacurriculum%5Baction%5D=show&tx_nacurriculum_nacurriculum%5Bcontroller%5D=Studienplan&cHash=49faa9a950a1c7f9584e860140930247))

--- 

<!-- *footer: Shqip: Zbatimi i Niveleve OSI, 2010 Rexhep-bunjaku, used under CC-BY-SA 3.0 -->

![OSI Network Layer Model](images/01-04-network_security/Wwww2.jpg)

---

<!-- *footer: OSI User Layers, 2013 Gvseostud, used under CC-BY-SA 3.0 -->

# OSI User Layers

![OSI User Layers](images/01-04-network_security/OSI_user_layers.png)

---

# [Wireshark](https://www.wireshark.org)

> Wireshark is the world's foremost and widely-used network protocol analyzer. It lets you see what's happening on your network at a microscopic level and is the de facto (and often de jure) standard across many commercial and non-profit enterprises, government agencies, and educational institutions. Wireshark development thrives thanks to the volunteer contributions of networking experts around the globe and is the continuation of a project started by Gerald Combs in 1998.

![Wireshark logo](images/01-04-network_security/wireshark_logo.png)

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

_:information_source: You might be better off performing this exercise on a privately owned laptop, because campus computers might not allow installation of Wireshark._

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

# VPN Architecture

> Using VPNs, an organization can help **secure private network traffic over an unsecured network**, such as the Internet. VPN helps provide a secure mechanism for encrypting and encapsulating private network traffic and moving it through an intermediate network. **Data is encrypted for confidentiality**, and **packets** that might be intercepted on the shared or public network **are indecipherable** without the correct encryption keys. Data is also encapsulated, or wrapped, with an IP header containing routing information. \[[^1]\]

---

# VPN Scenarios

* **Remote Access VPN**: \[...\] Single computer user who connects to a private network from a remote location. The VPN server provides access to the resources of the network to which the VPN server is connected.
* **Site-to-Site VPN**: \[...\] Connects two portions of a private network or two private networks. \[...\] Allows an organization to have routed connections with separate offices, or with other organizations, over the Internet. \[...\] The VPN server provides a routed connection to the network to which the VPN server is attached. \[[^1]\]

---

<!-- *footer: How VPN Works, Windows Server 2003 Technical Reference, (c) 2009 Microsoft -->

# Remote Client to a Private Intranet

![VPN Connecting a Remote Client to a Private Intranet](images/01-04-network_security/vpn_remote-to-intranet.gif)

---

# Remote Client to a Private Intranet

> A remote access VPN connection over the Internet enables a remote access client to initiate a dial-up connection to a local ISP instead of connecting to a corporate or outsourced network access server (NAS). By using the established physical connection to the local ISP, the remote access client initiates a VPN connection across the Internet to the organization’s VPN server. When the VPN connection is created, the remote access client can access the resources of the private intranet. \[...\] \[[^1]\]

---

<!-- *footer: How VPN Works, Windows Server 2003 Technical Reference, (c) 2009 Microsoft -->

# Two Remote Sites Across the Internet

> <small>When networks are connected over the Internet, as shown in the following figure, a router forwards packets to another router across a VPN connection. To the routers, the VPN connection operates as a data-link layer link. \[[^1]\]</small>

![VPN Connecting Two Remote Sites Across the Internet](images/01-04-network_security/vpn_two-sites.gif)

---

<!-- *footer: How VPN Works, Windows Server 2003 Technical Reference, (c) 2009 Microsoft -->

# Remote Access to a Secured Network over an Intranet

![VPN Connecting a Remote Client to a Private Intranet](images/01-04-network_security/vpn_hidden-site-via-intranet.gif)

---

<!-- *footer: -->

# Remote Access to a Secured Network over an Intranet

> In some organization intranets, the data of a department, such as human resources, is so sensitive that the network segment of the department is physically disconnected from the rest of the intranet. While this protects the data of the human resources department, it creates information accessibility problems for authorized users not physically connected to the separate network segment.
> 
> VPN connections help provide the required security to enable the network segment of the human resources department to be physically connected to the intranet. \[...\] \[[^1]\]

---

<!-- *footer: How VPN Works, Windows Server 2003 Technical Reference, (c) 2009 Microsoft -->

# Connecting Two Networks over an Intranet

![VPN Connecting a Remote Client to a Private Intranet](images/01-04-network_security/vpn_hidden-to-hidden.gif)

[^1]: https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2003/cc779919(v=ws.10)

---

<!-- *footer: -->

# Connecting Two Networks over an Intranet

> Two networks can be connected over an intranet using a site-to-site VPN connection. This type of VPN connection might be necessary, for example, for two departments in separate locations, whose data is highly sensitive, to communicate with each other. For instance, the finance department might need to communicate with the human resources department to exchange payroll information.
>
> The finance department and the human resources department are connected to the common intranet with computers that can act as VPN clients or VPN servers. \[...\] \[[^1]\]

---

# Exercise 4.3 (:house:)

1. Find out if your university (or company) is offering remote access via VPN and request access
2. Set up a VPN connection from your private computer (in your home network) and test the connection
3. Which protocols does your university (or company) VPN use for
   * Tunneling
   * Authentication
   * Encryption?
4. Elaborate how these protocols work together to provide a VPN (:pen:)

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
