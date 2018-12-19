<!-- $theme: gaia -->

<!-- $size: 16:9 -->

<!-- page_number: true -->

<!-- footer: Copyright (c) by Bjoern Kimminich | Licensed under CC-BY-SA 4.0 -->

# Penetration Testing

---

# Penetration Testing

> A penetration test, or "pen test" is an attempt to evaluate the security of IT infrastructures using a controlled environment to safely attack, identify, and exploit vulnerabilities. These vulnerabilities may exist in operating systems, services, networks, and application. They may also exist due to improper configurations or risky end-user behavior.
>
>  Penetration testing assessments are also useful in validating the efficacy of defensive mechanisms and determining how well end-users adhere to security policies. \[[^1]\]

[^1]: https://www.secureauth.com/products/penetration-testing

---

<!-- footer: The Penetration Testing Execution Standard, used under GNU Free Documentation License 1.2 -->

# [Penetration Test Phases](http://www.pentest-standard.org/index.php/Main_Page)

1. Pre-engagement Interactions
2. Intelligence Gathering
3. Threat Modeling
4. Vulnerability Analysis
5. Exploitation
6. Post Exploitation
7. Reporting

---

# [1. Pre-engagement Interactions](http://www.pentest-standard.org/index.php/Pre-engagement)

* [Scoping Meeting](http://www.pentest-standard.org/index.php/Pre-engagement#Scoping_Meeting)
* [Questionaires](http://www.pentest-standard.org/index.php/Pre-engagement#Questionnaires) for different scopes (Network, Web Application, WiFi, Physical, Social Engineering)
* Framing conditions ([Start & end date](http://www.pentest-standard.org/index.php/Pre-engagement#Specify_Start_and_End_Dates), [IP ranges & domains](http://www.pentest-standard.org/index.php/Pre-engagement#Specify_IP_Ranges_and_Domains), [dealing with 3rd parties](http://www.pentest-standard.org/index.php/Pre-engagement#Dealing_with_Third_Parties) etc.)
* [Emergency Contact Information](http://www.pentest-standard.org/index.php/Pre-engagement#Emergency_Contact_Information)
* **[Rules of Engagement](http://www.pentest-standard.org/index.php/Pre-engagement#Rules_of_Engagement)**

---

# [2. Intelligence Gathering](http://www.pentest-standard.org/index.php/Intelligence_Gathering)

* Choose appropriate level of Intelligence Gathering
  * Level 1: Compliance Driven <small>(base minimum, mostly automated through tools)</small>
  * Level 2: Best Practice <small>(L1 + manual analysis e.g. business understanding, org chart, etc.)</small>
  * Level 3: State Sponsored <small>(L1 + L2 + heavy manual analysis e.g. cultivating relationships on social networks, deep understanding of business relationships, etc.)</small>

---

## Intelligence Gathering Aspects

* [OSINT](http://www.pentest-standard.org/index.php/Intelligence_Gathering#OSINT)
* [Covert Gathering](http://www.pentest-standard.org/index.php/Intelligence_Gathering#Covert_Gathering) (Corporate / HUMINT)
* [Footprinting](http://www.pentest-standard.org/index.php/Intelligence_Gathering#Footprinting)
* [Identify Protection Mechanisms](http://www.pentest-standard.org/index.php/Intelligence_Gathering#Identify_Protection_Mechanisms)

---

# [3. Threat Modeling](http://www.pentest-standard.org/index.php/Threat_Modeling)

* [Business Asset Analysis](http://www.pentest-standard.org/index.php/Threat_Modeling#Business_Asset_Analysis) (e.g. policies, product or financial data, technical information, employee or customer data)
* [Business Process Analysis](http://www.pentest-standard.org/index.php/Threat_Modeling#Business_Process_Analysis) (including IT, HR or 3rd party support processes)
* [Threat Agents/Community Analysis](http://www.pentest-standard.org/index.php/Threat_Modeling#Threat_Agents.2FCommunity_Analysis) (see [Attackers Exercise](01-01-motivation.md#exercise-11-))
* [Threat Capability Analysis](http://www.pentest-standard.org/index.php/Threat_Modeling#Threat_Capability_Analysis) (e.g. used tools or availability of relevant exploits)
* [Motivation Modeling](http://www.pentest-standard.org/index.php/Threat_Modeling#Motivation_Modeling) (e.g. direct vs. indirect profit, grudge, fun/reputation, springboard)

---

# [4. Vulnerability Analysis](http://www.pentest-standard.org/index.php/Vulnerability_Analysis)

> Vulnerability testing is the process of discovering flaws in systems and applications which can be leveraged by an attacker. These flaws can range anywhere from host and service misconfiguration, or insecure application design. Although the process used to look for flaws varies and is highly dependent on the particular component being tested, some key principals apply to the process.
>
> When conducting vulnerability analysis of any type the tester should properly scope the testing for applicable depth and breadth to meet the goals and/or requirements of the desired outcome.

---

> \[...\] Once a vulnerability has been reported in a target system, it is necessary to determine the accuracy of the identification of the issue, and to research the potential exploitability of the vulnerability within the scope of the penetration test.

### Types of vulnerability analysis

* Active, e.g.
  * automated application scans
  * banner grabbing
  * network scans
* Passive (metadata analysis and traffic monitoring)

---

# 5. Exploitation

:wrench: **TODO**

---

# 6. Post Exploitation

:wrench: **TODO**

---

# 7. Reporting

:wrench: **TODO**

---

<!-- footer: Copyright (c) by Bjoern Kimminich | Licensed under CC-BY-SA 4.0 -->

# Bug Bounty Programs

:wrench: **TODO**

---

# [Web Security Policies](https://tools.ietf.org/html/draft-foudil-securitytxt-04) <small>(`security.txt`)</small>

> When security risks are discovered by independent security researchers, they often lack the channels to disclose them properly. As a result, security issues may be left unreported.  This document defines a standard ("security.txt") to help organizations describe the process for security researchers to follow in order to disclose security vulnerabilities securely.

---

## Fields of `security.txt`

* **Contact**: An address that researchers should use for reporting security issues
* **Encryption**: Encryption key that security researchers should use for encrypted communication
* **Acknowledgements**: Link to a page where security researchers are recognized for their reports
* **Permission**: Value `none` indicates to security researchers that they must not perform any kind of testing. Must not be interpreted as having any legal value.

---

* **Policy**: Link to where your security policy and/or disclosure policy is located
* **Signature**: Full URI of an external signature file that can be used to check the authenticity of a `security.txt` file
* **Hiring**: Linking to the vendor's security-related job positions

Example: <https://securitytxt.org/.well-known/security.txt>

---

<!-- *footer: red vs blue, 2014 Robert Couse-Baker, used under CC-BY 2.0 -->

# Red vs. Blue

![Red vs. Blue](images/01-06-security_mgmt_and_org/red-vs-blue.jpg)

---

## [Red Team](https://danielmiessler.com/study/red-blue-purple-teams/)

> **Red Teams** are external entities brought in to test the effectiveness of a security program. This is accomplished by emulating the behaviors and techniques of likely attackers in the most realistic way possible. The practice is similar, but not identical to, penetration testing, and involves the pursuit of one or more objectives.

---

## [Blue Team](https://danielmiessler.com/study/red-blue-purple-teams/)

> **Blue Teams** refer to the internal security team that defends against both real attackers and Red Teams. Blue Teams should be distinguished from standard security teams in most organizations, as most security operations teams do not have a mentality of constant vigilance against attack, which is the mission and perspective of a true Blue Team.

---

# Project Zero (Google)

:wrench: **TODO**