<!-- $theme: gaia -->

<!-- $size: 16:9 -->

<!-- page_number: true -->

<!-- footer: Copyright (c) by Bjoern Kimminich | Licensed under CC-BY-SA 4.0 -->

# Insecure Dependencies

---

# [Common Mistakes](https://www.owasp.org/index.php/Top_10-2017_A9-Using_Components_with_Known_Vulnerabilities)

* Not knowing used version of dependencies (client- and server-side)
  * Includes directly used components _and_ nested dependencies
* **Used software is vulnerable, unsupported, or out of date**
  * Includes OS, Web/Application server, DBMS, Applications, APIs, runtime environments and libraries
* Lack of regular scans and bulletin subscriptions for vulnerabilities
* **Patch Management Process insufficient** or missing
* Component configuration not secured (see [Insecure Configuration](#insecure-configuration))

---

<!-- *footer: -->

## Variable Exploitability

* Already-written exploits for many known vulnerabilities exist
* Other vulnerabilities require a custom exploit (e.g. [Zero Day](01-01-motivation.md#zero-day)s)

## Variable Impact

* Full range of weaknesses is possible
  * RCE, Injection, Broken Access Control, XSS, etc.
* Impact could be minimal, up to host takeover and data compromise

_:information_source: Some of the largest breaches to date have relied on exploiting known vulnerabilities in components (e.g. [Equifax](01-01-motivation.md#equifax-september-2017))_

---

# Risk Rating

## Using Components with Known Vulnerabilities

| Exploitability                 | Prevalence              | Detecability                   | Impact                          | Risk                                                                                             |
|:-------------------------------|:------------------------|:-------------------------------|:--------------------------------|:-------------------------------------------------------------------------------------------------|
| :large_orange_diamond: Average | :red_circle: Widespread | :large_orange_diamond: Average | :large_orange_diamond: Moderate | [A9](https://www.owasp.org/index.php/Top_10-2017_A9-Using_Components_with_Known_Vulnerabilities) |
| ( **2**                        | + **3**                 | + **2** ) / 3                  | * **2**                         | = **4.7**                                                   

---

# [Prevention](https://www.owasp.org/index.php/Top_10-2017_A9-Using_Components_with_Known_Vulnerabilities)

* **Remove unused dependencies**, unnecessary features, components, files, and documentation
* Continuously inventory component versions and sub-dependencies
* **Continuously monitor** [CVE](https://cve.mitre.org/)/[NVD](http://web.nvd.nist.gov/view/vuln/search) etc. **for vulnerabilities**
    * e.g. with OWASP Dependency-Check, [Retire.js](https://retirejs.github.io/retire.js/) or [`npm audit`](https://docs.npmjs.com/getting-started/running-a-security-audit)
* Subscribe to email alerts for security vulnerabilities related to components you use (especially when using commercial products)
* **Only obtain components from official sources** over secure links

---

* Prefer signed packages to avoid including a modified, malicious component
* Monitor for unmaintained libraries and components
* Monitor for components that do not create security patches for older versions
* If patching is not possible, consider deploying a virtual patch
* **Ensure ongoing** monitoring, triaging, and applying **updates for the lifetime of the application** or portfolio

<!-- -->

* **Define and enforce** the above in a **Patch Management Process**

---

# [OWASP Dependency-Check](https://wiki.int.kn/display/gscgiak/OWASP+Dependency+Check)

> **Dependency-Check is a utility that identifies project dependencies and checks if there are any known, publicly disclosed, vulnerabilities.** Currently, Java and .NET are supported; additional experimental support has been added for Ruby, Node.js, Python, and limited support for C/C++ build systems (autoconf and cmake). The tool can be part of a solution to the OWASP Top 10 2017 A9:2017-Using Components with Known Vulnerabilities.

![Dependency Check Logo](images/02-07-insecure_dependencies_and_configuration/dc.svg)

---

# Exercise 7.1

1. Open the [Sample Report](https://jeremylong.github.io/DependencyCheck/general/SampleReport.html) of OWASP Dependency-Check
2. Recommend an action plan for the assessed application
    * Distinguish between _short term_ and _long term_ actions
4. Collect potential risks for a corporate-wide rollout of OWASP Dependency-Check in your company
5. Collect possible mitigations for those risks

_:bulb: If your company does not use any technology that could be assessed by OWASP Dependency-Check, simply perform the exercise pretending it actually could._

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

<!-- *footer: -->

## Shodan Query Examples

##### :x: Search in Banner Data ("Google-style")

```bash
nordakademie
# = results with "nordakademie" in banner text
```

##### Search in Meta Data with `filtername:value`

```bash
hostname:nordakademie
# = results with "nordakademie" in host name

hostname:nordakademie product:apache -hash:0
# = Apache servers answering with non-empty banners

hostname:nordakademie http.component:php http.status:200
# = available (200 "OK") servers running PHP
```
---



##### Filtering for known vulnerabilities by CVE-ID

```bash
http.component:php vuln:CVE-2018-10547
# = Servers running PHP vulnerable to Reflected XSS on some error pages
```

_:warning: The `vuln` filter is only available to academic users or Small Business API subscription and higher._

#### REST and Streaming API

see **https://developer.shodan.io/api**

#### Literature Recommendations _(optional)_

* Matherly: [Complete Guide to Shodan](https://leanpub.com/shodan), 2017

---

# Exercise 7.2

1. Get an idea of the available Shodan query filters on https://developer.shodan.io/api/banner-specification
2. Perform some Shodan searches for Internet-connected devices associated with your current employer (e.g. by `hostname` or `ip`)

<hr>

3. Use an [online test](https://www.ssllabs.com/ssltest/index.html) to check the rating of at least one SSL configuration of your employer's hosts

_:information_source: Please consider ticking the "Do not show the results on the boards" checkbox before running the online scan!_ 

---

# [Prevention](https://www.owasp.org/index.php/Top_10-2017_A6-Security_Misconfiguration)

* **Repeatable hardening process**
* Development, QA & Production environments configured identically
  * but with different credentials used in each environment
* No unnecessary features, components, documentation, and samples
* Segmented application architecture
* Sending security directives to clients, e.g. Security Headers
* **Regularly review and update configurations as part of the Patch Management Process** (see [Insecure Dependencies](#insecure-dependencies))

---

# Exercise 7.3

1. Persist a Stored XSS attack via the _Contact Us_ page (:star::star::star::star:)
2. Report the vulnerability which makes this XSS possible (:star::star::star::star:)
 
<!-- -->

3. Report another vulnerability that could be exploited in a [Software Supply Chain Attack](https://csrc.nist.gov/CSRC/media/Projects/Supply-Chain-Risk-Management/documents/ssca/2017-winter/NCSC_Placemat.pdf) (:star::star::star::star::star:)

_:information_source: To report anything to the shop, you can use the "Contact Us" page. You have to supply as detailed information as possible._

