
<!-- theme: default -->

<!-- paginate: true -->

<!-- footer: Copyright (c) by **Bjoern Kimminich** | Licensed under [CC-BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) -->

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
* [Questionaires](http://www.pentest-standard.org/index.php/Pre-engagement#Questionnaires) for different scopes
  * <small>Network, Web Application, WiFi, Physical, Social Engineering</small>
* Framing conditions
  * <small>[Start & end date](http://www.pentest-standard.org/index.php/Pre-engagement#Specify_Start_and_End_Dates), [IP ranges & domains](http://www.pentest-standard.org/index.php/Pre-engagement#Specify_IP_Ranges_and_Domains), [dealing with 3rd parties](http://www.pentest-standard.org/index.php/Pre-engagement#Dealing_with_Third_Parties) etc.</small>
* [Emergency Contact Information](http://www.pentest-standard.org/index.php/Pre-engagement#Emergency_Contact_Information)
* :scroll: **[Rules of Engagement](http://www.pentest-standard.org/index.php/Pre-engagement#Rules_of_Engagement)**

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

# [5. Exploitation](http://www.pentest-standard.org/index.php/Exploitation)

> <small>The exploitation phase of a penetration test focuses solely on establishing access to a system or resource by bypassing security restrictions. If the prior phase, vulnerability analysis was performed properly, this phase should be well planned and a precision strike.</small>

* [Avoid or bypass countermeasures](http://www.pentest-standard.org/index.php/Exploitation#Countermeasures) (e.g. AV, ASLR or WAF)
* Escape detection (e.g. evade IDS/IPS or avoid cameras)
* Precision Strike
* Tailored Exploits
* Zero-Day Angle

---

# [6. Post Exploitation](http://www.pentest-standard.org/index.php/Post_Exploitation)

> <small>The purpose of the Post-Exploitation phase is to determine the value of the machine compromised and to maintain control of the machine for later use. The value of the machine is determined by the sensitivity of the data stored on it and the machines usefulness in further compromising the network.</small>

* Infrastructure Analysis (for potential targets deeper in the network)
* Pillaging <small><small>(e.g. personal information, credit card information, passwords, etc.)</small></small>
* Data Exfiltration
* Persistence <small><small>(e.g. installation of backdoor or creating an alternate user account)</small></small>
* Cleanup (after the penetration test has been completed)

---

# [7. Reporting](http://www.pentest-standard.org/index.php/Reporting)

<small>A typical pentest reports consists of two major sections in order to communicate the objectives, methods, and results of the testing conducted to various audiences.</small>

1. **Executive Summary**: <small>Specific goals of the Penetration Test and the high level findings of the testing exercise. The intended audience will be those who are in charge of the oversight and strategic vision of the security program as well as any members of the organization which may be impacted by the identified/confirmed threats.</small>
2. **Technical Report**: <small>Technical details of the test and all of the aspects/components agreed upon as key success indicators within the pre engagement exercise. The technical report section will describe in detail the scope, information, attack path, impact and remediation suggestions of the test.</small>

---

## Risk Rating Scale

![Reporting Risk Scale](images/01-08-penetration_testing/Reporting-risk-scale.png)

---

<!-- footer: Copyright (c) by **Bjoern Kimminich** | Licensed under [CC-BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) -->

# Awesome Penetration Testing

> A collection of awesome penetration testing resources.

### https://github.com/enaqx/awesome-pentest

[![Awesome List Logo](images/01-08-penetration_testing/logo.png)](https://github.com/sindresorhus/awesome)

---

# Bug Bounty Programs

> A bug bounty program is a deal offered by many websites and software developers by which individuals can **receive recognition and compensation for reporting bugs, especially** those pertaining to **exploits and vulnerabilities**. These programs allow the developers to discover and resolve bugs before the general public is aware of them, preventing incidents of widespread abuse. \[[^2]\]

### HackerOne's list of known Bug Bounty Programs

* https://hackerone.com/bug-bounty-programs

_:moneybag: Bounties may range from recognition over swag up to >100.000$!_

[^2]: https://en.wikipedia.org/wiki/Bug_bounty_program

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

<hr>

Example: <https://securitytxt.org/.well-known/security.txt>

```
# If you would like to report a security issue
# you may report it to us on HackerOne.
Contact: https://hackerone.com/ed
Encryption: https://keybase.pub/edoverflow/pgp_key.asc
Acknowledgements: https://hackerone.com/ed/thanks
```

---

<!-- _footer: red vs blue, 2014 Robert Couse-Baker, used under CC-BY 2.0 -->

# Red vs. Blue

![Red vs. Blue](images/01-06-security_mgmt_and_org/red-vs-blue.jpg)

---

# :triangular_flag_on_post: [Red Team](https://danielmiessler.com/study/red-blue-purple-teams/) 

> **Red Teams** are external entities brought in to test the effectiveness of a security program. This is accomplished by emulating the behaviors and techniques of likely attackers in the most realistic way possible. The practice is similar, but not identical to, penetration testing, and involves the pursuit of one or more objectives.

#### Exercise 8.1 (:house:)

1. In a fight between pirates and ninjas, who would win? (:thought_balloon:)
2. Read [Penetration Test vs. Red Team Assessment](https://blog.rapid7.com/2016/06/23/penetration-testing-vs-red-teaming-the-age-old-debate-of-pirates-vs-ninja-continues/)

---

# :cop: [Blue Team](https://danielmiessler.com/study/red-blue-purple-teams/)

> **Blue Teams** refer to the internal security team that defends against both real attackers and Red Teams. Blue Teams should be distinguished from standard security teams in most organizations, as most security operations teams do not have a mentality of constant vigilance against attack, which is the mission and perspective of a true Blue Team.

> <small>A team of highly skilled individuals who conduct systematic examinations of IS or products to determine adequacy of security measures, to identify security deficiencies, to predict effectiveness of proposed security measures, and to confirm adequacy of such measures after implementation.</small> \[[^3]\]

[^3]: https://static1.squarespace.com/static/5606c039e4b0392b97642a02/t/57375967ab48de6e3b4d0015/1463245159237/dodd85701.pdf

---

# Project Zero (Google)

> Project Zero is the name of a team of security analysts employed by Google tasked with finding zero-day vulnerabilities.
>
> <small>After finding a number of flaws in software used by many end-users \[...\] Google decided to form a full-time team dedicated to finding such vulnerabilities, not only in Google software but any software used by its users.
> 
> Bugs found by the Project Zero team are reported to the manufacturer and only made publicly visible once a patch has been released or if 90 days have passed without a patch being released.</small> \[[^4]\]

#### https://googleprojectzero.blogspot.com/

[^4]: https://en.wikipedia.org/wiki/Project_Zero