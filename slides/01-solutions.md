<!-- theme: default -->
<!-- paginate: true -->
<!-- footer: Copyright (c) by **Bjoern Kimminich** | Licensed under [CC-BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) -->
# Solutions

## Exercises 1st Semester

---

# Exercise 1.1 (Attacker Stereotypes)

| Name                | Characteristics / Motivation                                                 | Danger                  |
|:--------------------|:-----------------------------------------------------------------------------|:------------------------|
| **Script Kiddie**   | Bragging rights & wreaking havoc                                             | :skull:                 |
| **Hacktivists**     | (Pseudo-)political & social goals                                            | :skull::skull:          |
| **Competitors**     | Defamation & industrial espionage                                            | :skull::skull:          |
| **Organized Crime** | Monetization, e.g. extortion & fraud<br>(Providing Cyber-Crime-as-a-Service) | :skull::skull:(:skull:) |
| **Evil Employees**  | Revenge & corruption<br>Dangerous insider knowledge                          | :skull::skull::skull:   |
| **Nation States**   | Power! Unlimited resources & budget                                          | :skull:x100             |

---

# Exercise 2.1 (Threats to Security Goals)

| Threat                      | C                  | I                  | A                  |
|:----------------------------|:-------------------|:-------------------|:-------------------|
| Network Sniffing            | :heavy_check_mark: |                    |                    |
| DDoS Attack                 |                    |                    | :heavy_check_mark: |
| Rogue WiFi Access Point     | :heavy_check_mark: | :heavy_check_mark: |                    |
| Electromagnetic Pulse (EMP) |                    |                    | :heavy_check_mark: |
| Whistleblower               | :heavy_check_mark: |                    |                    |
| Social Engineering          | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |

---

### Exercise 2.2 (CIA³ Measures)

| Security Goal   | Technical Measures                                                                                                            | Organizational Measures                                                  |
|:----------------|:------------------------------------------------------------------------------------------------------------------------------|:-------------------------------------------------------------------------|
| Confidentiality | e.g. AES/RSA, HTTPS, [Tor](https://www.torproject.org/), 2FA                                                                  | e.g. Anonymous Payment Systems, Access Restrictions, Data Classification |
| Integrity       | e.g. SHA2, HSTS, MACs, PGP/GPG, Blockchain                                                                                    | e.g. Version Control, Access Logs                                        |
| Availability    | e.g. Load Balancer, [Circuit Breaker Pattern](https://martinfowler.com/bliki/CircuitBreaker.html), Heartbeat Monitoring, RAID | e.g. 24/7 Support, On-Call-Duty, SLAs                                    |

---

| Security Goal  | Technical Measures         | Organizational Measures                                                      |
|:---------------|:---------------------------|:-----------------------------------------------------------------------------|
| Accountability | :interrobang:              | e.g. Security Policies, Risk Assessments, RACI Matrix, Segregation of Duties |
| Assurance      | e.g. Vulnerability Scanner | e.g. KPIs, Customer/Supplier Audits, Penetration Test, Red Team              |

---

### Exercise 3.2 (Javascript Trojan)

1. Default Internet browser is opened (as it is probably bound to open
   `.html` files on most computers)
2. The JavaScript is executed resulting in the effective code
   `document["location"]=http://enjoyyourhaircut.com/5.html;` being run
3. The browser is redirected to <http://enjoyyourhaircut.com/5.html>
   (which does not exist any more)

---

![Relevant code sections of the JavaScript virus](images/01-03-malware/enjoy-your-haircut.png)

_:information_source: Only the yellow code sections are relevant as the
payload. The rest is merely obfuscation to prevent detection by AV
software!_

---

### Exercise 7.1 (Attack Tree: Access Building)

```md
1. Go through a door
  a. When it’s unlocked:
    i. Get lucky.
    ii. Obstruct the latch plate (the “Watergate Classic”).
    iii. Distract the person who locks the door at night.
  b. Drill the lock.
  c. Pick the lock.
  d. Use the key.
    i. Find a key.
    ii. Steal a key.
    iii. Photograph and reproduce the key.
    iv. Social engineer a key from someone.
      1. Borrow the key.
      2. Convince someone to post a photo of their key ring.
  e. Social engineer your way in.
    i. Act like you’re authorized and follow someone in.
    ii. Make friends with an authorized person.
    iii. Carry a box, a cup of coffee in each hand, etc.
```

---

<!-- _footer: Shostack, A. (2014) Threat Modeling: Designing for Security, Wiley -->
```md
2. Go through a window.
  a. Break a window.
  b. Lift the window.
3. Go through a wall.
  a. Use a sledgehammer or axe.
  b. Use a truck to go through the wall.
4. Gain access via other means.
  a. Use a fi re escape.
  b. Use roof access from a helicopter (preferably black) or adjacent
     building.
  c. Enter another part of the building, using another tenant’s access.
```

---

### Exercise 7.2 (Threat Boundaries)

![Sample Web Application Threat Boundaries](images/01-solutions/sample_webapp_threat-boundaries.png)
