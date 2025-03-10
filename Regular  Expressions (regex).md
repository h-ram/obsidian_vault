
Regular expressions (regex) are powerful text patterns used for searching, matching, and manipulating strings. They are widely used in programming, text processing, and command-line tools.

---
# **Types of Regular Expressions**

| **Regex Type**                                    | **Description**                                             | **Used In**                        |
| ------------------------------------------------- | ----------------------------------------------------------- | ---------------------------------- |
| **1. Basic Regular Expressions (BRE)**            | The oldest regex type; some characters need escaping (`\`). | `grep`, `sed`, `awk`               |
| **2. Extended Regular Expressions (ERE)**         | More expressive, supports `+`, `?`, `{}` without escaping.  | `grep -E`, `sed -r`, `awk`         |
| **3. Perl-Compatible Regular Expressions (PCRE)** | Advanced regex with lookaheads, backreferences, etc.        | `grep -P`, `Perl`, `Python`, `PHP` |

---
# **Basic Regex (BRE)**

| **Regex**     | **Description**                   | **Example**           | **Matches**                              |
| ------------- | --------------------------------- | --------------------- | ---------------------------------------- |
| `abc`         | Literal characters                | `cat`                 | `"cat"` but not `"catch"`                |
| `.`           | Any single character              | `c.t`                 | `"cat"`, `"cut"`, `"cot"`                |
| `^`           | Start of line                     | `^Hello`              | `"Hello world"` but not `"world Hello"`  |
| `$`           | End of line                       | `done$`               | `"job done"` but not `"done job"`        |
| `[abc]`       | Any character in brackets         | `gr[ae]y`             | `"gray"`, `"grey"`                       |
| `[^abc]`      | Any character **not** in brackets | `[^0-9]`              | `"a"`, `"B"` but not `"5"`               |
| `[a-z]`       | Any lowercase character (ASCII)   | `[a-x]`               | `"g"` but not `"G"`                      |
| `\(` `\)`     | Grouping                          | `\(ha\)\+`            | `"ha"`, `"hahaha"`                       |
| `\|`          | OR (alternation)                  | `apple\|banana`       | `"apple"`, `"banana"`                    |
| `*`           | Zero or more occurrences          | `bo*n`                | `"bn"`, `"bon"`, `"boon"`                |
| `\+`          | One or more occurrences           | `bo\+n`               | `"bon"`, `"boon"` but not `"bn"`         |
| `\?`          | Zero or one occurrence            | `colou\?r`            | `"color"`, `"colour"`                    |
| `\{n\}`       | Exactly `n` occurrences           | `o\{2\}`              | `"good"` but not `"god"`                 |
| `\{n,\}`      | At least `n` occurrences          | `o\{2,\}`             | `"good"`, `"goood"`                      |
| `\{n,m\}`     | Between `n` and `m` occurrences   | `o\{2,4\}`            | `"good"`, `"goood"`, but not `"goooood"` |
| `\n`          | Newline character                 | `grep 'line1\nline2'` | Matches `"line1\nline2"` in a file       |
| `\t`          | Tab character                     | `grep 'word\tword'`   | Matches `"word<TAB>word"`                |
| `[[:digit:]]` | Any digit (POSIX class)           | `[[:digit:]]`         | `"5"` but not `"a"`                      |
| `[[:alpha:]]` | Any letter (A-Z, a-z)             | `[[:alpha:]]`         | `"A"`, `"b"` but not `"5"`               |
| `[[:alnum:]]` | Any letter or digit               | `[[:alnum:]]`         | `"A"`, `"5"` but not `"@"`               |
| `[[:space:]]` | Any whitespace character          | `[[:space:]]`         | `" "`, `"\t"`, `"\n"`                    |

---

# **Extended Regex (ERE)**
ERE is a *superset* of BRE with some changes and overwrites and additional features.

| **Regex** | **Description**                 | **Example**    | **Matches**                              |
| --------- | ------------------------------- | -------------- | ---------------------------------------- |
| `()`      | Grouping                        | `(ha)+`        | `"ha"`, `"hahaha"`                       |
| \|        | OR (alternation)                | apple\|banana` | `apple` OR `banana`                      |
| `+`       | One or more occurrences         | `bo+n`         | `"bon"`, `"boon"` but not `"bn"`         |
| `?`       | Zero or one occurrence          | `colou?r`      | `"color"`, `"colour"`                    |
| `{n}`     | Exactly `n` occurrences         | `o{2}`         | `"good"` but not `"god"`                 |
| `{n,}`    | At least `n` occurrences        | `o{2,}`        | `"good"`, `"goood"`                      |
| `{n,m}`   | Between `n` and `m` occurrences | `o{2,4}`       | `"good"`, `"goood"`, but not `"goooood"` |
| `\b`      | Word boundary                   | `\bword\b`     | `" word "` but not `"wording"`           |
| `\s`      | Any whitespace                  | `a\sb`         | `"a b"`                                  |
| `\S`      | Any non-whitespace              | `a\Sb`         | `"axb"` but not `"a b"`                  |
| `\d`      | Any digit                       | `\d+`          | `"123"`, `"9"`                           |
| `\D`      | Any non-digit                   | `\D+`          | `"abc"`, `"xyz"`                         |
| `\w`      | Any word character              | `\w+`          | `"hello"`, `"word_123"`                  |
| `\W`      | Any non-word character          | `\W+`          | `"@"`, `"!"`, `"$%^"`                    |
**Key Differences Between ERE and BRE**
1. **Grouping:**
    - **BRE:** Must escape `()` → `\( \)`
    - **ERE:** Uses `()` directly
2. **Alternation (`|` OR operator):**
    - **BRE:** Must escape `\|`
    - **ERE:** Uses `|` directly
3. **Repetition (`+`, `?`, `{}`):**
    - **BRE:** Must escape `\+`, `\?`, `\{ \}`
    - **ERE:** Uses `+`, `?`, `{}` directly
4. **Character Classes (`\d`, `\s`, `\w`)**
    - **BRE:** Not supported
    - **ERE:** Supported
5. **Word Boundaries (`\b`)**
    - **BRE:** Not supported
    - **ERE:** Supported

# **Perl-Compatible Regex (PCRE)**
PCRE is a *superset* of ERE with some additional features.

| **Regex**  | **Description**                             | **Example**               | **Matches**                            |
| ---------- | ------------------------------------------- | ------------------------- | -------------------------------------- |
| `\b`       | Word boundary                               | `\bword\b`                | `" word "` but not `"wording"`         |
| `\B`       | Not a word boundary                         | `\Bword\B`                | `"sword"` but not `"word"`             |
| `\n`       | Newline character                           | `hello\nworld`            | Matches `"hello"` followed by newline  |
| `\r`       | Carriage return                             | `\r\n`                    | Matches Windows-style newlines         |
| `\t`       | Tab character                               | `a\tb`                    | `"a<TAB>b"`                            |
| `\xHH`     | Hexadecimal byte                            | `\x41`                    | `"A"` (ASCII 65)                       |
| `\uHHHH`   | Unicode character                           | `\u03A9`                  | `"Ω"` (Greek Omega)                    |
| `(?i)`     | Case-insensitive mode                       | `(?i)hello`               | `"hello"`, `"HELLO"`, `"Hello"`        |
| `(?m)`     | Multiline mode (`^` and `$` apply per line) | `(?m)^hello`              | Matches `"hello"` at start of any line |
| `(?s)`     | Dotall mode (`.` matches newlines)          | `(?s)c.t`                 | Matches `"cat"`, `"c\nt"`              |
| `(?:...)`  | Non-capturing group                         | `(?:ha)+`                 | `"haha"` but doesn't capture groups    |
| `(?=...)`  | Positive lookahead                          | `foo(?=bar)`              | `"foobar"` but not `"foobaz"`          |
| `(?!...)`  | Negative lookahead                          | `foo(?!bar)`              | `"foobaz"` but not `"foobar"`          |
| `(?<=...)` | Positive lookbehind                         | `(?<=foo)bar`             | `"foobar"` but not `"bazbar"`          |
| `(?<!...)` | Negative lookbehind                         | `(?<!foo)bar`             | `"bazbar"` but not `"foobar"`          |
| `(?#...)`  | Comment (ignored in regex)                  | `a(?#this is a comment)b` | `"ab"`                                 |
| `\K`       | Resets match start                          | `foo\Kbar`                | Only `"bar"` is returned as match      |
**Key Features of PCRE:**
1. **Supports everything in ERE plus:**
    - `\b` and `\B` for word boundaries.
    - `\s`, `\d`, `\w` shorthand character classes.
    - Lookaheads (`(?=...)`), lookbehinds (`(?<=...)`), and negations.
    - Unicode (`\uHHHH`), hexadecimal (`\xHH`).
    - Case-insensitive (`(?i)`), dotall (`(?s)`), and multiline (`(?m)`) modes.
    - Comments (`(?#...)`).
    - Non-capturing groups (`(?:...)`).
    - Match resets with `\K`.
2. **Powerful Assertions:**
    - Lookaheads and lookbehinds enable **context-sensitive matching**.
    - Word boundaries (`\b`) prevent unintended partial matches.
3. **Better Performance:**
    - PCRE is used in __Perl, PHP (preg__ functions), Python (`regex` module, not `re`), and advanced text editors_* like Sublime Text and VS Code.

---
# **How to Use Regex in Different Tools**

## **3.1. Regex in `grep`**

```bash
grep -E "error|failed|warning" log.txt
# Matches `"error"`, `"failed"`, or `"warning"`.

grep -E "[0-9]{2,4}" file.txt
# Matches numbers with 2 to 4 digits.
```
## **3.2. Regex in `sed`**

```bash
sed -E 's/[0-9]+/NUMBER/g' file.txt
# Replaces all numbers with `"NUMBER"`.

sed -n '/^ERROR/p' log.txt
# Prints lines starting with `"ERROR"`.
```
## **3.3. Regex in `awk`**
```bash
awk '/^[A-Za-z]+@[A-Za-z]+\.[a-z]+$/' emails.txt
# Finds valid email addresses.

awk '{if ($1 ~ /^[0-9]+$/) print $1}' file.txt
# Prints lines where the first column contains only numbers.
```
---
## **3.4. Regex in Python**
```python
import re

text = "User email: user@example.com"
match = re.search(r"\b[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Z|a-z]{2,}\b", text)
if match:
    print(match.group())
```
- Finds an email address in text.
---