<!-- theme: default -->
<!-- paginate: true -->
<!-- footer: Copyright (c) by **Bjoern Kimminich** | Licensed under [CC-BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) -->

# Cryptographic Failures

---

# Protection needs of data

> The first thing is to determine the protection needs of data in transit
> and at rest. For example, passwords, credit card numbers, health
> records, personal information, and business secrets require extra
> protection, mainly if that data falls under privacy laws, e.g., EU's
> General Data Protection Regulation (GDPR), or regulations, e.g.,
> financial data protection such as PCI Data Security Standard (PCI DSS). \[[^1]\]

[^1]: https://owasp.org/Top10/A02_2021-Cryptographic_Failures/#description

---

## [GDPR](https://publications.europa.eu/en/publication-detail/-/publication/3e485e15-11bd-11e6-ba9a-01aa75ed71a1/language-en)

> Regulation (EU) 2016/679 of the European Parliament and of the Council
> of 27 April 2016 on the protection of natural persons with regard to
> the processing of personal data and on the free movement of such data,
> and repealing Directive 95/46/EC (General Data Protection Regulation)

---

## [Personal Data](https://ec.europa.eu/info/law/law-topic/data-protection/reform/what-personal-data_en) as defined in GDPR

* Name and surname
* Home address
* Email address
* Identification card number
* Location data (for example on a mobile phone)
* Internet Protocol (IP) address
* ...

_**§** Articles 2, 4(1) and(5) and Recitals (14), (15), (26), (27), (29)
and (30)_

---

## [Sensitive Personal Data](https://ec.europa.eu/info/law/law-topic/data-protection/reform/rules-business-and-organisations/legal-grounds-processing-data/sensitive-data/what-personal-data-considered-sensitive_en) as defined in GDPR

* Personal data revealing racial or ethnic origin, political opinions,
  religious or philosophical beliefs
* Trade-union membership
* Genetic data, biometric data processed solely to identify a human
  being
* Health-related data
* Data concerning a person's sex life or sexual orientation

_**§** Article 4(13), (14) and (15) and Article 9 and Recitals (51) to
(56)_

---

## [GDPR Enforcement Tracker](https://enforcementtracker.com)

![GDPR Enforcement Tracker](images/02-06-sensitive_data/enforcementtracker.png)

---

## [PCI DSS](https://www.pcisecuritystandards.org/documents/PCIDSS_QRGv3_2.pdf)

> PCI DSS is the global data security standard adopted by the payment
> card brands for all entities that process, store or transmit
> cardholder data and/or sensitive authentication data.

---

## [PCI DSS Requirements](https://www.pcisecuritystandards.org/documents/PCIDSS_QRGv3_2.pdf)

| <small>Goals</small>                      | <small>Requirements</small>                                                  |
|:------------------------------------------|:-----------------------------------------------------------------------------|
| <small>Secure Network and Systems</small> | <small>Firewall; No default credentials</small>                              |
| <small>Protect Cardholder Data</small>    | <small>Protect stored data; encrypt transmissions</small>                    |
| <small>Vulnerability Management</small>   | <small>Anti-Malware/-Virus; Secure Development</small>                       |
| <small>Strong Access Controls</small>     | <small>Need-to-know access; Authentication; Restrict physical access</small> |
| <small>Monitoring & Testing</small>       | <small>Monitor network and data access; Test systems/processes</small>       |
| <small>Security Policy</small>            | <small>Maintain Information Security policy for all personnel</small>        |

---

# [Cryptographic Failures](https://owasp.org/Top10/A02_2021-Cryptographic_Failures)

-   Is any data transmitted in clear text? This concerns protocols such
    as HTTP, SMTP, FTP also using TLS upgrades like STARTTLS. External
    internet traffic is hazardous. Verify all internal traffic, e.g.,
    between load balancers, web servers, or back-end systems.

-   Are any old or weak cryptographic algorithms or protocols used either
    by default or in older code?

-   Are default crypto keys in use, weak crypto keys generated or
    re-used, or is proper key management or rotation missing?
    Are crypto keys checked into source code repositories?

-   Is encryption not enforced, e.g., are any HTTP headers (browser)
    security directives or headers missing?

---

-   Is the received server certificate and the trust chain properly validated?

-   Are initialization vectors ignored, reused, or not generated
    sufficiently secure for the cryptographic mode of operation?
    Is an insecure mode of operation such as ECB in use? Is encryption
    used when authenticated encryption is more appropriate?

