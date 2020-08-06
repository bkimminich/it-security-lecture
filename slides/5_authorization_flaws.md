<!-- theme: default -->
<!-- paginate: true -->
<!-- footer: Copyright (c) by **Bjoern Kimminich** | Licensed under [CC-BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) -->

# Authorization Flaws

---

# [Broken Access Control](https://owasp.org/www-project-top-ten/OWASP_Top_Ten_2017/Top_10-2017_A5-Broken_Access_Control)

Access control is supposed to prevent that users can act outside of
their intended permissions.

##### Possible Impact of Broken Access Control

* Access unauthorized functionality and/or data, such as access other
  users' accounts
* View sensitive files
* Modify other users' data
* Change access rights

---

##### Common Attacks

* Modifying URL, internal application state, or HTML page
* Changing the primary key to another users record
* Elevation of privilege
  * Acting as a user without being logged in
  * Acting as an admin when logged in as a user

_:information_source: Obtaining a higher level of access is also
referred to as **Vertical** Privilege Escalation while same-level access
to another user's data is called **Horizontal** Privilege Escalation._

---

* Metadata manipulation
  * Replaying or tampering with access control tokens
  * Cookie or hidden field manipulation
* Force browsing to authenticated pages as an anonymous user or to
  privileged pages as a standard user
* Accessing API with missing access controls for `POST`, `PUT` and
  `DELETE`

---

# Risk Rating

## Broken Access Control

| Exploitability                 | Prevalence                    | Detecability                   | Impact              | Risk                                                                                                |
|:-------------------------------|:------------------------------|:-------------------------------|:--------------------|:----------------------------------------------------------------------------------------------------|
| :large_orange_diamond: Average | :large_orange_diamond: Common | :large_orange_diamond: Average | :red_circle: Severe | [A5](https://owasp.org/www-project-top-ten/OWASP_Top_Ten_2017/Top_10-2017_A5-Broken_Access_Control) |

---

# Exercise

Assuming no access control is in place, which privilege escalations are
possible by tampering with the following URLs?

1. `http://logistics-worldwi.de/showShipment?id=40643108`
2. `http://my-universi.ty/api/students/6503/exams/view`
3. `http://document-warehou.se/landingpage?content=index.html`

---

# [Prevention](https://owasp.org/www-project-top-ten/OWASP_Top_Ten_2017/Top_10-2017_A5-Broken_Access_Control)

* **Access control** is only effective if **enforced in trusted
  server-side code**
* With the exception of public resources, **deny by default**
* **Implement** access control mechanisms **once and re-use** them
  throughout the application
* **Enforce record ownership**
* **Disable web server directory listing** and ensure file metadata and
  backup files are not present within web roots

---

* **Log access control failures**, alert admins when appropriate
* Rate limit API and controller access to minimize the harm from
  automated attack tooling
* Access tokens should be invalidated on the server after logout
* Developers and QA staff should include functional access control unit
  and integration tests

---

# Exercise

1. Access the _Admin Section_ of the store (:star::star:)
2. _View_ some other user's shopping _Basket_ (:star::star:)
3. Get rid of all submitted _Five-Star Feedback_ (:star::star:)
4. Post some _Forged Feedback_ for another user (:star::star::star:)
5. It's _Payback Time_: Place an order with a negative total
   (:star::star::star:)
6. Access the _Forgotten Developer_ and/or _Sales Backup_
   (:star::star::star::star:)

