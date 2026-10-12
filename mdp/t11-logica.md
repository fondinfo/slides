![](http://fondinfo.github.io/images/fun/hanoi-tower.png)
# Logica matematica
## Introduzione all'informatica <br> Michele Tomaiuolo @ Ingegneria UniPR

---

![](http://fondinfo.github.io/images/repr/hair-logic.svg)
# Algebra di Boole

---

![](http://fondinfo.github.io/images/hist/boole.jpg) George Boole, 1815-1864
# 💡️ Algebra di Boole

- L’algebra di Boole è un formalismo che opera su variabili (dette *variabili booleane*)
- Le variabili booleane possono assumere due soli valori
    - `Vero`: 1
    - `Falso`: 0
- Sulle variabili booleane è possibile definire delle funzioni (dette *funzioni booleane*)
- Anche le funzioni booleane possono assumere solo i due valori `vero` e `falso`

---

`$A$` | `$B$` | `$C$` | `$F_1$`
--|---|---|--
0 | 0 | 0 | 1
0 | 0 | 1 | 0
0 | 1 | 0 | 0
0 | 1 | 1 | 1
1 | 0 | 0 | 0
1 | 0 | 1 | 1
1 | 1 | 0 | 1
1 | 1 | 1 | 1

# 💡️ Funzione e tabella di verità

- *Tabella di verità* per definire una *funzione booleana*
- Valore risultante per ciascuna configurazione dei valori in ingresso

>

A volte, *specifica incompleta*: certe configurazioni di ingressi non possono verificarsi, perciò non è specificato alcun valore

---

# 💡️ Operatori logici

- Algebra di Boole: basata su un insieme di operatori

Operatore | Simbolo   | Simbolo alternativo
----------|-----------|---
**And**   | `$\land$` | `$\cdot$`
**Or**    | `$\lor$`  | `$+$`
**Not**   | `$\lnot$` | Sovralinea

- Semplici funzioni, specificate con tabelle di verità

`$A$` | `$B$` | `$A \land B$` | `$A \lor B$` | `$\lnot A$`
------|-------|---------------|--------------|------------
0     | 0     | 0             | 0            | 1
0     | 1     | 0             | 1            | 1
1     | 0     | 0             | 1            | 0
1     | 1     | 1             | 1            | 0

---

# 💡️ Altri operatori comuni

Operatore | Simbolo | Simbolo alternativo
----------|---------|---
Xor       | `$⊕$`     |
Nand      | `$\uparrow$`     | `$\bar\land$`
Nor       | `$\downarrow$`   | `$\bar\lor$`

`$A$` | `$B$` | `$A \oplus B$` | `$A \uparrow B$` | `$A \downarrow B$`
------|-------|----------------|------------------|-------------------
0     | 0     | 0              | 1                | 1
0     | 1     | 1              | 1                | 0
1     | 0     | 1              | 1                | 0
1     | 1     | 0              | 0                | 0

- Operatori possono essere combinati in *espressioni*
    - Altra forma di definizione di funzioni booleane
    - Es. `$F_2(A, B, C) = A \cdot B + C$`

---

# ⭐ Proprietà degli operatori

- Dimostrazione: si confrontano le due tabelle di verità

Proprietà    | Not
-------------|--------
Complemento  | `$\lnot \lnot A \equiv A$`

Proprietà    | And                                                | Or
-------------|----------------------------------------------------|--------------------------
Commutativa  | `$A \cdot B \equiv B \cdot A$`                     | `$A + B \equiv B + A$`
Associativa  | `$(A \cdot B) \cdot C \equiv A \cdot (B \cdot C)$` | `$(A+B)+C \equiv A+(B+C)$`
Distributiva | `$A+(B \cdot C) \equiv (A+B) \cdot (A+C)$`         | `$A \cdot (B+C) \equiv (A \cdot B)+(A \cdot C)$`
Idempotenza  | `$A \cdot A \equiv A$`                             | `$A + A \equiv A$`
Identità     | `$A \cdot 1 \equiv A$`                             | `$A + 0 \equiv A$`
Del limite   | `$A \cdot 0 \equiv 0$`                             | `$A + 1 \equiv 1$`
Assorbimento | `$A \cdot (A+B) \equiv A$`                         | `$A + (A \cdot B) \equiv A$`
Inverso      | `$A \cdot \lnot A \equiv 0$`                       | `$A + \lnot A \equiv 1$`
De Morgan    | `$\lnot (A \cdot B \cdot C \dots) \equiv \lnot A + \lnot B + \lnot C \dots$` | `$\lnot (A+B+C \dots) \equiv \lnot A \cdot \lnot B \cdot \lnot C \dots$`

---

# 🔬 Dimostrazioni

- De Morgan per And: `$\lnot (A \cdot B) \equiv \lnot A+ \lnot B$`

$A$ | $B$ | $\lnot A$ | $\lnot B$ | $A \cdot B$ | $\lnot (A \cdot B)$ | $\lnot A + \lnot B$
----|-----|-----------|-----------|-------------|---------------------|--------------------
0   | 0   | 1         | 1         | 0           | 1                   | 1
0   | 1   | 1         | 0         | 0           | 1                   | 1
1   | 0   | 0         | 1         | 0           | 1                   | 1
1   | 1   | 0         | 0         | 1           | 0                   | 0

- De Morgan per Or: `$\lnot (A+B) \equiv \lnot A \cdot \lnot B$`

$A$ | $B$ | $\lnot A$ | $\lnot B$ | $A + B$ | $\lnot (A+B)$ | $\lnot A \cdot \lnot B$
----|-----|-----------|-----------|---------|---------------|------------------------
0   | 0   | 1         | 1         | 0       | 1             | 1
0   | 1   | 1         | 0         | 1       | 0             | 0
1   | 0   | 0         | 1         | 1       | 0             | 0
1   | 1   | 0         | 0         | 1       | 0             | 0

---

# ⭐ De Morgan

- ⚠️ Attenzione a De Morgan: errore comune!

``` py
if x1 == x2 and y1 == y2:
    print("the points are equal")
```

``` py
if x1 != x2 or y1 != y2:  # not (x1 == x2 and y1 == y2)
    print("the points are different")
```

- Python permette di confrontare tuple

``` py
pt1 = x1, y1
pt2 = x2, y2
if pt1 != pt2:
    print("the points are different")
```

---

| `a`     | `a == True` || `not a` | `a == False`
|---------|-------------||---------|---
| `True`  | `True`      || `False` | `False`
| `False` | `False`     || `True`  | `True`

# 🤢️ Booleani e code smell

- ⚠️ Confrontare var booleana `a` e `True`?
    - `a` ha già lo stesso valore del confronto!

``` py
if a: …  # instead of “if a == True: …”
```

``` py
if not a: …  # instead of “if a == False: …”
```

- ⚠️ Attenzione ai risultati booleani prodotti con `if`

``` py
if radius > 50:
    big_enough = True
else:
    big_enough = False  # Too verbose and convoluted!
```

``` py
big_enough = radius > 50  # rhs expression holds the value, already
```

---

| `$A$` | `$B$` | `$C$` | `$F$` | |
|---|---|---|---|-------------------|
| 0 | 0 | 0 | 1 | → *SP* |
| 0 | 0 | 1 | 0 |        |
| 0 | 1 | 0 | 0 |        |
| 0 | 1 | 1 | 1 | → *SP* |
| 1 | 0 | 0 | 0 |        |
| 1 | 0 | 1 | 1 | → *SP* |
| 1 | 1 | 0 | 1 | → *SP* |
| 1 | 1 | 1 | 1 | → *SP* |

# ⭐ Forma canonica SP

- **Somma di Prodotti**: prendere le righe a 1
    - `$F(A, B, C) := ( \lnot A \cdot  \lnot B \cdot  \lnot C) + \\ ( \lnot A \cdot B \cdot C) + (A \cdot  \lnot B \cdot C) + \\ (A \cdot B \cdot  \lnot C) + (A \cdot B \cdot C)$`
- *Principio*: quali input rendono `F` vera?

---

| `$A$` | `$B$` | `$C$` | `$F$` | `$\lnot F$` | |
|---|---|---|---|----|---|
| 0 | 0 | 0 | 1 | 0  | |
| 0 | 0 | 1 | 0 | 1  | → *PS* |
| 0 | 1 | 0 | 0 | 1  | → *PS* |
| 0 | 1 | 1 | 1 | 0  | |
| 1 | 0 | 0 | 0 | 1  | → *PS* |
| 1 | 0 | 1 | 1 | 0  | |
| 1 | 1 | 0 | 1 | 0  | |
| 1 | 1 | 1 | 1 | 0  | |

# ⭐ Forma canonica PS

- **Prodotto di Somme**: prendere le righe a 0, *negate*
    - `$F(A, B, C) := (A+B+ \lnot C) \cdot \\ (A+ \lnot B+C) \cdot ( \lnot A+B+C)$`
- *Principio*: quali input rendono `$\lnot F$` vera?
    - `$\lnot F(A, B, C) := ( \lnot A \cdot  \lnot B \cdot C) + \\ ( \lnot A \cdot B \cdot  \lnot C) + (A \cdot  \lnot B \cdot  \lnot C)$`
    - `$F(A, B, C) := \lnot (( \lnot A \cdot  \lnot B \cdot C) + \\ ( \lnot A \cdot B \cdot  \lnot C) + (A \cdot  \lnot B \cdot  \lnot C))$`
    - ... De Morgan due volte e si ottiene *PS*

---


# Logica delle proposizioni

---

# 💡️ Proposizione

- Frase dichiarativa (*enunciato*) di senso compiuto che possa esser riconosciuta come “vera” o “falsa”
    - **Principio di non contraddizione**: un enunciato non può essere contemporaneamente vero e falso
    - **Principio del terzo escluso**: un enunciato è vero o falso, non esiste una terza possibilità (*tertium non datur*)
- Ad esempio, sono proposizioni:
    - “Il cane è un animale” - “2 = 1” - “I triangoli hanno tre lati”
- ... Mentre non lo sono:
    - “Il cane” - “Che ora è?” - “Se 2 = 1” - “Non fumare!” - “Io sto mentendo” (*)

>

(*) Paradosso: non si può stabilire se la frase è vera o falsa

---

![](http://fondinfo.github.io/images/repr/logical-problem.png)
# 💡️ Connettivi logici

- In logica, operatori booleani per *legare* proposizioni in forma più complessa
    - “e” (*congiunzione*, `$\land$`)
    - “o” (*disgiunzione*, `$\lor$`)
    - “non” (*negazione*, `$\lnot$`)
    - Valgono le proprietà già viste
- Esempio di formalizzazione
    - `$P_1 :=$` “Gold is in Chest1” <br> `$P_2 :=$` “Gold is in Chest2” <br> `$P_3 :=$` “Gold is in Chest3”
    - `$\lnot P_2 \land (P_1 \lor P_3) \land \lnot P_3 \equiv$` *(proprietà distributiva)* <br>
       `$\lnot P_2 \land (P_1 \land \lnot P_3 \lor P_3 \land \lnot P_3) \equiv$` *(proprietà dell'inverso)* <br>
       `$P_1 \land \lnot P_2 \land \lnot P_3$`

---

`$P$` | `$Q$` | `$P \implies Q$`
------|-------|---------
 F    |  F    |  T
 F    |  T    |  T
 T    |  F    |  F
 T    |  T    |  T

# 💡️ Implicazione logica

- **Connettivo condizionale**: esprime il legame “se ... allora”
    - `$P :=$` “io penso” (*premessa*, o *antecedente*)
    - `$Q :=$` “io esisto” (*conclusione*, o *conseguente*)
    - `$P \implies Q$`: “se penso allora esisto”
- `$P \implies Q$` si può leggere anche nei seguenti modi:
    - Da `$P$` segue `$Q$`
    - `$P$` è *condizione sufficiente* per `$Q$` (se `$P$` vera, allora `$Q$` vera)
    - `$Q$` è *condizione necessaria* per `$P$` (se `$Q$` falsa, allora `$P$` falsa)
- Esempi di implicazioni vere:
    - “Se 5 è un numero allora Roma è una città”
    - “Se Parigi è la capitale d'Italia, allora 5 + 5 = 10”

---

# 🧪 Verità dell'implicazione

`$P$` | `$Q$` | `$P \implies Q$` | `$Q \implies P$` | `$\lnot P \lor Q$`
------|-------|------------------|------------------|---
 F    |  F    |  T               | T                | T
 F    |  T    |  T               | F                | T
 T    |  F    |  F               | T                | F
 T    |  T    |  T               | T                | T

- `$P \implies Q$` è falsa solo in un caso: `$P$` vera e `$Q$` falsa
    - `$\lnot (P \implies Q) \equiv (P \land \lnot Q)$`
    - `$P \implies Q \equiv \lnot (P \land \lnot Q) \equiv$` *[De Morgan]* <br> `$\lnot P \lor \lnot ( \lnot Q) \equiv $` *[Doppia negazione]* <br> `$\lnot P \lor Q$` (implicazione vera quando: `$P$` falsa, o `$Q$` vera)
- L'implicazione **non** soddisfa la proprietà *commutativa*:
    - `$(P \implies Q) \neq (Q \implies P)$`

---

# 🧪 Doppia implicazione

- **Equivalenza logica**: si legge “P se e solo se Q”, <br> “P condizione necessaria e sufficiente per Q”

`$P$` | `$Q$` | `$P \implies Q$` | `$Q \implies P$` | `$P \iff Q$` | `$(P \land Q) \lor ( \lnot P \land \lnot Q)$`
----|-----|---------|---------|---------|------------------
 F  |  F  |  T      |  T      |  T      |  T
 F  |  T  |  T      |  F      |  F      |  F
 T  |  F  |  F      |  T      |  F      |  F
 T  |  T  |  T      |  T      |  T      |  T

- `$P \iff Q$`: valgono entrambe le implicazioni, `$(P \implies Q) \land (Q \implies P)$`
    - `$P \iff Q$` vera: `$P$` e `$Q$` entrambe vere, o entrambe false
    - Da proprietà distributiva e proprietà dell'inverso
    - `$(P \implies Q) \land (Q \implies P) \equiv ( \lnot P \lor Q) \land ( \lnot Q \lor P) \equiv \\ ( \lnot P \land \lnot Q) \lor ( \lnot P \land P) \lor ( \lnot Q \land Q) \lor (P \land Q) \equiv \\ (P \land Q) \lor ( \lnot P \land \lnot Q)$`

---

# 💡️ Deduzione logica

- Un *teorema* si riconduce all’implicazione `$P \implies Q$`
    - `$P$` (*ipotesi*): proposizione che si assume vera
    - `$Q$` (*tesi*): proposizione di cui si vuole dedurre la verità
- Processo di *deduzione logica*, o *dimostrazione*, deve seguire ben precisi schemi di ragionamento
    - Dimostrazione diretta (*modus ponens*)
    - Dimostrazione per assurdo (*modus tollens*)

---

# ⭐ Dimostrazione diretta

- *Modus ponens*: schema di ragionamento

Premesse | Conclusione
---------|------------
`$(P \implies Q)$` vera <br> `$P$` vera | `$Q$` vera

- `$P = T, P \implies Q = \lnot P \lor Q = F \lor Q = Q = T$`
- Esempio
    - Se c'è sole, Ugo arriva in bici (implicazione, *regola d'inferenza*)
    - C'è sole (*fatto*)
    - Ugo arriva in bici (*deduzione*)
- **Osservazione**: il solo fatto di sapere che `$P \implies Q$` è vera non consente di concludere niente su `$P$` e `$Q$`

---

# 🧪 Passaggi intermedi

- Sono possibili dimostrazioni con più passaggi intermedi
- Se vere le implicazioni `$P \implies R, R \implies Q$`... <br> e se `$P$` vera… <br> allora vera anche `$Q$`
- `$((P \implies R) \land (R \implies Q) \land P) \implies Q$`
- Schema di ragionamento

Premesse | Conclusione
---------|------------
`$(P \implies R)$` vera <br> `$(R \implies Q)$` vera <br> `$P$` vera | `$Q$` vera

---

# 🧪 Implicazione equivalente

`$P$` | `$Q$` | `$P \implies Q$` | `$\lnot Q$` | `$\lnot P$` | `$\lnot Q \implies \lnot P$`
----|-----|---------|------|------|----------
 F  |  F  |  T      |  T   |  T   |  T
 F  |  T  |  T      |  F   |  T   |  T
 T  |  F  |  F      |  T   |  F   |  F
 T  |  T  |  T      |  F   |  F   |  T

- Queste due implicazioni sono equivalenti
    - `$P \implies Q$`
    - `$\lnot Q \implies \lnot P$`
    - Infatti, `$\lnot P \lor Q \equiv \lnot ( \lnot Q) \lor \lnot P$`
- Nelle dimostrazioni, possiamo usare la seconda implicazione al posto della prima

---

# ⭐ Dimostrazione per assurdo

- Se è vera l’implicazione `$( \lnot Q \implies \lnot P)$` ed è vera `$P$`, allora è vera anche `$Q$`
- *Modus tollens*: schema di ragionamento

| Premesse | Conclusione |
|----------|-------------|
| `$( \lnot Q \implies \lnot P)$` vera <br> `$P$` vera | `$Q$` vera |

- Esempio di teorema
    - `$P := m \cdot n ≠ 0$`
    - `$Q := (m ≠ 0) \land (n ≠ 0)$`
    - Dimostrazione per assurdo: `$\lnot Q \implies \lnot P$`
    - Se `$(m = 0) \lor (n = 0)$`, allora `$m \cdot n = 0$`

---


# Logica dei predicati

---

# 💡️ Predicato, o enunciato aperto

- Frase che contiene *variabili*
    - La verità della frase dipende dal valore delle variabili
    - Se variabili sostituite da valori, diventa proposizione
- Esempio
    - `$P(x) :=$` “x è un numero dispari”
- Occorre definire il *dominio* delle variabili
- *Insieme di verità* del predicato
    - Valori delle variabili che rendono vero l'enunciato
    - Sottoinsieme del dominio delle variabili

---

# 💡️ Predicati con connettivi

- `$P(x) \land Q(x)$` – Vero per gli `$x$` che rendono veri sia `$P$` che `$Q$`
- `$P(x) \lor Q(x)$` – Vero per gli `$x$` che rendono vero almeno uno tra i predicati `$P$` e `$Q$`
- `$\lnot P(x)$` – Vero per gli `$x$` che rendono falso `$P$`
- `$P(x) \implies Q(x)$` – Vero per gli `$x$` che rendono falso `$P$` oppure vero `$Q$`
- `$P(x) \iff Q(x)$` – Vero per gli `$x$` che rendono `$P$` e `$Q$` entrambi falsi o entrambi veri

---

# ⭐ Quantificatori

- Un predicato può essere trasformato in una proposizione in due modi
    - Sostituendo le variabili con valori
    - Oppure, *quantificando* le sue variabili
- Una variabile legata a un quantificatore si dice *vincolata*, altrimenti *libera*
- I quantificatori logici sono due
    - Quantificatore **universale**
    - Quantificatore **esistenziale**

---

# 🧪 Quantificatore universale

- Afferma che una data proprietà valga per *tutti i valori* nel dominio della variabile vincolata
- `$\forall x, P(x)$` – “Per ogni x, P(x) è vero”
- Esempi
    - `$\forall n \in N, n \bmod 4 = 0 \implies even(n)$` – Tutti i multipli di 4 sono pari
    - `$\forall x \in R, \forall y \in R, (x + y)^2 = x^2 + 2xy + y^2$`

---

# 🧪 Quantificatore esistenziale

- Afferma che una data proprietà valga per *almeno un valore* della variabile vincolata
- `$\exists x : P(x)$` -- “Esiste almeno un x tale che P(x) è vero”
- Esempi
    - `$\exists n \in N : even(n)$` -- Esiste almeno un numero pari
    - `$\exists x \in R : 2x + 1 = 0$` -- L'equazione ammette almeno una soluzione
- Enunciati con `$\nexists$` riformulati con `$\forall$` e negando il predicato
    - `$\nexists x : x^2 < 0$`
    - `$\forall x, x^2 ≥ 0$`

---

# 🔬 Proprietà dei quantificatori

- I quantificatori sono sostanzialmente *congiunzioni* o *disgiunzioni* allargate a tutti gli elementi di un dominio
    - Per semplicità, dominio `$D := \{1, 2, 3\}$`
    - `$\forall x \in D, P(x) \equiv P(1) \land P(2) \land P(3)$`
    - `$\exists x \in D : P(x) \equiv P(1) \lor P(2) \lor P(3)$`
- Due quantificatori dello stesso tipo *possono* essere scambiati di posto senza alterare la verità dell’enunciato
- Invece, due quantificatori di diverso tipo *non possono* essere scambiati di posto
- I seguenti enunciati sono ben diversi
    - `$\forall x \in R, \exists y \in R : y \geq x$`
    - `$\exists y \in R : \forall x \in R, y \geq x$`

---

# ⭐ Negazione con quantificatori

- Per negare un enunciato che contiene quantificatori, occorrono due modifiche:
    - **①** Sostituire tutti i `$\forall$` con `$\exists$`, e viceversa
    - **②** Negare il predicato
- Proprietà analoga a *De Morgan*
    - Infatti i quantificatori sono sostanzialmente `$\land$` o `$\lor$` allargati
- Esempi
    - `$\lnot (\forall x, P(x)) \iff \exists x : \lnot P(x)$`
    - `$\lnot (\exists x : P(x)) \iff \forall x, \lnot P(x)$`

---

![](http://fondinfo.github.io/images/hist/plato-aristotle.jpg) Platone e Aristotele <br> ~350 a.C.
# 🧪 Sillogismi aristotelici

- Modus ponens con quantificatori
    - *Premessa maggiore*: “Tutti gli uomini sono mortali” <br> `$\forall x, uomo(x) \implies mortale(x)$`
    - *Premessa minore*: “Socrate è un uomo” <br> `$uomo(Socrate)$`
    - *Conclusione*: “Socrate è mortale” <br> `$mortale(Socrate)$`
- Il quantificatore si può eliminare sostituendo alla variabile un valore del dominio
    - `$uomo(Socrate) \implies mortale(Socrate)$`
- Poi si applica il modus ponens

---

# 🧪 Operazioni tra insiemi

- Siano definiti due insiemi di verità
    - `$A = \{x : P(x)\}, B = \{x : Q(x)\}$`
- *Unione*
    - `$A \cup B = \{x : x \in A \lor x \in B\} = \{x : P(x) \lor Q(x)\}$`
- *Intersezione*
    - `$A \cap B = \{x : x \in A \land x \in B\} = \{x : P(x) \land Q(x)\}$`
- *Complemento*
    - `$A' = \{x : x \notin A\} = \{x : \lnot P(x)\}$`

---

# 🧪 Proprietà degli insiemi

- Sugli stessi insiemi: `A` e `B`

Proprietà | Op. tra insiemi | Op. tra predicati
----------|-----------------|------------------
Commutativa | `$A \cup B = B \cup A$` | `$P \lor Q \equiv Q \lor P$`
Commutativa | `$A \cap B = B \cap A$` | `$P \land Q \equiv Q \land P$`
Associativa | `$(A \cup B) \cup C = A \cup (B \cup C)$` | `$(P \lor Q) \lor R \equiv P \lor (Q \lor R)$`
Associativa | `$(A \cap B) \cap C = A \cap (B \cap C)$` | `$(P \land Q) \land R \equiv P \land (Q \land R)$`
Distributiva | `$(A \cup B) \cap C = (A \cap C) \cup (B \cap C)$` | `$(P \lor Q) \land R \equiv (P \land R) \lor (Q \land R)$`
Distributiva | `$(A \cap B) \cup C = (A \cup C) \cap (B \cup C)$` | `$(P \land Q) \lor R \equiv (P \lor R) \land (Q \lor R)$`
Doppia neg. | `$(B')' = B$` | `$\lnot ( \lnot P) \equiv P$`
De Morgan | `$(A \cup B)' = A' \cap B'$` | `$\lnot (P \lor Q) \equiv \lnot P \land \lnot Q$`
De Morgan | `$(A \cap B)' = A' \cup B'$` | `$\lnot (P \land Q) \equiv \lnot P \lor \lnot Q$`

---

![large](http://fondinfo.github.io/images/comp/domino.svg)
# ⭐ Principio di induzione

- Sia `$P(n)$` un predicato definito su `$ℕ$`, tale che:
    - **①** `$P(1)$` è vero
    - **②** `$\forall n$`, supponendo `$P(n)$` vero, <br> segue che anche `$P(n+1)$` è vero
- Allora `$P(n)$` risulta vero `$\forall n$`

Premesse | Conclusione
---------|------------
`$P(1)$` <br> `$\forall n, P(n) \implies P(n+1)$` | `$\forall n, P(n)$`

>

Alcuni predicati sono definiti a partire da un dato `$k$`, anzichè da 1

---

# 🧪 Esempio, formula di Gauss

- Definiamo per comodità `$G(n) = \frac{n \cdot (n+1)}{2}$`
- Definiamo il predicato `$P(n)$` come: `$1 + 2 +  \cdot  \cdot  \cdot  + n = G(n)$`
- Dimostriamo *per induzione* che il predicato è vero `$\forall n$`
- **①** Il predicato per `$n=1$` è vero, infatti:
    - `$G(1) = \frac{1 \cdot (1+1)}{2} = 1$`
- **②** Supponiamo `$P(n)$` vero, ne segue `$P(n+1)$` vero, infatti:
    - Per la somma fino a `$n+1$`, bisogna aggiungere un termine:
    - `$1 + 2 + ... + n + n+1 = G(n) + n+1 = \\ \frac{n \cdot (n+1)}{2} + n+1 = \frac{n^2 + 3n + 2}{2} = \\ \frac{(n+1) \cdot (n+2)}{2} = G(n+1)$`
- Quindi la formula vale `$\forall n$`

---

![large](http://fondinfo.github.io/images/fun/hanoi.svg)
# 🧪 Esempio, Torre di Hanoi

- *Regola 1*: Spostare solo un disco alla volta
- *Regola 2*: Poggiarlo solo su uno più grande
- *Strategia* per `$n+1$` dischi
    - `$n$` dischi → piolo di appoggio, in `$R(n)$` mosse
    - poi ultimo disco → destinazione
    - infine gli altri → destinazione, in `$R(n)$` mosse
- Dimostrare *per induzione* che il numero di mosse per spostare `$n$` dischi è `$R(n) = 2^n-1$`
- **①** Per 1 disco, 1 mossa: `$1 = 2^1-1 = R(1)$`
- **②** Supponiamo servano `$R(n)$` mosse per `$n$` dischi...
    - Allora per `$n+1$` dischi:
    - `$R(n) + 1 + R(n) = 2 \cdot (2^n-1)+1 = 2^{n+1}-1 = R(n+1)$`
- Quindi la formula vale `$\forall n$`

---

![](http://fondinfo.github.io/images/repr/homer-genius.png)
# ⚠️ Sillogismi errati e quiz

- *Premessa maggiore*: “Tutti i geni sono distratti”
    - `$\forall x, genio(x) \implies distratto(x)$`
- *Premessa minore*: “Io sono distratto”
    - `$distratto(Io)$`
- *Conclusione*: “Io sono un genio”
    - `$genio(Io)$` – **Doh!** 😕
- Attenzione a usare l'implicazione giusta!
    - `$P \implies Q$`: condizione sufficiente, ma non necessaria
    - “Tutti gli svedesi sono biondi” …

>

<https://www.beniculturali.it/mibac/multimedia/MiBAC/documents/1228312182183_F1_Logica.pdf>
<br>
Domande 20, 22, 24, 27
