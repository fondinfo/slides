![](https://fondinfo.github.io/images/fun/shopping-list.png)
# Sequenze
## Introduzione alla programmazione

---

# Liste e indici

---

![](http://fondinfo.github.io/images/fun/shopping-list.png)
# ⭐ Lista

- Sequenza mutabile di elementi omogenei

``` py
groceries = ["spam", "egg", "beans"]
rainfall_data = [13, 24, 18, 15]
```

- A volte serve una lista di dimensione già nota
- I valori saranno calcolati durante l'esecuzione

``` py
results_by_month = [0] * 12  # 12 times 0 (list repetition)
```

---

![](http://fondinfo.github.io/images/misc/rock-cubes.png)
# ⭐ Cicli su liste: for

``` py
values = [2, 3, 5, 7, 11]

print("Cubes:")

for val in values:
    cube = val ** 3
    print(cube, end="\t")
```

``` text
8   27  125 343 1331
```

- A ogni iterazione, a `val` è assegnato un elemento di `values`
- Ciclo `for` per qualsiasi tipo di sequenza
    - `list`, `str`, `tuple`, `range`…

---

![](http://fondinfo.github.io/images/fun/wile-coyote.png)
# ⭐ Accesso agli elementi

- **Attenzione a usare indici validi!**
    - *Lunghezza* attuale di una lista `s`: `len(s)`
    - Elementi *numerati* da `0` a `len(s)-1`

``` py
groceries = ["spam", "egg", "beans", "bacon"]
n = len(groceries)           # 4
groceries[0]                 # "spam"
groceries[1]                 # "egg"
groceries[n-1]               # "bacon"
groceries[1] = "ketchup"     # replace a value, len is still 4
groceries.append("sausage")  # add to the end, len is 5
groceries                    # guess!
```

---

![](http://fondinfo.github.io/images/fun/month-list.svg)
# 🧪 Elementi e slice

- Indici *negativi* contano dalla fine
    - Da `-1` (ultimo) a `-len(s)` (primo)

``` py
months = ["Jan", "Feb", "Mar", "Apr", "May", "Jun",
          "Jul", "Aug", "Sep", "Oct", "Nov", "Dec"]
n = len(months)            # 12
months[3]                  # "Apr"
months[-2]                 # "Nov", same as n - 2
```

``` py
spring = months[2:5]       # ["Mar", "Apr", "May"]
quart1 = months[:3]        # ["Jan", "Feb", "Mar"]
quart4 = months[-3:]       # ["Oct", "Nov", "Dec"]
whole_year = months[:]     # Copy of the whole list
```

---

# 🧪 Inserimento e rimozione

``` py
groceries = ["spam", "egg", "beans"]

groceries[0] = "sausage"      # replace an element

groceries.append("bacon")     # add an element to the end
groceries.pop()               # remove (and return) last element

groceries.insert(1, "bacon")  # other elements shift
removed = groceries.pop(1)    # remove (and return) element at index

i = groceries.index("egg")    # 1, index of "egg" in groceries
if "egg" in groceries:        # True, groceries contains "egg"
    groceries.remove("egg")   # remove an element by value

groceries.clear()             # remove everything, groceries is empty now
```

---

# 🔬 Uguaglianza e identità

``` py
a = ["spam", "egg", "beans"]
b = a[:]         # new list!
b == a           # True, they contain the same values
b is a           # ❗ False, they are two objects in memory
                 # (try and modify one of them...)
c = a
c is a           # ❗ True, same object in memory
                 # (try and modify one of them...)
d = ["sausage", "tomato"]
groceries = c + d  # list concatenation --> new list!

# Lexicographical comparison of lists (or strings, tuples...)
# Compare the first two *different* elements
[2, 0, 0] > [1, 2, 0]  # True: 2 > 1
[2, 1, 0] > [2, 0, 1]  # True: 2 == 2, 1 > 0
```

---

# 🧪 Funzioni su liste

- Parametri passati *per assegnamento* (~ etichette)
    - ⇒ Modifiche agli oggetti: permanenti

``` py
def append_fib(data: list[int]):
    val = len(data)
    if val >= 2:
        val = data[-2] + data[-1]
    data.append(val)

def main():
    values = []
    for _ in range(12):
        append_fib(values)
        print(values)  # let's see what's going on
```

>

<https://fondinfo.github.io/play/?c08_fibonacci.py>

---

![](http://fondinfo.github.io/images/fun/fun-reset.svg)
# 🧪 Variabili e valori

- ❓ Qual è l'output del seguente programma?
- ❓ E se invece assegniamo a `data` una lista vuota?
    - Anzichè chiamare il suo metodo `clear`

``` py
def reset(data: list):
    data.clear()
    #data = []

def main():
    nums = [1, 2, 3]
    reset(nums)
    print(nums)

main()
```

>

<https://fondinfo.github.io/play/?c08_reset.py>

---

# 🧪 Stringhe e liste

- **Stringa**: sequenza *immutabile* di caratteri

``` py
txt = "Monty Python's Flying Circus"
txt[3]    # "t"
txt[-2]   # "u"
txt[6:12] # "Python"
txt[-6:]  # "Circus"
```

- **`join`** : da lista di stringhe a stringa unica
- **`split`** : da stringa unica a lista di stringhe
	- Senza parametri, separa in base a sequenze di caratteri bianchi
    - `" ", "\n", "\t"`…
	
``` py
whole = "|".join(["tue", "thu", "sat"])  # "tue|thu|sat"
days = "mon|wed|fri".split("|")  # ["mon", "wed", "fri"]
```

---

# Spacchettamento

- Qualsiasi sequenza può essere spacchettata su un *numero corrispondente* di variabili

``` py
>>> a, b, c = [1, 2, 3]
```

- Assegnamento *con stella* per catturare una sequenza in una lista
	- Provare a omettere `first`, `second`, o `last`

``` py
>>> first, second, *middle, last = [0, 1, 2, 3, 4, 5]  # range(6)
>>> first
0
>>> second
1
>>> middle
[2, 3, 4]
>>> last
5
```

---

![](http://fondinfo.github.io/images/misc/characters.png)
# 🧪 Cicli su stringhe

- Il ciclo `for` scorre i valori di qualsiasi sequenza
- Una stringa è una sequenza di caratteri

``` py
line = input("Text? ").lower()
digits, vowels = 0, 0

for c in line:
    if "0" <= c <= "9":  # char comparison
        digits += 1
    elif c in "aeiou":  # membership test
        vowels += 1
```

>

<https://fondinfo.github.io/play/?c03_vowels.py>

---

![](http://fondinfo.github.io/images/fun/brackets.svg)
# 🧪 Testo tra marcatori

- Di un testo, trascrivere solo parti comprese tra `<` e `>`
    - Se manca `>` dopo `<`, trascrivere fino alla fine

``` py
text = input("Text? ")
inside = False

for c in text:
    if c == "<" and not inside:
        inside = True
    elif c == ">" and inside:
        inside = False
        print()
    elif inside:
        print(c, end="")
```

>

<https://fondinfo.github.io/play/?c08_brackets.py>

---

![](http://fondinfo.github.io/images/misc/numbers.png)
# 🧪 Lista di contatori

- Contare separatamente le cifre in un testo
    - Quanti `0`? Quanti `1`? …
    - `10` condizioni, `10` variabili contatore
    - Oppure lista di `10` elementi

``` py
text = input("Text? ")
counters = [0] * 10

for c in text:
    if "0" <= c <= "9":
        counters[int(c)] += 1

print(counters)
```

>

<https://fondinfo.github.io/play/?c08_counters.py>

---

# 🧪 Tupla

- Sequenza **immutabile** di valori, anche di *tipo diverso*

``` py
# Tuple packing
pt = (5, 6, "red")
pt[0]  # 5
pt[1]  # 6
pt[2]  # "red"

# Sequence unpacking (from a list, string, tuple...)
x, y, colour = pt
a, b = 3, 4
a, b = b, a
```

---

![](http://fondinfo.github.io/images/fun/rollinz.jpg)
# ⭐ Insieme

- Collezione non ordinata e *senza ripetizioni*
    - Senza chiavi o indici
- Metodi `add` e `discard`
    - Aggiunta e rimozione
- Operatori `in`, `|` e `&`
    - Appartenenza, unione e intersezione

``` py
numbers = {1, 4, 5}
numbers.add(4)  # {1, 4, 5}
few = numbers & {4, 5, 6}  # {4, 5}, intersection
many = numbers | {3, 4}  # {1, 3, 4, 5}, union

empty_set = set()  # ⚠️ {} is an empty dict
```

>

<https://docs.python.org/3/library/stdtypes.html#set>

---

![](http://fondinfo.github.io/images/fun/dictionary.png)
# ⭐ Dizionario

- Chiamato anche *mappa* o *array associativo*
- Raccolta di coppie **chiave**-**valore**
- Chiave: *indice* per accedere al valore
    - Le chiavi sono *uniche* (~ `list`)
    - Tipo *`str`*, o altro tipo immutabile

``` py
tel = {"john": 4098, "terry": 4139}  # dict[str, int]
if "john" in tel:
    print(tel["john"])  # 4098, ⚠️ error for a missing key
tel["graham"] = 4127
for k, v in tel.items():
    print(k, v)  # john 4098 ⏎ terry 4139 ⏎ graham 4127 ⏎
```

>

Vedi: [get](https://docs.python.org/3/library/stdtypes.html#dict.get),
[keys](https://docs.python.org/3/library/stdtypes.html#dict.keys),
[values](https://docs.python.org/3/library/stdtypes.html#dict.values),
[items](https://docs.python.org/3/library/stdtypes.html#dict.items) <br>
<https://docs.python.org/3/library/stdtypes.html#dict>

---

`$\begin{pmatrix}5 & 0 & 0 & 0 \\ 0 & 8 & 0 & 0 \\ 0 & 0 & 3 & 0 \\ 0 & 6 & 0 & 0\end{pmatrix}$`
# 🧪 Matrice sparsa

- Matrice con molte celle “vuote”
- Oppure chiavi sparse, non numeriche
- Dizionario con chiavi di tipo *tupla*
- Metodo `dict.get` con valore di *default*

``` py
values = {(0, 0): 5, (1, 1): 8,
          (2, 2): 3, (1, 3): 6}  # dict[(int, int), int]

x = int(input("Col? "))
y = int(input("Row? "))
val = values.get((x, y), 0)  # key not found → default 0
print(val)
```

>

<https://docs.python.org/3/library/stdtypes.html#dict>

---

# 🥷 Funzioni su sequenze

---

![](http://fondinfo.github.io/images/misc/thanos-glove.png)
# 🥷 List comprehension

- Modo conciso per creare una lista, rielaborando una data sequenza
    - Espressione di *output*
    - Variabile di *iterazione*
    - Sequenza di *input*
- Condizione sugli elementi, opzionale

``` py
squares = [x ** 2 for x in range(5)]  # [0, 1, 4, 9, 16]
# squares = []
# for x in range(5):
#    squares.append(x ** 2)
```

``` py
nums = [int(c) for c in "h3ll0 w0rld" if "0" <= c <= "9"]
# [3, 0, 0]
```

---

![](http://fondinfo.github.io/images/fun/zip.png)
# 🥷 Zip

- Accoppia elementi di due (o +) sequenze
- Genera sequenza *lazy* di coppie (tuple)
- Lunghezza della sequenza più breve
- **Laziness**: risultati calcolati non subito
    - Solo quando servono

``` py
groceries = ["spam", "egg", "beans"]
quantities = ["100 g", "6 pc", "200 g", "too much"]

for p, q in zip(groceries, quantities):  # unpacking
    print(p, q, end=" § ")
# spam 100 g § egg 6 pc § beans 200 g §

z = list(zip(groceries, quantities))  # if you *really* need a list
# [("spam", "100 g"), ("egg", "6 pc"), ("beans", "200 g")]
```

---

![](http://fondinfo.github.io/images/repr/child-fingers.png)
# 🥷 Enumerate

- Accoppia un indice crescente con i valori di una sequenza
- Genera sequenza *lazy* di coppie
- Iterazioni con valore e indice assieme

``` py
groceries = ["spam", "egg", "bacon", "sausage"]

for i, val in enumerate(groceries):  # ~ zip(range(4), groceries)
    print(i, val, end=" § ")
# 0 spam § 1 egg § 2 bacon § 3 sausage §

e = list(enumerate(groceries))  # if you *really* need a list
[(0, "spam"), (1, "egg"), (2, "bacon"), (3, "sausage")]
```

---

# 🥷 Liste ordinate o rovesciate

- Funzioni `sorted` e `reversed` non alterano la lista
- Metodi `sort` e `reverse` alterano la lista (*in place*)
- Parametro `key`: contronto tra risultati di una *funzione*

``` py
groceries = ["spam", "bacon", "egg"]
s1 = sorted(groceries)           # ["bacon", "egg", "spam"]
s2 = sorted(groceries, key=len)  # ["egg", "spam", "bacon"]
rev = list(reversed(groceries))  # ["egg", "bacon", "spam"]
print(groceries)                 # ["spam", "bacon", "egg"]
```

``` py
groceries.sort()     # in-place
groceries.reverse()  # in-place
print(groceries)     # ["spam", "egg", "bacon"]
```

---

# 🥷 Chiavi di ordinamento

``` py
vals = sorted([2, 4, -1, -5], key=abs)  # [-1, 2, 4, -5]
```

- Funzione `itemgetter` in modulo `operator`
    - Parametri: uno o più indici interi
    - Risultato: funzione che estrae i valori corrispondenti
    - Utile per ordinare liste di tuple, liste di liste ecc.

``` py
from operator import itemgetter
records = [("Joe", 150), ("Rob", 310), ("Alb", 600), ("Din", 250)]
r1  = sorted(records, key=itemgetter(0))
# [("Alb", 600), ("Din", 250), ("Joe", 150), ("Rob", 310)]
r2 = sorted(records, key=itemgetter(1), reverse=True)
# [("Alb", 600), ("Rob", 310), ("Din", 250), ("Joe", 150)]
```

---

![](http://fondinfo.github.io/images/fun/legomap.png)
# 🥷 Map

- Parametri: funzione `f`, sequenza `l`
    - *(Funzione di ordine superiore)*
- `f` applicata a ogni valore in `l`
- Risultato: sequenza *lazy* dei risultati

``` py
vals = [-2, -1, 0, 1, 2]  # or, range(-2, 3)
for v in map(abs, vals):
    print(v, end="\t")
# 2    1    0    1    2
```

``` py
vals = [1, 2]
vals += map(int, "3,4,5".split(","))  # [1, 2, 3, 4, 5]
```

>

Più sequenze, se servono come parametri per `f`

---

# 🥷 Filter

- Parametri: *predicato* `p` (funzione booleana), sequenza `l`
- Risultato: sequenza *lazy* con i soli valori che rispettano `p`

``` py
def odd(x): return x % 2 == 1
def pos(x): return x > 0

vals = [4, 5, -6, 0, -7, 8]
for v in filter(odd, vals):
    print(v, end="\t")  # 5  -7
for v in filter(pos, vals):
    print(v, end="\t")  # 4  5  8
```

---

# 🥷 Istruzioni ed espressioni

- **Espressione**: codice la cui valutazione produce un valore
    - Adatta a parte destra di un assegnamento (*rvalue*)
- Molte **istruzioni** Python non corrispondono a un valore
    - `if`, `while`, `for`, `def`, `class` *non* sono espressioni
    - Assegnamenti `=`, `+=` ecc. *non* sono espressioni
- Esiste un `if` speciale, come espressione

``` py
val = "boom" if 5 % 2 == 0 else "bang"
```

- Da v3.8: *assegnamento* `:=` speciale, come espressione

``` py
while (v := float(input("val? "))) >= 0:  # sentinel
    print(v ** .5)
```

---

# 🥷 Valore di verità

- Ogni oggetto può essere convertito in `bool`
- Costanti e numeri *falsy*
    - `None`, `False`, `0`, `0.0` ecc.
- Sequenze *falsy*
    - `""`, `()`, `[]`, `{}`, `set()`, `range(0)`
- Altri oggetti, normalmente *truthy*
    - Decide metodo `__bool__`, o `__len__`

``` py
while v := input("val? "):  # sentinel, "" is falsy
    print(float(v) ** 2)
```

>

<https://docs.python.org/3/library/stdtypes.html#truth>

---

# 🥷 Funzioni di aggregazione

- Da sequenza a risultato singolo
- Operazioni logiche
    - **`all`** : *AND* logico su tutti i valori di *thrutiness*
    - **`any`** : *OR* logico su tutti i valori di *thrutiness*
- Operazioni numeriche
    - **`sum`, `max`, `min`, `len`**
    - Metodo **count** su sequenza: numero di occorrenze di un valore

``` py
>>> all((2, 1, 0, -1, ""))  # 0 and "" are falsy
False
>>> any([2, 1, 0, -1, ""])  # 2, 1 and -1 are truthy
True
>>> "abracadabra".count("a")
5
```

---

# 🥷 Valori casuali da sequenze

- **`choice`** : estrazione casuale da sequenza, probabilità uniforme

``` py
>>> from random import choice, sample, shuffle
>>> choice("aeiou")
"e"
```

- **`shuffle`** : mescolamento casuale di una lista (*in place*)

``` py
>>> vals = [2, 3, 5, 7, 11, 13]
>>> shuffle(vals)
>>> vals
[2, 11, 7, 3, 5, 13]
```

- **`sample`** : *n* estrazioni, da posizioni casuali non ripetute

``` py
>>> sample("aeiou", 3)  # a sequence and an int
["e", "o", "i"]  # result is a list
```

---

# 🏊 Esercizi

---

![](http://fondinfo.github.io/images/misc/histogram-rot.svg)
# Istogramma con barre orizzontali

- Chiedere all'utente una lista di valori positivi
    - Fino a inserimento del valore `0` (sentinella)
- Mostrare un istogramma
    - Lunghezza orizzontale di ciascuna barra proporzionale al valore corrispondente
    - La barra più lunga occupa tutto lo spazio disponibile in orizzontale

---

![](http://fondinfo.github.io/images/misc/dice.png)
# Risultati casuali

- Simulare `n` lanci di una coppia di dadi
    - `n` scelto dall'utente
- Contare quante volte si presenta ciascun risultato
    - Risultati possibili: da 2 a 12
    - Somma dei due dadi

>

Per conteggiare i vari risultati, usare una lista di (almeno) 11 valori

---

# Riempimento

- Definire funzione `fill` con due parametri
    - Lista di numeri interi
    - Indice intero $i$, una posizione nella lista
- Riempie con valori 1 le celle che contengono inizialmente 0, attorno all'indice dato
    - Elemento con indice $i$ ≠ 0: termina subito
    - Elemento con indice $i$ = 0: impostato a 1, riempimento a destra e sinistra
    - Arrivati a elemento ≠ 0: riempimento si blocca
- Es.: apice indica posizione $i$ nella lista: avvio del riempimento

``` txt
   0022000000002000
            ^
-> 0022111111112000
```

---

![](http://fondinfo.github.io/images/misc/merge-sign.png) ![](http://fondinfo.github.io/images/comp/merge.svg)
# Merge

- Definire una funzione `merge`
- Due parametri di tipo `list`
    - Entrambe le liste sono già ordinate (❗)
    - Entrambe le liste alla fine risulteranno vuote
- Risultato `list`
    - Risultato contiene tutti i valori delle due liste
    - I valori del risultato sono tutti in ordine
- Non usare `sort`, `sorted`; non ordinare la lista
    - Basta confrontare i valori in testa alle due liste
    - Quello più piccolo in assoluto è tra quei due
    - Rimuovere il valore scelto, dalla sua lista

---

![](https://fondinfo.github.io/images/misc/clamp.svg)
# Clamp di lista

- Definire la funzione `clamp` con tre parametri
    - Una lista di numeri
    - Un limite minimo $a$
    - Un limite massimo $b$
- Modifica numeri nella lista
    - Se minori di $a$, li sostituisce con $a$
    - Se maggiori di $b$ li sostituisce con $b$

``` py
data = [3, 4, 6, 7, 3, 5, 6, 12, 4]
clamp(data, 5, 10)
# data = [5, 5, 6, 7, 5, 5, 6, 10, 5]
```

---

![](https://fondinfo.github.io/images/misc/shuffle.svg)
# Shuffle

- Definire una funzione `shuffle`
    - Parametro: una lista di valori
    - Mescola *in-place* gli elementi della lista
- Per ogni indice $i$ della lista
    - Genera un indice $j$ casuale, valido
    - Scambia di posto elementi in $i$ e $j$

>

Naturalmente, *senza* usare la funzione `random.shuffle`

---

# Occorrenze

- Data una stringa contenente una sequenza di parole
    - Separate tra loro da uno spazio
- Contare le occorrenze di ogni parola della sequenza

>

Utilizzare un dizionario

---

# Parole comuni

- Date due stringhe `s1` e `s2` contenenti sequenze di parole
    - Separate tra loro da uno spazio
- Trovare l'insieme delle parole appartenenti a entrambe le stringhe
