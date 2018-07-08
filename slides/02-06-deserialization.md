<!-- $theme: gaia -->

<!-- $size: 16:9 -->

<!-- page_number: true -->

<!-- footer: Copyright (c) by Bjoern Kimminich | Licensed under CC-BY-SA 4.0 -->

# Deserialization

---

<!-- *footer: Български: Схема на сериализация и десериализация, 2016 WnbKrumov, used under CC-BY-SA 4.0 -->

# Serialization

> Object serialization transforms an object's data to a bytestream that represents the state of the data. The serialized form of the data contains enough information to recreate the object with its data in a similar state to what it was when saved. \[[^1]\]

![Български: Схема на сериализация и десериализация, 2016 WnbKrumov, used under CC-BY-SA 4.0](images/02-06-deserialization/serialization.jpg)

[^1]: http://www.oracle.com/technetwork/java/serial-137074.html

---

# Risk Rating

## Insecure Deserialization

| Exploitability                   | Prevalence                    | Detecability                   | Impact              | Risk                                                                          |
|:---------------------------------|:------------------------------|:-------------------------------|:--------------------|:------------------------------------------------------------------------------|
| :small_orange_diamond: Difficult | :large_orange_diamond: Common | :large_orange_diamond: Average | :red_circle: Severe | [A8](https://www.owasp.org/index.php/Top_10-2017_A8-Insecure_Deserialization) |
| ( **1**                          | + **2**                       | + **2** ) / 3                  | * **3**             | = **5.0**                                                                     |

