<!-- $theme: gaia -->

<!-- $size: 16:9 -->

<!-- page_number: true -->

<!-- footer: Copyright (c) by Bjoern Kimminich | Licensed under CC-BY-SA 4.0 -->

# Sensitive Data

---

# Sensitive Data

> Sensitive data such as **passwords, credit card numbers, health records, personal information and business secrets** require extra protection, particularly if that data falls under privacy laws (EU's General Data Protection Regulation GDPR), financial data protection rules such as PCI Data Security Standard (PCI DSS) or other regulations. \[[^1]\]

[^1]: https://www.owasp.org/images/b/bc/OWASP_Top_10_Proactive_Controls_V3.pdf

---

## [Personal Data](https://ec.europa.eu/info/law/law-topic/data-protection/reform/what-personal-data_en) as defined in GDPR

* Name and surname
* Home address
* Email address
* Identification card number
* Location data (for example on a mobile phone)
* Internet Protocol (IP) address
* ...

_**§** Articles 2, 4(1) and(5) and Recitals (14), (15), (26), (27), (29) and (30)_

---

## [Sensitive Personal Data](https://ec.europa.eu/info/law/law-topic/data-protection/reform/rules-business-and-organisations/legal-grounds-processing-data/sensitive-data/what-personal-data-considered-sensitive_en) as defined in GDPR

* Personal data revealing racial or ethnic origin, political opinions, religious or philosophical beliefs
* Trade-union membership
* Genetic data, biometric data processed solely to identify a human being
* Health-related data
* Data concerning a person's sex life or sexual orientation

_**§** Article 4(13), (14) and (15) and Article 9 and Recitals (51) to (56)_

---

<!-- *footer: -->

# [Sensitive Data Exposure](https://www.owasp.org/index.php/Top_10-2017_A3-Sensitive_Data_Exposure)

* **Failure to determine the protection needs of data**
* Transmitting data in clear text (e.g. HTTP, SMTP, FTP)
* Employing old or weak cryptographic algorithms
* Using default or weak generated crypto keys
* Lack of proper key management/rotation
* Not enforcing encryption through browser directives/HTTP headers
* Lack of certificate verification

_:warning: External Internet traffic is especially dangerous!_

---

# Risk Rating

## Sensitive Data Exposure

| Exploitability                 | Prevalence              | Detecability                   | Impact              | Risk                                                                         |
|:-------------------------------|:------------------------|:-------------------------------|:--------------------|:-----------------------------------------------------------------------------|
| :large_orange_diamond: Average | :red_circle: Widespread | :large_orange_diamond: Average | :red_circle: Severe | [A3](https://www.owasp.org/index.php/Top_10-2017_A3-Sensitive_Data_Exposure) |
| ( **2**                        | + **3**                 | + **2** ) / 3                  | * **3**             | = **7.0**                                                                    |

---

# [Prevention](https://www.owasp.org/index.php/Top_10-2017_A3-Sensitive_Data_Exposure)

* **Classify data in system** and determine sensitivity level
* **Don't store sensitive data unnecessarily**
* Encrypt data at rest
* Ensure up-to-date and strong
  * Standard algorithms
  * Protocols
  * Keys
* Encrypt data in transit (e.g. [TLS](01-06-encryption.md)) and enforce encryption (e.g. HSTS)

---

## [HTTP Strict Transport Security (HSTS)](https://www.owasp.org/index.php/HTTP_Strict_Transport_Security_Cheat_Sheet)

> HTTP Strict Transport Security (HSTS) is an opt-in security enhancement that is specified by a web application through the use of a special response header. Once a supported browser receives this header that browser will prevent any communications from being sent over HTTP to the specified domain and will instead send all communications over HTTPS. It also prevents HTTPS click through prompts on browsers.

##### Example

```http
Strict-Transport-Security: max-age=16070400; includeSubDomains
```

---

## [Secure Cryptographic Storage Design](https://www.owasp.org/index.php/Cryptographic_Storage_Cheat_Sheet)

* Only store sensitive data that you need
* Use strong approved Authenticated Encryption
* Store a one-way and salted value of passwords
* Ensure that the cryptographic protection remains secure even if access controls fail
* Ensure that any secret key is protected from unauthorized access
* Follow applicable regulations on use of cryptography

---

### [Best Practices](https://www.owasp.org/index.php/Cryptographic_Storage_Cheat_Sheet#Architectural_Decision) (as of 2018)

| Scenario                | Practice                       | Key Length |
|:------------------------|:-------------------------------|:-----------|
| Key exchange            | Diffie–Hellman                 | 2048+ bits |
| Message Integrity       | HMAC-SHA2                      |            |
| Message Hash            | SHA2                           | 256 bits   |
| Asymetric encryption    | RSA                            | 2048 bits  |
| Symmetric-key algorithm | AES                            | 128 bits   |
| Password Hashing        | Argon2, PBKDF2, Scrypt, Bcrypt |            |

---

# Exercise 6.1

1. Access a confidential document (:star:)
2. Retrieve as many clear text user passwords as you can (:interrobang:)

##### Bonus exercises on cryptography (_optional_)

3. Visit the Token Sale page before it officially goes live (:star::star::star:)
4. Retrieve both the :rabbit2: easter eggs (:star::star::star::star:)
5. Solve the steganography challenge (:star::star::star::star:)
6. Solve the non-existent challenge \#99 (:star::star::star::star::star::star:)