-   Are passwords being used as cryptographic keys in absence of a
    password base key derivation function?

-   Is randomness used for cryptographic purposes that was not designed
    to meet cryptographic requirements? Even if the correct function is
    chosen, does it need to be seeded by the developer, and if not, has
    the developer over-written the strong seeding functionality built into
    it with a seed that lacks sufficient entropy/unpredictability?

---

-   Are deprecated hash functions such as MD5 or SHA1 in use, or are
    non-cryptographic hash functions used when cryptographic hash functions
    are needed?

-   Are deprecated cryptographic padding methods such as PKCS number 1 v1.5
    in use?

-   Are cryptographic error messages or side channel information
    exploitable, for example in the form of padding oracle attacks?

---

# Data Factors

## A02:2021 – Cryptographic Failures

| CWEs Mapped | Max Incidence Rate | Avg Incidence Rate | Avg Weighted Exploit | Avg Weighted Impact | Max Coverage | Avg Coverage | Total Occurrences | Total CVEs |
|:-----------:|:------------------:|:------------------:|:--------------------:|:-------------------:|:------------:|:------------:|:-----------------:|:----------:|
|     29      |       46.44%       |       4.49%        |         7.29         |        6.81         |    79.33%    |    34.85%    |      233,788      |   3,075    |

---

# [Prevention](https://owasp.org/Top10/A02_2021-Cryptographic_Failures/#how-to-prevent)

-   Classify data processed, stored, or transmitted by an application.
    Identify which data is sensitive according to privacy laws,
    regulatory requirements, or business needs.

-   Don't store sensitive data unnecessarily. Discard it as soon as
    possible or use PCI DSS compliant tokenization or even truncation.
    Data that is not retained cannot be stolen.

-   Make sure to encrypt all sensitive data at rest.

-   Ensure up-to-date and strong standard algorithms, protocols, and
    keys are in place; use proper key management.

---

-   Encrypt all data in transit with secure protocols such as TLS with
    forward secrecy (FS) ciphers, cipher prioritization by the
    server, and secure parameters. Enforce encryption using directives
    like HTTP Strict Transport Security (HSTS).

-   Disable caching for response that contain sensitive data.

-   Apply required security controls as per the data classification.

-   Do not use legacy protocols such as FTP and SMTP for transporting
    sensitive data.

-   Store passwords using strong adaptive and salted hashing functions
    with a work factor (delay factor), such as Argon2, scrypt, bcrypt or
    PBKDF2.

---

-   Initialization vectors must be chosen appropriate for the mode of
    operation.  For many modes, this means using a CSPRNG (cryptographically
    secure pseudo random number generator).  For modes that require a
    nonce, then the initialization vector (IV) does not need a CSPRNG.  In all cases, the IV
    should never be used twice for a fixed key.

-   Always use authenticated encryption instead of just encryption.

-   Keys should be generated cryptographically randomly and stored in
    memory as byte arrays. If a password is used, then it must be converted
    to a key via an appropriate password base key derivation function.

---

-   Ensure that cryptographic randomness is used where appropriate, and
    that it has not been seeded in a predictable way or with low entropy.
    Most modern APIs do not require the developer to seed the CSPRNG to
    get security.

-   Avoid deprecated cryptographic functions and padding schemes, such as
    MD5, SHA1, PKCS number 1 v1.5 .

-   Verify independently the effectiveness of configuration and
    settings.

---

## Information Classification

| Class            | Description                                                                                                              | Examples                                                                                              |
|:-----------------|:-------------------------------------------------------------------------------------------------------------------------|:------------------------------------------------------------------------------------------------------|
| **Public**       | <small><small>Information without any confidentiality requirements.</small></small>                                      | <small><small>User documentation, news, press releases, lunch menus</small></small>                   |
| **Internal**     | <small><small>Common information inside an organization.</small></small>                                                 | <small><small>Memos, system documentation or meeting minutes</small></small>                          |
| **Confidential** | <small><small>Information or compartmental data with restricted access. Disclosure might induce damage.</small></small>  | <small><small>Customer, HR, financial or PII data; source code, credentials, logfiles</small></small> |
| **Secret**       | <small><small>Highest confidentiality and integrity requirements. Damaging to organization if disclosed.</small></small> | <small><small>Business secrets, secret formulae, planned mergers/acquisitions</small></small>         |

---

# Exercise 6.1

For each classification level decide if the listed practices should be
allowed (:heavy_check_mark:) or strictly forbidden (:x:). Use footnotes
to describe preconditions (if necessary).

