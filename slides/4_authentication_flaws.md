<!-- theme: default -->
<!-- paginate: true -->
<!-- footer: Copyright (c) by **Bjoern Kimminich** | Licensed under [CC-BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) -->

# Authentication Flaws

---

# :x: [Typical Flaws in Authentication](https://owasp.org/www-project-top-ten/OWASP_Top_Ten_2017/Top_10-2017_A2-Broken_Authentication)

* Permits brute force or other automated attacks
* Permits default, weak, or well-known passwords
* Uses weak or ineffective credential recovery and forgot-password
  processes (e.g. "knowledge-based answers")
* Uses plain text, encrypted, or weakly hashed passwords
* Has missing or ineffective multi-factor authentication
* Exposes Session IDs in the URL
* Does not rotate Session IDs after successful login
* Does not properly invalidate Session IDs

---

# Risk Rating

## Broken Authentication

| Exploitability    | Prevalence                    | Detecability                   | Impact              | Risk                                                                                                |
|:------------------|:------------------------------|:-------------------------------|:--------------------|:----------------------------------------------------------------------------------------------------|
| :red_circle: Easy | :large_orange_diamond: Common | :large_orange_diamond: Average | :red_circle: Severe | [A2](https://owasp.org/www-project-top-ten/OWASP_Top_Ten_2017/Top_10-2017_A2-Broken_Authentication) |

---

# Exercise

1. Watch
   [How To Keep Your Passwords Safe](https://www.facebook.com/CollegeHumor/videos/10155483807197807/)
   :tv:
2. Log in with MC SafeSearch's user account (:star::star:)

---

#### [Password Strength Controls](https://pages.nist.gov/800-63-3/sp800-63-3.html)

* **Enforce minimum password length** of at least 10 characters
* Maximum length should allow 64 characters or more
* **No periodic password resets** as users rely on predictable patterns
* Avoid password complexity rules as _all of them_ are predictable
* Ban bad passwords or ones which have appeared in data breaches
  * e.g. [Troy Hunt's 10GB+ list](https://haveibeenpwned.com/Passwords)
    or
    [Daniel Miesler's various lists](https://github.com/danielmiessler/SecLists/tree/master/Passwords)
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

# Exercise

1. Log in as admin exploiting its insufficient _Password Strength_
   (:star::star:)
2. _Reset Jim's Password_ by answering his secret question
   (:star::star::star:)
3. _Login Bjoern_ using his Gmail account (:star::star::star::star:)

