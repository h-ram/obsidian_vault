**Punycode** is a way of encoding **Unicode characters** (which includes Chinese, Arabic, etc.) into **ASCII characters** so that they can be used in domain names, as the Domain Name System (DNS) only supports ASCII characters.
- Punycode adds the prefix **"xn--"** to the encoded domain.
- Unicode characters are then transformed into an ASCII-compatible encoding that uses a specific pattern.
```
tést.com  --> xn--tst-7ka.com
例子.测试  --> xn--fsq.xn--zfr164b
привет.рф --> xn--e1afmkfd.xn--p1ai
```
---
# How Punycode Looks in Practice
- You will rarely see Punycode in regular web addresses, as modern browsers automatically decode Punycode back into the readable Unicode form. For instance, if you enter **"xn--tst-7ka.com"** in the address bar, your browser will display it as **"tést.com"**.