| Practice                 | Public | Internal | Confidential | Secret |
|:-------------------------|:-------|:---------|:-------------|:-------|
| Publish on Internet      |        |          |              |        |
| Publish on Intranet      |        |          |              |        |
| Print on :printer:       |        |          |              |        |
| Share with third parties |        |          |              |        |
| Copy to USB key          |        |          |              |        |

---

# Exercise 6.2

For each classification level define restrictions (:red_circle:) and/or
recommendations (:o:) for the listed lifecycle phases.

| Phase                           | Public | Internal | Confidential | Secret |
|:--------------------------------|:-------|:---------|:-------------|:-------|
| Permanent storage<br>           |        |          |              |        |
| Transfer (internal network)<br> |        |          |              |        |
| Transfer (public network)<br>   |        |          |              |        |
| Disposal<br>                    |        |          |              |        |

---

## [HTTP Strict Transport Security (HSTS)](https://cheatsheetseries.owasp.org/cheatsheets/HTTP_Strict_Transport_Security_Cheat_Sheet.html)

> HTTP Strict Transport Security (HSTS) is an opt-in security
> enhancement that is specified by a web application through the use of
> a special response header. Once a supported browser receives this
> header that browser will prevent any communications from being sent
> over HTTP to the specified domain and will instead send all
> communications over HTTPS. It also prevents HTTPS click through
> prompts on browsers.

##### Example

```http
Strict-Transport-Security: max-age=16070400; includeSubDomains
```

---

## [Secure Cryptographic Storage Design](https://cheatsheetseries.owasp.org/cheatsheets/Cryptographic_Storage_Cheat_Sheet.html)

* Only store sensitive data that you need
* Use strong approved Authenticated Encryption
* Store a one-way and salted value of passwords
* Ensure that the cryptographic protection remains secure even if access
  controls fail
* Ensure that any secret key is protected from unauthorized access
* Follow applicable regulations on use of cryptography

---

## [Perfect Forward Secrecy (PFS)](https://www.wired.com/2016/11/what-is-perfect-forward-secrecy/)

> Perfect forward secrecy means that a piece of an encryption system
> automatically and frequently changes the keys it uses to encrypt and
> decrypt information, such that if the latest key is compromised, it
> exposes only a small portion of the user’s sensitive data. Encryption
> tools with perfect forward secrecy switch their keys as frequently as
> every message in text-based conversation, every phone call in the case
> of encrypted calling apps, or every time a user loads or reloads an
> encrypted web page in his or her browser.

:information_source: Examples of crypto protocols (used for instant
messaging conversations) providing PFS are
[OTR (Off-the-record) Messaging](https://otr.cypherpunks.ca/index.php)
and
[Double Ratchet](https://signal.org/docs/specifications/doubleratchet/)
(used within [Signal](https://signal.org/)).

---

### [Best Practices](https://wiki.owasp.org/index.php/Cryptographic_Storage_Cheat_Sheet#Architectural_Decision)

| Scenario                                                                                                         | Practice                     | :key: Length     |
|:-----------------------------------------------------------------------------------------------------------------|:-----------------------------|:-----------------|
| Key exchange                                                                                                     | Diffie-Hellman               | 2048+ bits       |
| Message Integrity                                                                                                | HMAC-SHA2                    | -                |
| Message Hash                                                                                                     | SHA2                         | 256 bits         |
| [Asymetric encryption](https://cheatsheetseries.owasp.org/cheatsheets/Cryptographic_Storage_Cheat_Sheet.html)    | **ECC** (Curve25519), RSA    | 2048 bits (RSA)  |
| [Symmetric-key algorithm](https://cheatsheetseries.owasp.org/cheatsheets/Cryptographic_Storage_Cheat_Sheet.html) | AES                          | 128-**256** bits |
| [Password Hashing](https://cheatsheetseries.owasp.org/cheatsheets/Password_Storage_Cheat_Sheet.html)             | **Argon2id**, scrypt, PBKDF2 | -                |

---

# Exercise 6.3 (:house:)

1. Access a confidential document (:star:)
2. Retrieve as many clear text user passwords as you can
   (:star::star::star::star:)
3. Visit the Token Sale page before it officially goes live
   (:star::star::star::star::star:)

##### Bonus exercises on cryptography (_optional_)

4. Retrieve both the :rabbit2: easter eggs (:star::star::star::star:)
5. Solve the steganography challenge (:star::star::star::star:)
6. Solve the non-existent challenge \#999
   (:star::star::star::star::star::star:)

