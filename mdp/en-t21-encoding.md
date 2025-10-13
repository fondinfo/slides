![](http://fondinfo.github.io/images/repr/binary-hacker.jpg)
# Information Encoding
## Introduction to Computer Science <br> Michele Tomaiuolo @ Ingegneria UniPR

---

![](http://fondinfo.github.io/images/repr/analog-clock.png) ![](http://fondinfo.github.io/images/repr/digital-clock.png)
# 💡️ Analog and Digital

- A quantity (physical or abstract) can be represented in two forms
    - **Analog**: **continuous** set of values (*dense and “without holes”*)
    - **Digital** (or numerical): **discrete** set of values (*all points are isolated*)

---

# 💡️ Discrete Approximation

- Some information is intrinsically discrete
    - “Artificial” information, e.g., written text
    - Atomic or subatomic scale…
- Many physical quantities have a continuous form
    - For their processing on a computer: digital representation
    - *Approximation* of the analog value
    - Error depends on the precision of the chosen digital representation

---

# 💡️ Code

- A system based on symbols, which allows the representation of information
- *Symbol*: atomic element
- *Alphabet*: set of possible symbols (`$A$`)
- *Cardinality* of the code: number of symbols in the alphabet
- *String*: sequence of symbols (`$s \in A^\star$`)
- *Language*: set of well-formed strings (`$L \subseteq A^\star$`)

---

![](http://fondinfo.github.io/images/repr/child-fingers.png)
# 💡️ Positional Code

- A natural number can be represented with a positional notation
    - Sum of positive powers of the base

`$$
N = c_0 \cdot base^0 + c_1 \cdot base^1 + \cdots + c_n \cdot base^n
$$`

- Ex. `$587_{dec} = 7 \cdot 10^0 + 8 \cdot 10^1 + 5 \cdot 10^2$`
- Commonly used positional numbering systems
    - Decimal (base 10; c: `$0-9$`)
    - Binary (base 2; c: `$0-1$`)
    - Hexadecimal (base 16; c: `$0-9, A-F$`)

---

# 💡️ Information Encoding

- Encoding: correspondence rules for converting from one code to another
- Bijective correspondence
    - Between a string in one code
    - And a string in another code
- A certain string in an alphabet rich in symbols corresponds to a longer string in a more reduced alphabet

---


![](http://fondinfo.github.io/images/repr/binary-tunnel.jpg)
# Binary Numbers

---

![](http://fondinfo.github.io/images/repr/sum-binary.jpg)
# 💡️ Binary Code

- Base 2; c: `$0-1$`
- Digital information in computers represented by a sequence of 0s and 1s
    - System invented by Leibniz, ~1700
    - Zuse's programmable computer, ~1940
- **Bit**: single element of a binary sequence
- **Nibble**: sequence of *4 bits*
- **Byte**: sequence of *8 bits*
- *MSB* (Most significant bit): leftmost bit in the sequence
- *LSB* (Least significant bit): rightmost bit in the sequence

>

<https://www.wikihow.com/Convert-from-Binary-to-Decimal>
<br>
<https://www.wikihow.com/Convert-from-Decimal-to-Binary>

---

# ⭐ Decimal → Binary Encoding

- *(1)* Divide the decimal number by 2
- *(2)* The remainder is the value of the new bit, to the left
- *(3)* The quotient is the number to continue with *(loop)*
- That is, continue dividing the quotient by 2 until it becomes zero
- Ex.: `$35_{dec} = 00100011_{bin} = 1·2^0 + 1·2^1 + 1·2^5$`

`$n$`  | `$n \div B$` | `$n \bmod B$` | weight
-------|--------------|---------------|-------
`$35$` |       `$17$` |         `$1$` | `$1 = 2^0$`
`$17$` |        `$8$` |         `$1$` | `$2 = 2^1$`
 `$8$` |        `$4$` |         `$0$` | `$4 = 2^2$`
 `$4$` |        `$2$` |         `$0$` | `$8 = 2^3$`
 `$2$` |        `$1$` |         `$0$` | `$16 = 2^4$`
 `$1$` |        `$0$` |         `$1$` | `$32 = 2^5$`

---

![](http://fondinfo.github.io/images/repr/binary-fingers.svg) … 819
# 🧪 Natural Numbers

- Represent a natural number `$N$` in binary form
- `$k$` bits are needed, such that `$2^k > N$`
- E.g. 4 bits for natural numbers from 0 to 15
- A computer assigns a fixed number of bits for different types of information
    - Cases of non-representable values
    - **Overflow**, **underflow**

---

# 🧪 Powers of 2

| | |
|---|---|
| `$2^1 = 2$`   | `$2^9 = 512$` |
| `$2^2 = 4$`   | `$2^{10} = 1024$` |
| `$2^3 = 8$`   | `$2^{11} = 2048$` |
| `$2^4 = 16$`  | `$2^{12} = 4096$` |
| `$2^5 = 32$`  | `$2^{16} = 65'536$` |
| `$2^6 = 64$`  | `$2^{24} = 16'777'216$` |
| `$2^7 = 128$` | `$2^{32} = 4'294'967'296$` |
| `$2^8 = 256$` | `$2^{64} ≃ 16 × 10^{18}$` |

$1K = 2^{10} ≃ 10^3$, $1M = 2^{20} ≃ 10^6$, $1G = 2^{30} ≃ 10^9$

*Power properties*: $a^x·a^y = a^{x+y}, a^x/a^y = a^{x-y}, (a^x)^y = (a^y)^x = a^{x·y}$

---

# 🧪 Hexadecimal (Hex)

![large](http://fondinfo.github.io/images/repr/hex-numbers.svg)

---

![](http://fondinfo.github.io/images/repr/hex-table.svg)
# 🧪 Bin ↔ Hex

![small](http://fondinfo.github.io/images/repr/bin-hex.png)

- Group of 4 bits: 16 different configurations
    - *Arrangements with repetition*: `$2^4 = 16$`
- Each configuration corresponds to one of the 16 hexadecimal symbols

---

# 🧪 Addition and Subtraction

``` text
    1   1
0 0 0 1 0 1 1 0 +
0 0 0 1 0 1 0 1 =
-----------------
0 0 1 0 1 0 1 1
```

``` text
            0 10
0 0 0 0 1 1 1 0 -
0 0 0 0 0 1 0 1 =
-----------------
0 0 0 0 1 0 0 1
```
>

Pay attention to carry and borrow (at the top)

---

# 🧪 Multiplication

``` text
        1 0 1 1 x
        1 1 0 1 =
        ---------
        1 0 1 1 +
      0 0 0 0
    -------------
      0 1 0 1 1 +
    1 0 1 1
  ---------------
    1 1 0 1 1 1 +
  1 0 1 1
-----------------
1 0 0 0 1 1 1 1
```

---

# 🧪 Division


``` text
1 0 1 1 0 1 : 1 1
0 0          ---------
-----         0 1 1 1 1
1 0 1 -
  1 1
-------
  1 0 1 -
    1 1
  -------
    1 0 0 -
      1 1
    -------
        1 1 -
        1 1
        -----
        0 0
```

---

# 🧪️ Hex and bin in Python

- *Hex* or *bin* values in Python
    - Prefix `0x` or `0b`
    - They are always normal `int` type values
- Conversion from string to number: `int` function
    - The numbering base can also be specified, or `0`
- From number to string: `str`, `hex`, `bin` functions
- [Bitwise operators](https://docs.python.org/3/library/stdtypes.html#bitwise-operations-on-integer-types), bit by bit: `&, |, ^, ~`

``` py
blank_hex = 0x20  # just a plain `int`, valued as 32(dec)
blank_bin = 0b100000  # 32(dec)

i = int("20", 16)  # i is 32(dec)
j = int("0x20", 0)  # base inferred by prefix
txt = hex(32)  # "0x20"
```

---

![](http://fondinfo.github.io/images/repr/sign-magn.svg)
# 💡️ Integers

- Negative numbers also need to be represented
    - A bit must be reserved for the sign
    - This halves the maximum allowed magnitude
- **Magnitude and sign**
    - The first bit (MSB) indicates the sign
    - 0 positive, 1 negative
    - The remaining bits represent the magnitude

---

![](http://fondinfo.github.io/images/repr/twos-compl.svg)
# ⭐ Two's Complement

- Alternative, *different from magnitude and sign representation!*
- Representing a negative number
    - **➊** Start from its positive opposite
    - **➋** Complement the number <br> (1s become 0s and vice versa)
    - **➌** Add 1
- Even so, the first bit (MSB) indicates the sign
    - 0 positive, 1 negative
    - MSB weighs as $-(2^{N-1})$; other bits weigh positively
- ⚠️ *Warning*: you need to know the encoding and number of bits
    - Following examples: each signed integer stored in a single *byte*

---

# 🧪 Ex. Integer Number

- With *one byte*, +35 in binary is: **`0`**`0100011`
- Number –35, in magnitude and sign: **`1`**`0100011`
- Number –35, in two's complement: **`1`**`1011101`

``` text
0 0 1 0 0 0 1 1 ¬
-----------------
1 1 0 1 1 1 0 0 +
              1 =
-----------------
1 1 0 1 1 1 0 1
```

- $-2^7 + 2^6 + 2^4 + 2^3 + 2^2 + 2^0 =$ <br> $-128 + 64 + 16 + 8 + 4 + 1 = -35$

`¬`: simple complement, bit by bit

---

# 🧪 Signed Sum

- Sum 12 and -35 on 8 bits, magnitude and sign
    - Subtraction between 35 and 12
    - Sign change
- Same operation, two's complement
    - Simple sum: `12 + -35 = -23`

``` text
0 0 0 0 1 1 0 0 +
1 1 0 1 1 1 0 1 =
-----------------
1 1 1 0 1 0 0 1
```

>

<https://integer.exposed/>

---

# 💡️ Rational Numbers

- Fractional part: sum of negative powers of the base

`$$
F = c_{-1} \cdot base^{-1} + \cdots + c_{-n} \cdot base^{-n}
$$`

- Two *alternative* representations
    - **Fixed-point**: sign, integer part, decimal part
    - **Floating-point**: sign, mantissa, exponent
- In base 10, [scientific notation](https://it.wikipedia.org/wiki/Notazione_scientifica)
    - Number expressed as: `$m \times 10^n$`
    - `$m$` *mantissa*, `$n$` *exponent*
    - Normalized form: `$1 \leq m < 10$`
    - E.g. Avogadro's number: `$N_A=6.02214076 \times 10^{23}$`

---

# ⭐ Fractional Part in Binary

- **➊** Multiply the fractional part (`$f$`) by 2
- **➋** Assign the integer part of the result (`$\lfloor f \cdot B \rfloor$`) as the bit value *(loop)*
- That is: continue multiplying the fractional part of the result by 2... <br> until it becomes zero

`$f$` | `$f \cdot B$` |  `$\lfloor f \cdot B \rfloor$`  | weight
----------|-------------------|-------|---------
`$0.375$` |       `$0.750$`   | `$0$` | `$2^{-1}$`
`$0.750$` |       `$1.500$`   | `$1$` | `$2^{-2}$`
`$0.500$` |       `$1.000$`   | `$1$` | `$2^{-3}$`

---

# 🧪 Fixed-point

- Number expressed as: `$r = (i, f)$`
    - **`$i$`** is the integer part, `$n_1$` bits
    - **`$f$`** is the fractional part, `$n_2$` bits
- Constant precision along the real axis
    - E.g. `$f$` of 3 bits, consecutive values always spaced by 1/8
    - Between each integer and the next, we can represent 8 values

![](http://fondinfo.github.io/images/repr/fixed-point.png)

---

# ⭐ Floating-point

- Number expressed as: `$r = ±(1+f) \times 2^n$`
    - **`$n$`** is the integer exponent (or characteristic), `$n_1$` bits
    - **`$f$`** is the fractional part (`$0 \leq f < 1$`), `$n_2$` bits
    - `$2$` is the base, `$m = 1+f$` is also called *mantissa*
- Variable precision along the real axis; e.g.:
    - `$f \in \{0, \frac{1}{4}, \frac{2}{4}, \frac{3}{4}\}$`, 2 bits <br> `$n \in \{-2, -1, 0, 1\}$`, 2 bits

![large](http://fondinfo.github.io/images/repr/float4.svg)

>

<http://www.mathworks.com/company/newsletters/news_notes/pdf/Fall96Cleve.pdf>

---

# ⭐ IEEE 754 double & single

- **Double precision**: *64 bits* (~ `$10^{±308}$`, with 16 decimal digits)
    - 1 sign bit, 11 exponent bits, 52 fraction bits
    - `$1023$` (`$=2^{11-1} - 1$`) is added to the exponent
- **Single precision**: *32 bits* (~ `$10^{±38}$`, with 7 decimal digits)
    - `$127$` (`$=2^{8-1} - 1$`) is added to the exponent

![large](http://fondinfo.github.io/images/repr/ieee754-32-ex.svg)

>

<https://www.wikihow.com/Convert-a-Number-from-Decimal-to-IEEE-754-Floating-Point-Representation>

---

# ⭐ IEEE 754 half-precision

- **Half precision**: *16 bits* (~ `$10^{±4.8}$` with 3 decimal digits)
    - Used in GPUs (↓precision ↑speed)
- `$15$` (`$=2^{5 − 1} − 1$`) is added to the exponent
- `$-118.625 = -1110110.101_{bin} = -1.110110101_{bin} × 2^6$`

![small](http://fondinfo.github.io/images/repr/ieee754-16-ex.svg)

>

<https://float.exposed/>

---

# 🔬 Bitwise Operations in Python

- *Bitwise* operators, applied bit by bit
- Not to be confused with logical operators (`and`, `or`, `not`)

``` py
x = 0b1011  # bin value (11 dec)
y = 0x2A    # hex value (42 dec)

bin(42)     # "0b101010", a string
hex(42)     # "0x2a", a string

x & y       # bitwise AND (applied for each couple of bits)
x | y       # bitwise OR
x ^ y       # bitwise XOR
~x          # bitwise complement, 0b...11110100

shift = 3   # some int
x << shift  # x = x * (2 ** shift)
y >> shift  # y = y / (2 ** shift)
```

---

# Equality and Proximity

- Discrete approximation of real numbers
- ⚠️ Pay attention to equality comparisons

``` py
>>> 0.2 + 0.1 == 0.3
False
```

``` py
for i in range(360):
    a = math.radians(i)
    print(math.sin(a) ** 2 + math.cos(a) ** 2 == 1)  # fails ~¼ of times
```

- *Solutions*: *proximity* comparisons — 👉 [`isclose`](https://docs.python.org/3/library/math.html#math.isclose)

```
>>> abs(x - y) <= 10 ** -9
True
>>> math.isclose(x, y)
True
```

---

![](http://fondinfo.github.io/images/misc/characters.png)
# Characters and Text

---

# 💡️ Characters and Text

- A convention for numerical (binary) encoding of characters is needed
- **ASCII** (American Standard Code for Information Interchange) 7-bit encoding
    - *Alphanumeric characters*: uppercase letters, lowercase letters, numbers, space
    - *Symbols and punctuation*: `@`, `#`, …
    - *Control characters* (not all displayable): `TAB, LF, CR, BELL` etc.

---

# ⭐ Base ASCII Table

![large](http://fondinfo.github.io/images/repr/ascii.svg)

- Each row has 16 characters with consecutive codes
- Character code: count all characters preceding it
    - E.g. `S` @ `x=3`, `y=5` ⇒ `ord("S") == y * 16 + x == 83`

---

# ⭐ Line Break

- Unix: `LF` (*Line Feed, `0A`*)
    - Multics, Unix etc., Mac OS X, BeOS, Amiga, RISC OS
- Old Apple: `CR` (*Carriage Return, `0D`*)
    - Commodore, Apple II family, Mac OS up to version 9
- Windows: `CR+LF` (*`0D+0A`*)
    - Most early OSes, DOS, OS/2, Windows, Symbian

---

![large](http://fondinfo.github.io/images/repr/codepage-437.png)
# 💡️ Extended ASCII Table

- Accented characters + graphic characters
    - *Code Page 437* for PC (DOS) in North America
    - Possible to mix English and French text (although in France *CP850*)
    - But not together with Greek (*CP737*), Russian, etc.
- **ISO 8859**, standard 8-bit ASCII extensions
    - ISO 8859-1 (or Latin1): Western European Languages
    - ISO 8859-2: Eastern European Languages
    - ISO 8859-5: Cyrillic alphabet
    - ISO 8859-15: Latin1 with euro symbol (€)

---

![](http://fondinfo.github.io/images/repr/hieroglyphics.jpg) ![](http://fondinfo.github.io/images/repr/no-klingon.png)
# 💡️ Unicode

- Unicode associates a precise **code-point** (32 bits) with each symbol
    - Possible to represent billions of symbols
    - First 256 code-points = *Latin1*
- Currently >30 writing systems
    - Representation of *hieroglyphs* and *cuneiform* characters
    - From *emoticons* **:-)** to *emoji* **☺️**: ideograms for facial expressions, common objects, places, weather events, and animals
    - Proposal for *Klingon* (from Star Trek… rejected!)

>

<http://fondinfo.github.io/data/utf8-demo.txt>
<br>
[More examples of multimedia files](http://fondinfo.github.io/data/)

---

![small](http://fondinfo.github.io/images/repr/unicode.svg)
![](http://fondinfo.github.io/images/repr/text-len.png)
# ⭐ Unicode Transformation Format

- Encoding of a *code-point* into a bit sequence
    - One or more **code-units** are needed
- *UTF-32* – 32-bit code-unit, always 1 c.u.
- *UTF-16* – 16-bit code-unit, length 1-2 c.u.
- *UTF-8* – 8-bit code-unit, length 1-4 c.u.
    - Max compatibility with ASCII

![](http://fondinfo.github.io/images/repr/utf8.jpg)

---

![](http://fondinfo.github.io/images/repr/utf8-web-growth.svg)
# ⭐ UTF-8

- If highest bit is `0` in the *code-point*
    - ASCII symbol on 7 bits, unchanged
- Otherwise, encoded on `n` *code-units* (bytes)
    - First byte starts with `n` bits set to `1`, then one to `0`
    - Subsequent bytes all start with `10`
- Payload bits / encoding length: `7/8`, `11/16`, `16/24`, `21/32`

![large](http://fondinfo.github.io/images/repr/utf8-examples.png)

>

[Pike&Thompson: UTF-8 designed on a placemat](https://www.cl.cam.ac.uk/~mgk25/ucs/utf-8-history.txt)

---

# 🧪️ UTF-8 in Python

- Type **`bytes`**: immutable sequence of bytes
    - `encode` method to encode `str` → `bytes`
    - `decode` method to decode `bytes` → `str`
    - Formats `"utf-8"`, `"utf-32-be"`…
- `hex` method to represent `bytes`
    - Separator between bytes, optional
    - Inverse operation with `bytes.fromhex`
- Insert hex code-points into a string: `\x…`, `\u…` and `\U…`

``` py
>>> txt = "My 2¢ 😉"  # or: "My 2\xa2 \U0001f609"
>>> enc = txt.encode("utf-8")  # `bytes`
>>> enc.hex(" ")
"4d 79 20 32 c2 a2 20 f0 9f 98 89"
>>> enc.decode("utf-8")  # back to `str`
"My 2¢ 😉"
```
