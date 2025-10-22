
![](http://fondinfo.github.io/images/repr/binary-hacker.jpg)
# Codifica dell'informazione
## Introduzione all'informatica <br> Michele Tomaiuolo @ Ingegneria UniPR

---

![](http://fondinfo.github.io/images/repr/analog-clock.png) ![](http://fondinfo.github.io/images/repr/digital-clock.png)
# 💡️ Analogico e digitale

- Una grandezza (fisica o astratta) può essere rappresentata in due forme
    - **Analogica**: insieme di valori **continuo** (*denso e “senza buchi”*)
    - **Digitale** (o numerica): insieme di valori **discreto** (*tutti i punti sono isolati*)

---

# 💡️ Approssimazione discreta

- Alcune informazioni sono intrinsecamente discrete
    - Informazioni “artificiali”, es. un testo scritto
    - Scala atomica o subatomica …
- Molte grandezze fisiche hanno forma continua
    - Per loro elaborazione al calcolatore: rappresentazione digitale
    - *Approssimazione* del valore analogico
    - Errore dipende dalla precisione della rappresentazione digitale scelta

---

# 💡️ Codice

- Sistema basato su simboli, che permette la rappresentazione dell’informazione
- *Simbolo*: elemento atomico
- *Alfabeto*: insieme dei simboli possibili (`$A$`)
- *Cardinalità* del codice: numero di simboli dell’alfabeto
- *Stringa* : sequenza di simboli (`$s \in A^\star$`)
- *Linguaggio* : insieme stringhe ben formate (`$L \subseteq A^\star$`)

---

![](http://fondinfo.github.io/images/repr/child-fingers.png)
# 💡️ Codice posizionale

- Un numero naturale può essere rappresentato con una notazione posizionale
    - Somma di potenze positive della base

`$$
N = c_0 \cdot base^0 + c_1 \cdot base^1 + \cdots + c_n \cdot base^n
$$`

- Es. `$587_{dec} = 7 \cdot 10^0 + 8 \cdot 10^1 + 5 \cdot 10^2$`
- Sistemi di numerazione posizionali di uso comune
    - Decimale (base 10; c: `$0-9$`)
    - Binario (base 2; c: `$0-1$`)
    - Esadecimale (base 16; c: `$0-9, A-F$`)

---

# 💡️ Codifica dell’informazione

- Codifica: regole di corrispondenza per passare da un certo codice a un altro
- Corrispondenza biunivoca
    - Tra una stringa di un codice
    - E una stringa di un altro codice
- A una certa stringa in un alfabeto ricco di simboli, corrisponde una stringa più lunga in un alfabeto più ridotto

---


![](http://fondinfo.github.io/images/repr/binary-tunnel.jpg)
# Numeri binari

---

![](http://fondinfo.github.io/images/repr/sum-binary.jpg)
# 💡️ Codice binario

- Base 2; c: `$0-1$`
- Informazione digitale nei calcolatori rappresentata con una sequenza di 0 e 1
    - Sistema ideato da Leibniz, ~1700
    - Calcolatore programmabile di Zuse, ~1940
- **Bit**: singolo elemento di una sequenza binaria
- **Nibble**: sequenza di *4 bit*
- **Byte**: sequenza di *8 bit*
- *MSB* (Most significant bit): bit più a sinistra nella sequenza
- *LSB* (Least significant bit): bit più a destra nella sequenza

>

<https://www.wikihow.com/Convert-from-Binary-to-Decimal>
<br>
<https://www.wikihow.com/Convert-from-Decimal-to-Binary>

---

# ⭐ Codifica decimale → binaria

- *(1)* Dividere il numero decimale per 2
- *(2)* Il resto è il valore del nuovo bit, a sinistra
- *(3)* Il quoziente è il numero con cui continuare *(loop)*
- Ossia continuare a dividere per 2 il quoziente, finché non si annulla
- Es.: `$35_{dec} = 00100011_{bin} = 1·2^0 + 1·2^1 + 1·2^5$`

`$n$`  | `$n \div B$` | `$n \bmod B$` | peso
-------|--------------|---------------|-------
`$35$` |       `$17$` |         `$1$` | `$1 = 2^0$`
`$17$` |        `$8$` |         `$1$` | `$2 = 2^1$`
 `$8$` |        `$4$` |         `$0$` | `$4 = 2^2$`
 `$4$` |        `$2$` |         `$0$` | `$8 = 2^3$`
 `$2$` |        `$1$` |         `$0$` | `$16 = 2^4$`
 `$1$` |        `$0$` |         `$1$` | `$32 = 2^5$`

---

![](http://fondinfo.github.io/images/repr/binary-fingers.svg) … 819
# 🧪 Numeri naturali

- Rappresentare un numero naturale `$N$` in forma binaria
- Occorrono `$k$` bit, t.c. `$2^k > N$`
- Es. 4 bit per numeri naturali da 0 a 15
- Un calcolatore assegna un numero fisso di bit per diversi tipi di informazione
    - Casi di valori non rappresentabili
    - **Overflow**, **underflow**

---

# 🧪 Potenze di 2

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

*Proprietà potenze*: $a^x·a^y = a^{x+y}, a^x/a^y = a^{x-y}, (a^x)^y = (a^y)^x = a^{x·y}$

---

# 🧪 Esadecimale (Hex)

![large](http://fondinfo.github.io/images/repr/hex-numbers.svg)

---

![](http://fondinfo.github.io/images/repr/hex-table.svg)
# 🧪 Bin ↔ Hex

![small](http://fondinfo.github.io/images/repr/bin-hex.png)

- Gruppo di 4 bit: 16 configurazioni diverse
    - *Disposizioni con ripetizione*: `$2^4 = 16$`
- Ciascuna configurazione corrisponde a uno dei 16 simboli esadecimali

---

# 🧪 Somma e sottrazione

``` text
 0 +         1 +         1 +         1 +
 0 +         0 +         1 +         1 +
 0 =         0 =         0 =         1 =
----        ----        ----        ----
 0           1          10          11
```

``` text
    1   1                            0 10
0 0 0 1 0 1 1 0 +        0 0 0 0 1 1 1 0 -
0 0 0 1 0 1 0 1 =        0 0 0 0 0 1 0 1 =
-----------------        -----------------
0 0 1 0 1 0 1 1          0 0 0 0 1 0 0 1
```

>

Attenzione a riporto e prestito (in alto)

---

# 🧪 Moltiplicazione

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

# 🧪 Divisione


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

# 🧪️ Hex e bin in Python

- Valori *hex* o *bin* in Python
    - Prefisso `0x` o `0b`
    - Sono sempre normali valori di tipo `int`
- Conversione da stringa a numero: funzione `int`
    - Si può specificare anche la base di numerazione, oppure `0`
- Da numero a stringa: funzioni `str`, `hex`, `bin`
- [Operatori bitwise](https://docs.python.org/3/library/stdtypes.html#bitwise-operations-on-integer-types), bit a bit: `&, |, ^, ~`

``` py
blank_hex = 0x20  # just a plain `int`, valued as 32(dec)
blank_bin = 0b100000  # 32(dec)

i = int("20", 16)  # i is 32(dec)
j = int("0x20", 0)  # base inferred by prefix
txt = hex(32)  # "0x20"
```

---

![](http://fondinfo.github.io/images/repr/sign-magn.svg)
# 💡️ Numeri interi

- Occorre rappresentare anche i numeri negativi
    - Necessario riservare un bit per il segno
    - Ovvero, si dimezza il massimo modulo ammesso
- **Modulo e segno**
    - Il primo bit (MSB) indica il segno
    - 0 positivo, 1 negativo
    - I restanti bit rappresentano il modulo

---

![](http://fondinfo.github.io/images/repr/twos-compl.svg)
# ⭐ Complemento a due

- Alternativa, rappr. *diversa da modulo e segno!*
- Rappresentare un numero negativo
    - **➊** Partire dal suo opposto positivo
    - **➋** Complementare il numero <br> (gli 1 diventano 0 e viceversa)
    - **➌** Sommare 1
- Anche così, il primo bit (MSB) indica il segno
    - 0 positivo, 1 negativo
    - MSB pesa come $-(2^{N-1})$; altri bit pesano in positivo
- ⚠️ *Attenzione*: bisogna conoscere codifica e num bit
    - Esempi seguenti: ogni intero con segno memorizzato in un singolo *byte*

---

# 🧪 Es. numero intero

- Avendo *un byte*, +35 è in binario: **`0`**`0100011`
- Numero –35, in modulo e segno: **`1`**`0100011`
- Numero –35, in complemento a due: **`1`**`1011101`

``` text
0 0 1 0 0 0 1 1 ¬
-----------------
1 1 0 1 1 1 0 0 +
              1 =
-----------------
1 1 0 1 1 1 0 1
```

- $-2^7 + 2^6 + 2^4 + 2^3 + 2^2 + 2^0 =$ <br> $-128 + 64 + 16 + 8 + 4 + 1 = -35$

`¬`: complemento semplice, bit a bit

---

# 🧪 Somma con segno

- Sommare 12 e -35 su 8 bit, modulo e segno
    - Sottrazione tra 35 e 12
    - Cambio di segno
- Stessa operazione, complemento a due
    - Semplice somma: `12 + -35 = -23`

``` text
0 0 0 0 1 1 0 0 +
1 1 0 1 1 1 0 1 =
-----------------
1 1 1 0 1 0 0 1
```

>

<https://integer.exposed/>

---

# 💡️ Numeri razionali

- Parte frazionaria: somma di potenze negative della base

`$$
F = c_{-1} \cdot base^{-1} + \cdots + c_{-n} \cdot base^{-n}
$$`

- Due rappresentazioni *alternative*
    - **Virgola fissa**: segno, parte intera, parte decimale
    - **Virgola mobile**: segno, mantissa, esponente
- In base 10, [notazione scientifica](https://it.wikipedia.org/wiki/Notazione_scientifica)
    - Numero espresso come: `$m \times 10^n$`
    - `$m$` *mantissa*, `$n$` *esponente*
    - Forma normalizzata: `$1 \leq m < 10$`
    - P.es. Numero di Avogadro: `$N_A=6.02214076 \times 10^{23}$`

---

# ⭐ Parte frazionaria in binario

- **➊** Moltiplicare la parte frazionaria (`$f$`) per 2
- **➋** Assegnare la parte intera del risultato (`$\lfloor f \cdot B \rfloor$`) come valore del bit *(loop)*
- Ossia: continuare a moltiplicare per 2 la parte frazionaria del risultato... <br> finché non si annulla

`$f$` | `$f \cdot B$` |  `$\lfloor f \cdot B \rfloor$`  | peso
----------|-------------------|-------|---------
`$0.375$` |       `$0.750$`   | `$0$` | `$2^{-1}$`
`$0.750$` |       `$1.500$`   | `$1$` | `$2^{-2}$`
`$0.500$` |       `$1.000$`   | `$1$` | `$2^{-3}$`

---

# 🧪 Virgola fissa

- Numero espresso come: `$r = (i, f)$`
    - **`$i$`** è la parte intera, `$n_1$` bit
    - **`$f$`** è la parte frazionaria, `$n_2$` bit
- Precisione costante lungo l’asse reale
    - P.es. `$f$` di 3 bit, valori consecutivi sempre distanziati di 1/8
    - Tra ciascun intero e il successivo, possiamo rappresentare 8 valori

![](http://fondinfo.github.io/images/repr/fixed-point.png)

---

# ⭐ Virgola mobile

- Numero espresso come: `$r = ±(1+f) \times 2^n$`
    - **`$n$`** è l'esponente intero (o caratteristica), `$n_1$` bit
    - **`$f$`** è la parte frazionaria (`$0 \leq f < 1$`), `$n_2$` bit
    - `$2$` è la base, `$m = 1+f$` è anche detto *mantissa*
- Precisione variabile lungo l’asse reale; p.es.:
    - `$f \in \{0, \frac{1}{4}, \frac{2}{4}, \frac{3}{4}\}$`, 2 bit <br> `$n \in \{-2, -1, 0, 1\}$`, 2 bit

![large](http://fondinfo.github.io/images/repr/float4.svg)

>

<http://www.mathworks.com/company/newsletters/news_notes/pdf/Fall96Cleve.pdf>

---

# ⭐ IEEE 754 double & single

- **Precisione doppia**: *64 bit* (~ `$10^{±308}$`, con 16 cifre decimali)
    - 1 bit di segno, 11 bit di esponente, 52 bit di frazione
    - All'esponente si somma `$1023$` (`$=2^{11-1} - 1$`)
- **Precisione singola**: *32 bit* (~ `$10^{±38}$`, con 7 cifre decimali)
    - All'esponente si somma `$127$` (`$=2^{8-1} - 1$`)

![large](http://fondinfo.github.io/images/repr/ieee754-32-ex.svg)

>

<https://www.wikihow.com/Convert-a-Number-from-Decimal-to-IEEE-754-Floating-Point-Representation>

---

# ⭐ IEEE 754 half-precision

- **Mezza precisione**: *16 bit* (~ `$10^{±4.8}$` con 3 cifre decimali)
    - Usata nelle GPU (↓precisione ↑velocità)
- All’esponente si somma `$15$` (`$=2^{5 − 1} − 1$`)
- `$-118.625 = -1110110.101_{bin} = -1.110110101_{bin} × 2^6$`

![small](http://fondinfo.github.io/images/repr/ieee754-16-ex.svg)

>

<https://float.exposed/>

---

<!-- .slide: data-visibility="hidden" -->

# 🔬 Operazioni bit a bit in Python

- Operatori *bitwise*, applicati bit a bit
- Da non confondere con operatori logici (`and`, `or`, `not`)

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

# Uguaglianza e prossimità

- Approssimazione discreta dei reali
- ⚠️ Attenzione ai confronti di uguaglianza

``` py
>>> 0.2 + 0.1 == 0.3
False
```

``` py
for i in range(360):
    a = math.radians(i)
    print(math.sin(a) ** 2 + math.cos(a) ** 2 == 1)  # fails ~¼ of times
```

- *Soluzioni* : confronti di *prossimità* — 👉 [`isclose`](https://docs.python.org/3/library/math.html#math.isclose)

```
>>> abs(x - y) <= 10 ** -9
True
>>> math.isclose(x, y)
True
```

---

![](http://fondinfo.github.io/images/misc/characters.png)
# Caratteri e testo

---

# 💡️ Caratteri e testo

- Necessaria convenzione per codifica numerica (binaria) dei caratteri
- Codifica **ASCII** (American Standard Code for Information Interchange) a 7 bit
    - *Caratteri alfanumerici*: lettere maiuscole, minuscole, numeri, spazio
    - *Simboli e punteggiatura*: `@`, `#`, …
    - *Caratteri di controllo* (non tutti visualizzabili): `TAB, LF, CR, BELL` ecc.

---

# ⭐ Tabella ASCII di base

![large](http://fondinfo.github.io/images/repr/ascii.svg)

- In ogni riga 16 caratteri con codici consecutivi
- Codice di un carattere: si contano tutti quelli che lo precedono
    - Es. `S` @ `x=3`, `y=5` ⇒ `ord("S") == y * 16 + x == 83`

---

# ⭐ Interruzione di riga

- Unix: `LF` (*Line Feed, `0A`*)
    - Multics, Unix etc., Mac OS X, BeOS, Amiga, RISC OS
- Vecchi Apple: `CR` (*Carriage Return, `0D`*)
    - Commodore, Apple II family, Mac OS up to version 9
- Windows: `CR+LF` (*`0D+0A`*)
    - Most early OSes, DOS, OS/2, Windows, Symbian

---

![large](http://fondinfo.github.io/images/repr/codepage-437.png)
# 💡️ Tabella ASCII estesa

- Caratteri accentati + caratteri per grafici
    - *Code Page 437* per PC (DOS) in Nord America
    - Possibile mischiare testo in inglese e francese (anche se in Francia *CP850*)
    - Ma non assieme greco (*CP737*), russo ecc.
- **ISO 8859**, estensioni standard per ASCII a 8 bit
    - ISO 8859-1 (o Latin1): Lingue dell’Europa Occidentale
    - ISO 8859-2: Lingue dell’Europa Orientale
    - ISO 8859-5: Alfabeto cirillico
    - ISO 8859-15: Latin1 con simbolo euro (€)

---

![](http://fondinfo.github.io/images/repr/hieroglyphics.jpg) ![](http://fondinfo.github.io/images/repr/no-klingon.png)
# 💡️ Unicode

- Unicode associa un preciso **code-point** (32 bit) a ciascun simbolo
    - Possibile rappresentare miliardi di simboli
    - Primi 256 code-point = *Latin1*
- Attualmente >30 sistemi di scrittura
    - Rappresentazione di *geroglifici* e caratteri *cuneiformi*
    - Da *emoticon* **:-)** a *emoji* **☺️**: ideogrammi per espressioni facciali, oggetti comuni, posti, eventi meteo e animali
    - Proposta per *Klingon* (da Star Trek… rifiutata!)

>

<http://fondinfo.github.io/data/utf8-demo.txt>
<br>
[Altri esempi di file multimediali](https://fondinfo.github.io/data)

---

![small](http://fondinfo.github.io/images/repr/unicode.svg)
![](http://fondinfo.github.io/images/repr/text-len.png)
# ⭐ Unicode Transformation Format

- Codifica di un *code-point* in una sequenza di bit
    - Servono uno o più **code-unit**
- *UTF-32* – code-unit di 32-bit, sempre 1 c.u.
- *UTF-16* – code-unit di 16-bit, lunghezza 1-2 c.u.
- *UTF-8* – code-unit di 8-bit, lunghezza 1-4 c.u.
    - Max compatibilità con ASCII

![](http://fondinfo.github.io/images/repr/utf8.jpg)

---

![](http://fondinfo.github.io/images/repr/utf8-web-growth.svg)
# ⭐ UTF-8

- Se bit più alto a `0`, nel *code-point*
    - Simbolo ASCII su 7 bit, invariato
- Altrimenti, codifica su `n` *code-unit* (byte)
    - Primo byte inizia con `n` bit a `1`, poi uno a `0`
    - Byte seguenti cominciano tutti con `10`
- Bit di payload / lunghezza codifica: `7/8`, `11/16`, `16/24`, `21/32`

![large](http://fondinfo.github.io/images/repr/utf8-examples.png)

>

[Pike&Thompson: UTF-8 designed on a placemat](https://www.cl.cam.ac.uk/~mgk25/ucs/utf-8-history.txt)

---

# 🧪️ UTF-8 in Python

- Tipo **`bytes`** : sequenza immutabile di byte
    - Metodo `encode` per codificare `str` → `bytes`
    - Metodo `decode` per decodificare `bytes` → `str`
    - Formati `"utf-8"`, `"utf-32-be"`…
- Metodo `hex` per rappresentare `bytes`
    - Separatore tra i byte, opzionale
    - Operazione inversa con `bytes.fromhex`
- Inserire code-point hex in una stringa: `\x…`, `\u…` e `\U…`

``` py
>>> txt = "My 2¢ 😉"  # or: "My 2\xa2 \U0001f609"
>>> enc = txt.encode("utf-8")  # `bytes`
>>> enc.hex(" ")
"4d 79 20 32 c2 a2 20 f0 9f 98 89"
>>> enc.decode("utf-8")  # back to `str`
"My 2¢ 😉"
```
