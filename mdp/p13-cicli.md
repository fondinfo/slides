![](http://fondinfo.github.io/images/misc/red-squares.svg)
# Cicli
## Introduzione alla programmazione

---

# Cicli e stringhe

---

# 🧪 Confronto tra stringhe

- Confronto tra stringhe, in ordine *lessicografico*
    - `<, <=, >, >=, ==, !=`
    - Confronto deciso dal primo carattere diverso
- Primi 128 codici *Unicode* == *ASCII*
    - Prima le cifre, poi le maiuscole, infine le minuscole
- Operatore **`in`**: test di appartenenza (sottostringa)

``` py
>>> "art" < "arc"
False
>>> "arT" < "arc"
True
>>> "Py" in "Monthy Python"
True
>>> chr(83)
"S"
>>> ord("S")
83
```

---

# Tabella ASCII

![large](http://fondinfo.github.io/images/repr/ascii-large.svg)

---

![](http://fondinfo.github.io/images/misc/characters.png)
# Cicli su stringhe

- Il ciclo `for` scorre i valori di qualsiasi *sequenza*
- Una stringa è una *sequenza* di caratteri
- Ogni carattere è ancora di tipo `str`, lunghezza 1

``` py
for c in "Python":
    print(ord(c))
```

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

![](http://fondinfo.github.io/images/algo/words.svg)
# 🧪 Ordine tra due stringhe

- L'utente fornisce due stringhe → 3 alternative
    - Sono in ordine
    - Sono invertite
    - Sono uguali

``` py
a = input("First word? ")
b = input("Second word? ")

if a < b:
    print("The words are ordered")
elif a > b:
    print("The words are inverted")
else:
    print("The words are equal")
```

---

![](http://fondinfo.github.io/images/algo/words.svg)
# 🧪 Senza elif

- Se la prima stringa non precede la seconda…
    - C'è un'altra condizione, `if` annidato
    - Codice più complicato, meno leggibile
    - Molte condizioni → annidamento crescente

``` py
a = input("First word? ")
b = input("Second word? ")

if a < b:
    print("The words are ordered")
else:
    if a > b:
        print("The words are inverted")
    else:
        print("The words are equal")
```

---

![](http://fondinfo.github.io/images/algo/calc.svg)
# 🧪 Operazioni aritmetiche

``` py
a = float(input())
b = float(input())
op = input()

if op == "+":
    print(a + b)
elif op == "-":
    print(a - b)
elif op == "*":
    print(a * b)
elif op == "/" and b != 0:
    print(a / b)
else:
    print("Operation not allowed")
```

---

# Controllo di stampa

- Caratteri speciali in stringhe
    - `\n` : ritorno a capo (codice 10 dec)
    - `\t` : tabulazione orizzontale (codice 9 dec)

``` py
>>> print("one\ttwo\tthree\nfour\tfive\tsix")
one     two     three
four    five    six
```

- Parametri opzionali per `print`
    - `end` : sequenza finale, default `\n`
    - `sep` : separatore tra parametri, default *spazio*

``` py
>>> for i in range(3):
        print(1, 2, 3, sep=".", end=";")
1.2.3;1.2.3;1.2.3;
```

---

# Stringhe formattate

- Concatenazione di stringhe : op. `+`
    - Complesso comporre stringhe con molti dati
- Alternativa : *stringhe formattate*, o *f-string*
    - `f` prima di virgolette
    - Espressioni in stringa, tra graffe
    - Sostituite da loro rappresentazione testuale

``` py
radius = 2.5
area = math.pi * radius**2
# msg = ("The circle with radius " + str(radius) +
#        " has area " + str(area) + ".")
msg = f"The circle with radius {radius} has area {area}."
print(msg)
```

---

# Cicli e linearità

---

![](http://fondinfo.github.io/images/algo/linearity.svg)
# 💡 Linearità

- In un ciclo `for i in range(n)…`
- Legame lineare tra una grandezza $v$ e $i$

$$v = m \cdot i + q$$

- Se noti il primo e l'ultimo valore: $v_{first}, v_{last}$
    - `$\begin{cases}v_{first} = m \cdot 0 + q, (i = 0) \\ v_{last} = m \cdot (n-1) + q, (i = n-1)\end{cases}$`
    - `$\implies \begin{cases}q = v_{first} \\ m = \frac{v_{last} - v_{first}}{n-1}\end{cases}$`
- Visto che $i$ è intero, $m$ è la differenza tra due istanze
    - P.es. se $v$ è la posizione di quadrati disegnati in sequenza
    - ⇒ $m$ è la distanza tra due quadrati successivi

---

![](http://fondinfo.github.io/images/misc/red-squares.svg)
# 🧪 Sequenza di n quadrati

- Disegnare una sequenza di $n$ quadrati
    - $L$: lato canvas noto, $l$: lato quadrati noto
    - ⇒ Posizioni primo e ultimo quadrato: $v_{first} = 0, v_{last} = L - l$

``` py
pos_fst, pos_lst = 0, L - l
pos_m = (pos_lst - pos_fst) / max(n - 1, 1)  # ⚠️ div by 0
for i in range(n):
    pos = pos_m * i + pos_fst
    g2d.draw_rect((pos, pos), (l, l))
```

- ❓ Colore da nero fino a rosso
- ❓ Margine di $10$ pixel attorno a disegno

>

<https://fondinfo.github.io/play/?c03_squares.py>

---

![](http://fondinfo.github.io/images/fun/times-table.svg)
# Cicli e annidamento

- Stampare la tavola pitagorica
- Primo passo: stampare una sola riga

``` py
y = int(input("Insert a value: "))
for x in range(1, 11):
    print(x * y, end="\t")  # keep printing on the same line
print()  # print just a `newline`
```

- Poi, ripetere tutto per le 10 righe

``` py
for y in range(1, 11):
    for x in range(1, 11):
        print(x * y, end="\t")
    print()
```

>

<https://fondinfo.github.io/play/?c03_tables.py>

---

![](http://fondinfo.github.io/images/misc/color-grid.svg) ![](http://fondinfo.github.io/images/repr/raster-tile.svg)
# Griglia di colori

- Mostrare una griglia `rows×cols` di rettangoli
    - In orizzontale, blu cresce da 0 a 255
    - In verticale, verde cresce da 0 a 255
- Due cicli annidati, come tabelline
    - Valori lineari rispetto a `x` o `y`

``` py
w, h = CANVAS_W / max(cols, 1), CANVAS_H / max(rows, 1)
g, b = 255 / max(rows - 1, 1), 255 / max(cols - 1, 1)
for y in range(rows):
    for x in range(cols):
        g2d.set_color((0, g * y, b * x))
        g2d.draw_rect((w * x, h * y), (w, h))
```

>

<https://fondinfo.github.io/play/?c03_grid.py>

---

# Cicli con sentinella

---

![](http://fondinfo.github.io/images/misc/rock-cubes.png)
# Sentinella

- Acquisire valori di input, in ciclo
    - Ciascun valore viene elaborato
- Finché valori diversi dal valore *sentinella*
    - Il valore *sentinella* non deve essere elaborato
    - Qui è `-1`, ma importa che si distingua da dati

``` py
v = int(input("Value (-1 to end)? "))
while v != -1:
    print(v ** 3)  # <-- in general, process v here
    v = int(input("Value (-1 to end)? "))
```

- Codice di input presente due volte
    - Prima di cominciare il ciclo
    - Dopo aver elaborato il valore corrente

---

# Cicli for e while

- Si usa `for` per tutte le sequenze e gli iterabili
    - `range, tuple, str, list`… Più semplice e chiaro!
- Si usa `while` con sentinella o in casi più particolari
- Es. conteggio da `0` a `n-1`
    - `while`: contatore inizializzato e incrementato a mano

``` py
n = int(input("n? "))
for count in range(n):
    print(count)
```

``` py
n = int(input("n? "))
count = 0
while count < n:
    print(count)
    count += 1
```

---

# Sentinella con conteggio

``` py
count = 0
v = int(input("Value (-1 to end)? "))
while v != -1:
    count += 1
    print(v ** 3)  # <-- process here v as needed
    v = int(input("Value (-1 to end)? "))
print("Number of processed values:", count)
```

---

![](http://fondinfo.github.io/images/algo/sentinel.svg)
# Totale parziale

- Sommare tutti i valori in input, fino a sentinella
- Variabile per totale parziale
    - Acquisito nuovo valore → aggiunto al totale
- Come quando aggiorniamo il costo di un *carrello*

``` py
total = 0
v = int(input("Value (-1 to end)? "))
while v != -1:  # -1 is the sentinel
    total += v
    v = int(input("Value (-1 to end)? "))
print("Sum of all values:", total)
```

- ❓ Contare i valori e calcolare la media

>

<https://fondinfo.github.io/play/?c03_sentinel.py>

---

![](http://fondinfo.github.io/images/algo/sum1n.svg)
# 🧪 Somma di Gauss

- Sommare tutti i naturali da $1$ a $n$, dato
- *Totale parziale*, ma meglio `for` su `range` dato
- Verificare risultato con la formula di Gauss

`$$\sum_{k=1}^n k = \frac{n(n+1)}{2}$$`

``` py
n = int(input("n? "))
total = 0
for i in range(1, n + 1):
    total += i
```

>

<https://it.wikipedia.org/wiki/Carl_Friedrich_Gauss#Biografia>
<br>
<https://fondinfo.github.io/play/?c03_gauss.py>

---

# Ricerca del massimo

- Trovare il massimo in una sequenza di valori
- Variabile per massimo temporaneo
    - Valore iniziale: `-math.inf` (`$-\infty$`)
    - Aggiornata ogni volta che si trova un valore migliore

``` py
from math import inf
largest = -inf  # -∞
for v in [3, 7, 5, 6]:
    if v > largest:
        largest = v
print(largest)
```

💡 Le funzioni `max` e `min` accettano come parametro una sequenza
<br><br>
❓ Come adattare al ciclo con sentinella?

---

# Acquisizione in lista

- Acquisire valori in numero non noto
- *Sentinella* per terminare: p.es. riga vuota

``` py
values = []  # list of floats
val = input("Val? (empty line to finish) ")

while val != "":
    values.append(float(val))  # float values
    val = input("Val? (empty line to finish) ")
```

- Evitare di memorizzare tutti i dati, quando possibile
    - Efficienza, scalabilità a *Big Data*
    - Esempio: calcolo della media, senza lista

---

# 🏊 Esercizi

---

# Somma di potenze di 2

- Chiedere all'utente un numero $n$
- Sommare le prime $n$ potenze di 2
    - $2^0 + 2^1 + ... + 2^{n-1}$
- Tenere il conto di un *totale parziale*
- Verificare risultato con questa formula (sempre di Gauss)

`$$\sum_{k=0}^{n-1} 2^k = 2^n - 1$$`

>

Preferibile `for` o `while`?

---

![](http://fondinfo.github.io/images/misc/blue-row.svg)
# Cerchi in riga

- Chiedere all'utente un numero $n$
- In un canvas $L\times L$, con $L=500$ predefinito
- Disegnare una fila orizzontale di $n$ cerchi
    - Tutti di uguale dimensione
    - Coprono tutta la larghezza del canvas
- Il colore varia gradualmente dal nero fino al blu saturo
    - Da sinistra verso destra

---

![](http://fondinfo.github.io/images/misc/red-circles.svg)
# Cerchi concentrici

- Chiedere all'utente un numero $n$
- In un canvas $L\times L$, con $L=500$ predefinito
- Disegnare $n$ cerchi al centro del canvas
    - Diametro decrescente, da $L$ fino a $\frac{L}{n}$
    - Colore da rosso (cerchio esterno) a nero

---

![](http://fondinfo.github.io/images/misc/red-squares.svg)
# Quadrati in diagonale

- Chiedere all'utente un numero `n`
- In un canvas $L\times L$, con $L=500$ predefinito
- Disegnare sulla diagonale $n$ quadrati
    - Tutti di uguale dimensione
    - Coprono tutta la diagonale del canvas
- Quadrati sovrapposti per metà del loro lato $l$
   - $l$ non predefinito, dipende da $n$

>

Rivedere esempio simile: analisi ancora valida ma bisogna calcolare $l$
<br>
In $L$ ci dovranno stare esattamente $n+1$ semilati ($l/2$)

---

# Distanza dagli angoli

- Chiedere all'utente due numeri $w$ e $h$ (num. colonne e righe)
- Mostrare due tabelle, ∀ cella $(x, y)$ calcolare distanza di Manhattan
    1. Rispetto all'angolo in alto a sinistra $(x_0, y_0) = (0, 0)$
    2. Rispetto all'angolo in basso a sinistra: $(x_0, y_0) = (0, h - 1)$

``` txt
0 1 2 3
1 2 3 4
2 3 4 5
3 4 5 6

3 4 5 6
2 3 4 5
1 2 3 4
0 1 2 3
```

>

Distanza di Manhattan: di quante celle bisogna spostarsi in orizzontale e verticale, $|\Delta x| + |\Delta y|$

---

![](http://fondinfo.github.io/images/misc/resistors.png)
`$R_s = \Sigma R_i$` <br>
`$\frac{1}{R_p} = \Sigma \frac{1}{R_i}$`

# Resistenze con sentinella

- Leggere, attraverso un ciclo, una sequenza di valori di resistenze elettriche
- La sequenza termina quando l'utente immette il valore 0
- Alla fine, visualizzare la resistenza equivalente, sia nel caso di resistenze disposte in serie, che in parallelo

---

![](http://fondinfo.github.io/images/misc/bingo-balls.png)
# Numero segreto

- Generare all'inizio del programma un numero “segreto” a caso tra 1 e 90
- Chiedere ripetutamente all'utente di immettere un numero, finché non indovina quello generato
- A ogni tentativo, dire se il numero immesso è maggiore o minore del numero segreto

---

![](http://fondinfo.github.io/images/misc/monster.png)
# La stanza del mostro

- Il giocatore si muove su una scacchiera di 5x5 celle, partendo da un angolo
    - Le righe e le colonne sono numerate da 0 a 4
- Un tesoro e un mostro sono nascosti in due posizioni casuali *diverse*, all'inizio del gioco
    - Non si sovrappongono tra loro, nè con l'angolo del giocatore
- A ogni turno:
    - Chiedere al giocatore una direzione (`w/a/s/d`)
    - Se capita sulla cella del tesoro, ha vinto
    - Se capita sulla cella del mostro, ha perso

>

Basta memorizzare tre coppie di coordinate cartesiane
<br>
Non è richiesto l'uso della grafica

---

![](http://fondinfo.github.io/images/games/climbing.svg)
# Free climbing

- Gara tra due arrampicatori, in forma testuale
- Ripetutamente, generare due numeri casuali
    - Ciascun numero $∈ [-1, 3]$
    - Balzo in alto (o piccola discesa) di ciascun concorrente
    - Il livello di un concorrente non diventa mai $< 0$
- Vince chi arriva prima in cima (una costante `TOP`)
