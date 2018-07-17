<!-- $theme: gaia -->

<!-- $size: 16:9 -->

<!-- page_number: true -->

<!-- footer: Copyright (c) by Bjoern Kimminich | Licensed under CC-BY-SA 4.0 -->

# Insecure Dependencies

---

# Risk Rating

## Using Components with Known Vulnerabilities

| Exploitability                 | Prevalence              | Detecability                   | Impact                          | Risk                                                                                             |
|:-------------------------------|:------------------------|:-------------------------------|:--------------------------------|:-------------------------------------------------------------------------------------------------|
| :large_orange_diamond: Average | :red_circle: Widespread | :large_orange_diamond: Average | :large_orange_diamond: Moderate | [A9](https://www.owasp.org/index.php/Top_10-2017_A9-Using_Components_with_Known_Vulnerabilities) |
| ( **2**                        | + **3**                 | + **2** ) / 3                  | * **2**                         | = **4.7**                                                                                        |

---

# Insecure Configuration

---

# [Common Mistakes](https://www.owasp.org/index.php/Top_10-2017_A6-Security_Misconfiguration)

* **Missing appropriate security hardening** across application stack
* Improperly configured permissions on cloud services
* **Unnecessary features are enabled or installed**
* **Default accounts** and their passwords **still enabled** and unchanged
* Overly informative error messages (e.g. revealing stack traces)
* Latest security features are disabled or not configured securely
* No proper security headers or directives configured on server
* Software is out of date or vulnerable (see [Insecure Dependencies](#insecure-dependencies))

---

# Potential Impact

* Unauthorized access to
  * system data
  * functionality
* Complete system compromise
  * e.g. by installing a web shell or backdoor

_:information_source: Especially information leakage from error message can often be useful to attackers in subsequent attacks like Injection or Privilege Escalation._

---

# Risk Rating

## Security Misconfiguration

| Exploitability    | Prevalence              | Detecability      | Impact                          | Risk                                                                           |
|:------------------|:------------------------|:------------------|:--------------------------------|:-------------------------------------------------------------------------------|
| :red_circle: Easy | :red_circle: Widespread | :red_circle: Easy | :large_orange_diamond: Moderate | [A6](https://www.owasp.org/index.php/Top_10-2017_A6-Security_Misconfiguration) |
| ( **3**           | + **3**                 | + **3** ) / 3     | * **2**                         | = **6.0**                                                                      |
---

# Web Shells

> **A web shell is a script that can be uploaded to a web server to enable remote administration of the machine.** Infected web servers can be either Internet-facing or internal to the network, where the web shell is used to pivot further to internal hosts.
>
> **A web shell can be written in any language that the target web server supports.** The most commonly observed web shells are written in languages that are widely supported, such as PHP and ASP. Perl, Ruby, Python, and Unix shell scripts are also used. \[[^1]\]

---

> Using network reconnaissance tools, **an adversary can identify vulnerabilities that can be exploited and result in the installation of a web shell.** For example, these vulnerabilities can exist in content management systems (CMS) or web server software.
> 
> Once successfully uploaded, **an adversary can use the web shell to leverage other exploitation techniques to escalate privileges and to issue commands remotely.** These commands are directly linked to the privilege and functionality available to the web server and may include the ability to add, delete, and execute files as well as the ability to run shell commands, further executables, or scripts. \[[^1]\]

[^1]: https://www.us-cert.gov/ncas/alerts/TA15-314A

---

# [Shodan](https://www.shodan.io)

> **Shodan is a search engine for Internet-connected devices.** Web search engines, such as Google and Bing, are great for finding websites. But what if you're interested in measuring which countries are becoming more connected? Or if you want to know which version of Microsoft IIS is the most popular? Or you want to find the control servers for malware? Maybe a new vulnerability came out and you want to see how many hosts it could affect? Traditional web search engines don't let you answer those questions. \[[^2]\]

![Shodan Logo](images/02-07-insecure_dependencies_and_configuration/shodan-logo.png)

---

> Shodan gathers information about all devices directly connected to the Internet. **If a device is directly hooked up to the Internet then Shodan queries it for various publicly-available information.** The types of devices that are indexed can vary tremendously: ranging from small desktops up to nuclear power plants and everything in between.
>
> So what does Shodan index then? **The bulk of the data is taken from _banners_, which are metadata about a software that's running on a device**. This can be information about the server software, what options the service supports, a welcome message or anything else that the client would like to know before interacting with the server. \[[^2]\]

---

## Areas of application for Shodan services

> * **Network Security**: keep an eye on all devices at your company that are facing the Internet
> * **Market Research**: find out which products people are using in the real-world
> * **Cyber Risk**: include the online exposure of your vendors as a risk metric
> * **Internet of Things**: track the growing usage of smart devices
> * **Tracking Ransomware**: measure how many devices have been impacted by ransomware \[[^2]\]

[^2]: https://help.shodan.io/the-basics/what-is-shodan

---

## Shodan Query Syntax

:wrench: **TODO**

---

# Exercise 7.2

1. Perform some Shodan searches for Internet-connected devices related to your own university (e.g. nordakademie.de)
2. Perform Shodan research on your current employer