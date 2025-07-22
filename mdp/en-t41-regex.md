![](http://fondinfo.github.io/images/comp/attack.svg)
# Regex
## Introduction to Computer Science <br> Michele Tomaiolo @ Ingegneria UniPR

---

![](http://fondinfo.github.io/images/comp/tangible.jpg)
# 💡️ Formal Languages

- Present in all applications
    - Programming languages
    - Markup languages (e.g., HTML, Latex)
    - Human-machine interaction (e.g., Google, Zork)
- Fundamental in system software
    - Compilers
    - Interpreters…
- Paradigmatic in theory
    - Many problems reducible to *membership*
    - Does a string belong to a language?

>

<https://www.google.com/search?q=zork+site:archive.org>

---

# 💡️ Alphabets and Strings

- Alphabet `$\Sigma$`: set of symbols
- String `$s$`: sequence of symbols from `$\Sigma$`
    - `$s \in \Sigma^\star$`, set of all strings
    - `$\varepsilon$`: empty string
    - `$|s|$`: length of string `$s$`
- Language `$L \subseteq \Sigma^\star$`
    - Subset of all possible strings
    - Grammar: formal rules to define "well-formed strings" of `$L$`

---

![](http://fondinfo.github.io/images/comp/roman-nums-clock.jpg) ![large](http://fondinfo.github.io/images/comp/roman-nums-table.png)
# 🧪 Roman Numerals

- Alphabet

| Symbol: | I | V | X | L | C | D | M |
|---|---|---|---|---|---|---|---|
| Value: | 1 | 5 | 10 | 50 | 100 | 500 | 1000 |

- Rules
    - Maximum 3 repetitions of a symbol...
    - But `V, L, D` are not repeated
    - Smaller numbers follow larger ones...
    - Except `IV, IX, XL, XC, CD, CM`

>

<https://en.wikipedia.org/wiki/Roman_numerals#Standard_form>

---

# 💡️ Definition of Languages

- **Algebraic** approach: *regular expressions*
    - Language built with operations on more elementary languages
- **Generative** approach: *grammars*
    - Rules for generating strings belonging to the language
- **Recognition** approach: *automata*
    - Algorithms to decide whether a string belongs to the language or not

---


# Regular Expressions

---

# 💡️ Operations on Languages

- `$L_1$` and `$L_2$` languages on `$\Sigma^\star$` (two sets of strings)
- *Union*
    - `$L_1 \cup L_2 := \{x \in \Sigma^\star : x \in L_1 \lor x \in L_2\}$`
- *Intersection*
    - `$L_1 \cap L_2 := \{x \in \Sigma^\star : x \in L_1 \land x \in L_2\}$`
- *Complementation* : ``
    - `$L^c := \{x \in \Sigma^\star : x \notin L\}$`

---

# 💡️ String Concatenation

- Concatenation operation: `$\cdot$`
    - Associative property: `$(x \cdot y) \cdot z = x \cdot (y \cdot z)$`
    - Not commutative: `$x \cdot y \neq y \cdot x$`
    - `$\Sigma^\star$` closed with respect to `$\cdot$`: `$\Sigma^\star \times \Sigma^\star \to \Sigma^\star$`
- Power
    - `$x^n := x \cdot x \cdot x \cdot x \cdots$` (`$n$` times)
- Identity element `$ε$`
    - Empty string, `$\forall x \in \Sigma^\star, ε \cdot x = x \cdot ε = x$`
- `$<\Sigma^\star, \cdot, ε>$`: monoid

---

# 💡️ Language Concatenation


- *Concatenation or product*
    - `$L_1 \cdot L_2 := \{x \in \Sigma^\star : x = x_1 \cdot x_2, x_1 \in L_1, x_2 \in L_2\}$`
    - E.g., `$L_1 := \{ab, bb\}; L_2 := \{aa, ab\};$` <br> `$L_1 \cdot L_2 = \{abaa, abab, bbaa, bbab\}$`
- *Power*
    - `$L^n := L \cdot L^{n-1}, n\geq1; L^0 := \{ε\}$` by convention
    - Concatenation of `$n$` arbitrary strings from `$L$`
    - E.g., `$L := \{ab, bb\}; L^2 = \{abab, abbb, bbab, bbbb\}$`
- *Kleene Star*
    - `$L^\star := \bigcup_{n=0}^∞ L^n, $`
    - Arbitrary concatenation of strings from `$L$`
    - `$L^\star$`: closure of `$L$` with respect to `$\cdot$`

---

# 💡️ Regular Expressions

- *Regular expression*: string `$r$` over alphabet `$\Sigma ∪ \{+,\star,(,),\cdot,\varnothing\}$` such that:
    - `$r = \varnothing$`: empty language; or
    - `$r \in \Sigma$`: language with a single symbol; or
    - `$r = s + t$`: union of languages `$L(s)$`, `$L(t)$`; or
    - `$r = s \cdot t$`: concatenation of languages `$L(s)$`, `$L(t)$`; or
    - `$r = s^\star$`: closure of language `$L(s)$`
    - (with `$s$` and `$t$` being regular expressions; `$\cdot$` symbol often implicit)
- *Regular languages*: representable with regular expressions ("*regex*")

---

# 💡️ Expressions and Languages

- `$\Sigma := \{a, b\}$`
- <em>`$(a + b \cdot b)$`</em>
    - `$\{a, bb\}$`
- <em>`$(a + b \cdot b)^\star$`</em>
    - `$\{\varepsilon, a, bb, aa, abb, bba, bbbb, aaa, \dots\}$`
- <em>`$(a + b)^\star$`</em>
    - `$\{\varepsilon, a, b, aa, ab, ba, bb, aaa, \dots\}$`
- <em>`$a \cdot (a + b)^\star \cdot b$`</em>
    - `$\{ab, aab, abb, aaab, aabb, abab, \dots\}$`

---

# 💡️ Save the day with regex

![large](http://fondinfo.github.io/images/comp/regex-xkcd.png)

---

# ⭐ PCRE, Perl Compatible RegEx

- Character concatenation: `goal`
- Union between expressions (option): `one|two|three`
- One character from a set (or not): `[a-z]`, `[^a-z0-9]`
- Any character: `defin.tely`
- Repetitions (0+, 1+, 0-1): `goo*al`, `go+al`, `goo?al`
- Subexpression: `(left right )*halt`

![](http://fondinfo.github.io/images/comp/perl-problems.png)

---

# ⭐ Regex, Character Classes

- `[...]` to include any of the characters in parentheses
    - Single characters or adjacent character ranges
    - `[A-Z]` = any uppercase letter
    - `[a-zABC]` = any lowercase letter or `A`, `B`, or `C`
- `[^...]` to exclude any of the characters in parentheses
    - `[^0-9]` = any non-numeric character
- Special sequences to identify character classes
    - `\d` = numeric, i.e., `[0-9]`
    - `\s` = `[ \t\r\n\f]`
    - `\w` = `[0-9a-zA-Z_]`
    - `\D` = non-numeric, i.e., `[^0-9]` (also `\W` etc.)

---

# ⭐ Regex, Special Characters

- `.` for any single character
    - `A.B` recognizes strings like `AoB`, `AwB`, `AOB`, etc.
- `\` escape, to signal special sequences or treat special characters as normal
    - `\?` searches for `?`
- `^` matches the beginning of the text
- `$` matches the end of the text
- `|` for alternative between two expressions (union)
    - `A|B` = character `A` or character `B`
- `(...)` for grouping sub-expressions
    - `ga(zz|tt)a` finds both `gazza` and `gatta`

---

# ⭐ Regex, Repetitions

- `{...}` to specify the number of repetitions
    - `\d{3,5}` sequences of at least three digits, at most five
- `*` zero or more occurrences of an expression
    - `(ab)*` recognizes `ab`, `abab`, the empty string, but does not recognize `abba`
- `+` one or more occurrences
    - `(ab)+` does not recognize the empty string
- `?` zero or at most one occurrence (optional part)
    - `https?://\S*` recognizes both http and https URLs

>

⭐ <http://www.zytrax.com/tech/web/regex.htm>

---

![large](http://fondinfo.github.io/images/comp/codice-fiscale.png)
# 🧪 Regex in HTML

``` html
<form>
    Date (dd/mm/yyyy):
    <input name="dd" title="dd/mm/yyyy"
        pattern="\d{2}/\d{2}/\d{4}" />
    <input type="submit" />
</form>
```

- *Date*: `\d{2}/\d{2}/\d{4}`
- *File*: `.+\.zip`
- *E-mail*: `[\w\-\.]+@[\w\-\.]+\.[a-z]+`
- *Domain*: `[\w\-]+\.(it|com|org|net|eu)`
- *Tax code*: `[A-Z]{6}\d\d[A-Z]\d\d[A-Z]\d{3}[A-Z]`

---

# 🧪 Regex find in Python

``` py
>>> import re
>>> text = "He was carefully disguised but captured quickly by police."
>>> re.findall(r"\w+ly", text)
['carefully', 'quickly']
>>> text = "Python is a <multi-paradigm> <programming language>."
>>> re.findall(r"<([^>]*)>", text)
['multi-paradigm', 'programming language']
>>> re.split(r"\W+", text)
['Python', 'is', 'a', 'multi', 'paradigm', 'programming', 'language', '']
```

>

<http://docs.python.org/3/library/re.html>

---

# 🧪 Regex sub in Python

``` py
>>> re.sub(r"([0-9])([a-z]+)", r"\1<sup>\2</sup>", "He won the 3rd prize")
'He won the 3<sup>rd</sup> prize'
>>> re.sub(r"([aeiou])\1+", r"\1", "troooppo miiiticoo!")
'troppo mitico!'
>>> re.sub(r"(o?)([aeiou])\2+", r"\1\2", "gooood daaay!")
'good day!'
```

>

<http://docs.python.org/3/library/re.html>
