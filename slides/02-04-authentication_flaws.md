<!-- $theme: gaia -->

<!-- $size: 16:9 -->

<!-- page_number: true -->

<!-- footer: Copyright (c) by Bjoern Kimminich | Licensed under CC-BY-SA 4.0 -->

# Authentication Flaws

---

<!-- *footer: -->

# :x: [Typical Flaws in Authentication](https://www.owasp.org/index.php/Top_10-2017_A2-Broken_Authentication)

* Permits brute force or other automated attacks
* Permits default, weak, or well-known passwords
* Uses weak or ineffective credential recovery and forgot-password processes (e.g. "knowledge-based answers")
* Uses plain text, encrypted, or weakly hashed passwords
* Has missing or ineffective multi-factor authentication
* Exposes Session IDs in the URL
* Does not rotate Session IDs after successful login
* Does not properly invalidate Session IDs

---

# Risk Rating

## Broken Authentication

| Exploitability    | Prevalence                    | Detecability                   | Impact              | Risk                                                                       |
|:------------------|:------------------------------|:-------------------------------|:--------------------|:---------------------------------------------------------------------------|
| :red_circle: Easy | :large_orange_diamond: Common | :large_orange_diamond: Average | :red_circle: Severe | [A2](https://www.owasp.org/index.php/Top_10-2017_A2-Broken_Authentication) |
| ( **3**           | + **2**                       | + **2** ) / 3                  | * **3**             | = **7.0**                                                                  |

---

# Exercise

1. Watch [How To Keep Your Passwords Safe](https://www.facebook.com/CollegeHumor/videos/10155483807197807/) :tv:
2. Log in with MC SafeSearch's user account (:star::star:)

_:warning: Do **not** use SQL Injection for authentication bypass!_

---

<!-- *footer: -->

# Exercise

1. Pick one Security Question and explain how :muscle: it is against attacks.
2. What would you recommend to pick as an answer? Assume that the risk of compromise is full takeover of your user account.

![Security Questions](images/02-04-authentication_flaws/secret_questions.png)

---

<!-- *footer: -->

#### [Password Strength Controls](https://pages.nist.gov/800-63-3/sp800-63-3.html)

* **Enforce minimum password length** of at least 10 characters
* Maximum length should allow 64 characters or more
* **No periodic password resets** as users rely on predictable patterns
* Avoid password complexity rules as _all of them_ are predictable
* Ban bad passwords or ones which have appeared in data breaches
  * e.g. [Troy Hunt's 10GB+ list](https://haveibeenpwned.com/Passwords) or [Daniel Miesler's various lists](https://github.com/danielmiessler/SecLists/tree/master/Passwords)  
* Allow convenience features on password fields
  * Offer _Show Password while typing_ option
  * Allow pasting from clipboard into password fields

---

#### Other Authentication Controls

* **Transmit passwords only over TLS**
  * The "login landing page" must be served over TLS as well
* **Prevent Brute-Force Attacks** (e.g. throttling or periodic lockout)
* Require re-authentication for sensitive features
* **Offer optional 2FA / MFA**
  * Consider strong transaction authentication

#### Enterprise Controls

* Use centralized corporate authentication system (if in place)

---

# Two-Factor Authentication

> Two-factor authentication adds a second level of authentication to an account log-in. When you have to enter only your username and one password, that's considered a single-factor authentication. 2FA requires the user to have two out of three types of credentials before being able to access an account. The three types are:
>
> * **Something you know**, such as a personal identification number (PIN), password or a pattern
> * **Something you have**, such as an ATM card, phone, or fob
> * **Something you are**, such as a biometric like a fingerprint or voice print \[[^1]\]

[^1]: https://www.cnet.com/news/two-factor-authentication-what-you-need-to-know-faq/

---

# [2FA Method Comparison](https://www.expressvpn.com/blog/best-two-factor-authentication)

| Method            | Security        | Privacy                              | Access             |
|:------------------|:----------------|:-------------------------------------|:-------------------|
| SMS               | :key:           | :sunglasses:                         | :door::door::door: |
| Authenticator App | :key::key:      | :sunglasses::sunglasses::sunglasses: | :door:             |
| Hardware Key      | :key::key::key: | :sunglasses::sunglasses::sunglasses: | :door::door:       |

> <small>Hardware keys win from a security perspective, they are private and unaffected by a dying or out of range phone. However, only a few services (Google, Dropbox, Facebook, Github and a few others) support the standard so far. Unless you trust your phone provider (and few providers are trustworthy), **an authenticator app is the best option**.</small>

---

<!-- *footer: -->

# Password Managers

> Password managers are programs, browser plugins or web services that automate management of large number of different credentials, including memorizing and filling-in, generating random passwords on different sites etc. \[[^2]\]

| [![KeePass Logo](images/02-04-authentication_flaws/keepass_322x132.png)](https://keepass.info/) | [![LastPass Logo](images/02-04-authentication_flaws/LastPass-Logo-Color.png)](https://www.lastpass.com) | [![1Password Logo](images/02-04-authentication_flaws/1password-logo-awesome%402x.png)](https://1password.com/) |
|:------------------------------------------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------|
| Open Source (GPLv2)                                                                             | Proprietary / Freemium                                                                                  | Proprietary                                                                                                    |
| Local installation, optional file or cloud sync                                                 | Cloud-based                                                                                             | Local installation with Cloud sync                                                                             |

[^2]: https://www.owasp.org/index.php/Authentication_Cheat_Sheet#Password_Managers

---

# Exercise

1. Log in with the admin's user account (:star::star:)
2. Reset Jim's password by answering his secret question (:star::star::star:)
3. Log in with Bjoern's user account (:star::star::star::star:)
