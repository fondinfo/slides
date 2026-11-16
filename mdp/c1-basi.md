# Linguaggio C
## Introduzione alla programmazione

---

# Dal Python al C

---

![](http://fondinfo.github.io/images/hist/thompson-ritchie.jpg)
# 💡 Python e C a confronto

| | Python | C |
|---|---|---|
| Esecuzione | bytecode su macchina virtuale | codice macchina nativo |
| Tipi | dinamici | statici |
| Memoria | gestita | in mano al programmatore |
| Errori | eccezioni | spesso... silenzio 😱 |

- C: linguaggio di sistemi operativi, embedded, interpreti
    - *CPython* è scritto in C!
- D. Ritchie, 1972 (Unix)

---

# Dal sorgente all'eseguibile

---

![](http://fondinfo.github.io/images/algo/helloworld.png)
# 🧪 Il primo programma

``` c
#include <stdio.h>

int main(void) {
    printf("Hello, world!\n");
    return 0;
}
```

- Python: `print("Hello, world!")`
- ❓ Cosa ci sembra inutile? Cosa manca?

---

![](http://fondinfo.github.io/images/dev/build.svg)
# ⭐ Compilare ed eseguire

``` sh
gcc hello.c -o hello
./hello
```

- Il **compilatore** traduce *tutto* il sorgente in codice macchina
- Poi si esegue il file prodotto
- Windows: `hello.exe`

> Python: `python hello.py` compila in *bytecode* (`.pyc`), poi lo esegue su una *macchina virtuale*
<br>
C: il risultato è codice macchina, eseguito direttamente dalla CPU

---

![](http://fondinfo.github.io/images/dev/compiler.svg)
# 💡 Le fasi della compilazione

1. **Preprocessore**: `#include`, `#define`
2. **Compilatore**: C → assembly
3. **Assemblatore**: → file oggetto `.o`
4. **Linker**: oggetti + librerie → eseguibile

``` sh
gcc -E hello.c    # solo preprocessore
gcc -S hello.c    # fino ad assembly
gcc -c hello.c    # fino a hello.o
```

---

# ⭐ Warning: sempre attivi!

``` sh
gcc -std=c11 -Wall -Wextra -pedantic hello.c -o hello
```

- Il compilatore *segnala* molti errori che Python scoprirebbe a runtime
- ⚠️ Un *warning* è quasi sempre un bug
- Obiettivo: zero warning

---

# 🧪 Leggere i messaggi

``` c
#include <stdio.h>

int main(void) {
    printf("Hi")
    return 0;
}
```

``` txt
hello.c: In function 'main':
hello.c:5:5: error: expected ';' before 'return'
```

- ❓ Riga e colonna: dove guardare? Perché la riga 5?
- Errori in sequenza: correggere il *primo*

---

# Struttura e tipi

---

# ⭐ Struttura di un programma

- **`#include`**: porta le dichiarazioni di una libreria
    - `<stdio.h>`: I/O, `<stdlib.h>`, `<math.h>`...
- **`main`**: punto di ingresso, restituisce un `int`
    - `return 0`: tutto ok (codice di uscita)
- Istruzioni terminate da **`;`**, blocchi tra **`{ }`**
    - L'indentazione non conta per il compilatore
- Commenti: `// riga` e `/* blocco */`

---

![](http://fondinfo.github.io/images/algo/my-shoes.png)
# ⭐ Tipi di dato

- **`int`**: interi (tipicamente 32 bit)
- **`long`, `long long`**: interi più ampi
- **`double`**: reali (`float`: meno precisi)
- **`char`**: un carattere (1 byte)
- **`bool`**: con `#include <stdbool.h>`

``` c
int n = 5;
double x = 2.5;
char c = 'A';
```

- Variabili *dichiarate* con il loro tipo, che non cambia più
- Una variabile C è una *scatola*, di dimensione fissa
    - Python: un'*etichetta* su un oggetto

---

# 🧪 Dimensioni dei tipi

``` c
printf("%zu\n", sizeof(int));     // 4
printf("%zu\n", sizeof(double));  // 8
printf("%zu\n", sizeof(char));    // 1
```

- `sizeof`: dimensione in byte
- Limiti: `<limits.h>` (`INT_MAX`), `<float.h>`
- ❓ Quanti valori distinti in 32 bit?

---

![](http://fondinfo.github.io/images/repr/twos-compl.svg)
# ⚠️ Gli interi non sono infiniti

``` c
int x = INT_MAX;  // 2147483647
x = x + 1;        // ???
```

- Python: `2 ** 100` funziona sempre
- C: il risultato *esce dai bit* disponibili
    - Per `int` con segno: comportamento *indefinito*
- Scegliere il tipo adatto al problema

---

# ⚠️ Divisione intera e resto

``` c
printf("%d\n", 7 / 2);     // 3
printf("%f\n", 7 / 2.0);   // 3.500000
printf("%d\n", -7 % 3);    // -1
```

- `/` tra due interi: divisione *intera*
- Per avere un reale: almeno un operando `double`
- Cast: `(double) a / b`
- `%` con negativi: *diverso da Python*

---

# 💡 Operatori: da Python a C

| Python | C |
|---|---|
| `a // b` | `a / b` (tra interi) |
| `a ** b` | `pow(a, b)` (`<math.h>`) |
| `and`, `or`, `not` | `&&`, `\|\|`, `!` |
| `i += 1` | `i++`, `i += 1` |
| `x = y = 0` | idem |

---

# 💡 Un `char` è un numero

``` c
char c = 'A';
printf("%c %d\n", c, c);   // A 65
c = c + 1;                 // 'B'
```

- Nessun `ord` / `chr`: sono già interscambiabili
- `'A'` (apici singoli): *un* carattere
- `"A"` (virgolette): una *stringa*, tutt'altra cosa...

>

Le stringhe in C: prossimo capitolo

---

# 💡 Tabella ASCII

![large](http://fondinfo.github.io/images/repr/ascii-large.svg)

---

# 💡 Costanti

``` c
#define N 10
const double PI = 3.14159265;
```

- `#define`: sostituzione di testo, prima di compilare
- `const`: variabile non modificabile
- Convenzione: nomi maiuscoli

---

# Output

---

# ⭐ printf

``` c
int n = 5;
double x = 2.5;
printf("n = %d, x = %f\n", n, x);
```

- Prima la *stringa di formato*, poi i valori
- **`%d`** int, **`%ld`** long, **`%f`** double
- **`%c`** char, **`%s`** stringa, **`%x`** esadecimale
- **`%%`** per scrivere `%`
- Niente a capo automatico: serve `\n`

---

# 🧪 Larghezza e precisione

``` c
printf("%5d|%-5d|\n", 42, 42);   //    42|42   |
printf("%.2f\n", 3.14159);       // 3.14
printf("%8.3f\n", 3.14159);      //    3.142
```

- Python: `f"{x:.2f}"`, `f"{n:5}"`
- ❓ Come stampare una tabella allineata?

---

# ⚠️ Specificatore sbagliato

``` c
printf("%d\n", 3.5);    // ???
printf("%f\n", 42);     // ???
```

- Il compilatore *non controlla* il tipo dei valori
- Risultato: numeri a caso, o crash
- `-Wall` segnala molti di questi errori

---

# Input

---

![](http://fondinfo.github.io/images/algo/hello-user.svg)
# ⭐ scanf

``` c
int n;
printf("n? ");
scanf("%d", &n);
printf("Square: %d\n", n * n);
```

- Python: `n = int(input("n? "))`
- `&n`: *indirizzo* di `n`, cioè dove `scanf` deve scrivere
    - Una funzione C non può modificare le variabili di chi la chiama...
    - ...a meno che non ne riceva l'indirizzo
- ❓ Cosa succederebbe senza `&`?

---

# ⭐ Il risultato di scanf

``` c
int n;
int r = scanf("%d", &n);
```

- `r == 1`: valore letto correttamente
- `r == 0`: input non numerico (es. `abc`)
- `r == EOF`: fine dell'input
- ❓ Cosa fare se l'utente scrive `abc`?

---

![](http://fondinfo.github.io/images/algo/sentinel.svg)
# 🧪 Sentinella: fino a fine input

``` c
int v, total = 0;
while (scanf("%d", &v) == 1) {
    total += v;
}
printf("Sum: %d\n", total);
```

- Si ferma con input non valido o con fine file
    - Ctrl-D (Linux/Mac), Ctrl-Z (Windows)
- Anche da file: `./sum < numbers.txt`

>

`while`, come in Python: sintassi del C tra poche slide

---

# ⚠️ Dettagli di scanf

``` c
double x;
scanf("%lf", &x);   // lf per double, in scanf!

char c;
scanf(" %c", &c);   // lo spazio salta i bianchi
```

- `printf`: `%f` per `double`
- `scanf`: `%lf` per `double`
- Il tasto Invio resta nel buffer di input

---

![](http://fondinfo.github.io/images/misc/dice.png)
# ⭐ Numeri casuali

``` c
#include <stdlib.h>
#include <time.h>

int main(void) {
    srand(time(NULL));   // once, at the start

    for (int i = 0; i < 5; i++) {
        printf("%d\n", rand() % 6 + 1);   // 1..6
    }
    return 0;
}
```

- **`srand`: una sola volta**, all'inizio del programma
- `rand() % n` → da `0` a `n-1`
- Python: `random.randint(a, b)`

>

`for` del C: tra poche slide

---

# Controllo del flusso

---

![](http://fondinfo.github.io/images/algo/if-else.svg)
# ⭐ if / else

``` c
if (a < b) {
    printf("The words are ordered\n");
} else if (a > b) {
    printf("The words are inverted\n");
} else {
    printf("The words are equal\n");
}
```

- Condizione *tra parentesi*, niente `:`
- `elif` → `else if`
- Graffe sempre, anche per una sola istruzione

---

# 💡 Vero e falso

- `0` è **falso**, qualsiasi altro valore è **vero**
- I confronti producono `0` o `1`
- `<stdbool.h>`: `bool`, `true`, `false`

``` c
int n = 5;
if (n) printf("true\n");
if (!n) printf("false\n");
```

---

# ⚠️ Due classici

``` c
if (x = 5) { /* ... */ }        // assegnamento, non confronto!
if (0 <= x && x <= 10) { }      // corretto
if (0 <= x <= 10) { }           // sempre vero!
```

- Python: `0 <= x <= 10` funziona
- C: `(0 <= x) <= 10` → `0` o `1`, `<= 10`
- `-Wall` segnala il primo caso

---

![](http://fondinfo.github.io/images/algo/while.svg)
# ⭐ Cicli for e while

``` c
for (int i = 0; i < n; i++) {
    printf("%d\n", i);
}

int count = 0;
while (count < n) {
    printf("%d\n", count);
    count++;
}
```

- `for (init; condizione; passo)`
- Python: `for i in range(n)`

---

# 🧪 Ciclo do-while

``` c
int v;
do {
    printf("Value (>= 0)? ");
    scanf("%d", &v);
} while (v < 0);
```

- La condizione è controllata *dopo*
- Utile per validare l'input
- ❓ Come si farebbe in Python?

---

![](http://fondinfo.github.io/images/fun/times-table.svg)
# 🧪 Tavola pitagorica

``` c
for (int y = 1; y <= 10; y++) {
    for (int x = 1; x <= 10; x++) {
        printf("%4d", x * y);
    }
    printf("\n");
}
```

- Python: `print(x * y, end="\t")`
- Qui `%4d` + `\n` a fine riga

---

# ⭐ switch

``` c
switch (op) {
    case '+': r = a + b; break;
    case '-': r = a - b; break;
    case '*': r = a * b; break;
    default:
        printf("Operation not allowed\n");
}
```

- Solo per interi e `char`
- ⚠️ Senza `break`, l'esecuzione *prosegue* nel caso successivo

---

# Funzioni

---

![](http://fondinfo.github.io/images/fun/function.png)
# ⭐ Definire una funzione

``` c
int square(int x) {
    return x * x;
}

int main(void) {
    printf("%d\n", square(7));
    return 0;
}
```

- Tipo restituito e tipi dei parametri *obbligatori*
- `void`: nessun valore / nessun parametro

---

# ⭐ Prototipi

``` c
int square(int x);   // prototype

int main(void) {
    printf("%d\n", square(7));
    return 0;
}

int square(int x) {
    return x * x;
}
```

- Una funzione si deve *dichiarare* prima dell'uso
- Il prototipo dice solo *come si chiama* e *che tipi ha*

---

# ⚠️ Parametri per valore

``` c
void inc(int x) {
    x++;
}

int n = 5;
inc(n);
printf("%d\n", n);   // 5
```

- La funzione riceve una *copia*
- ❓ Come far modificare `n` a `inc`?
    - Come fa `scanf`...

>

Risposta: nel prossimo capitolo

---

# 💡 Riepilogo

- *Compilare* prima di eseguire; **`-Wall -Wextra`** sempre
- Tipi statici, dimensioni finite
- `printf` / `scanf`: stringhe di formato
- Controllo flusso: stessa logica, sintassi diversa
- Funzioni: tipi e prototipi

---

# 🏊 Esercizi

---

# Compilare e rompere

- Compilare `hello.c` con `-Wall -Wextra -pedantic`
- Introdurre, uno alla volta, questi errori
    - Dimenticare `;`
    - Dimenticare `#include <stdio.h>`
    - Scrivere `pritnf`
- Per ciascuno, leggere il messaggio e spiegarlo

---

# Dimensioni dei tipi

- Stampare `sizeof` di `char`, `int`, `long`, `long long`, `double`
- Stampare anche `INT_MAX` e `INT_MIN`
- Eseguire poi `INT_MAX + 1`
    - Cosa si ottiene?
    - Cosa dice il compilatore?

---

# Fattoriale e overflow

- Chiedere un numero $n$ e calcolare $n!$
- Prima con `int`, poi con `long long`
- Stampare i fattoriali da $1$ a $25$
- Da quale $n$ il risultato è palesemente sbagliato?

>

Python non ha questo problema: perché?

---

# Somma con sentinella

- Leggere interi, con `scanf`, fino a input non valido
- Alla fine, visualizzare
    - Quanti valori sono stati letti
    - Somma e media (con decimali!)
- Provare anche con: `./prog < dati.txt`

---

# Somma di potenze di 2

- Chiedere all'utente un numero $n$
- Sommare le prime $n$ potenze di 2
    - $2^0 + 2^1 + ... + 2^{n-1}$
- Verificare con la formula $2^n - 1$
- ⚠️ Fino a quale $n$ funziona con `int`?

---

![](http://fondinfo.github.io/images/misc/bingo-balls.png)
# Numero segreto

- Generare un numero casuale tra 1 e 90
    - `rand() % 90 + 1`, con `<stdlib.h>`
    - `srand(time(NULL))`, `<time.h>`: *una sola volta*, all'inizio
- Chiedere ripetutamente un numero, finché l'utente non indovina
- Dire se è maggiore o minore
- Contare i tentativi

---

![](http://fondinfo.github.io/images/fun/times-table.svg)
# Tavola pitagorica allineata

- Chiedere all'utente la dimensione $n$
- Stampare la tabella $n \times n$ delle moltiplicazioni
- Le colonne devono essere allineate
    - Larghezza calcolata in base ai valori massimi
- Stampare anche una riga di intestazione

---

# Distanza dagli angoli

- Chiedere due interi $w$ e $h$
- Stampare due tabelle con la distanza di Manhattan
    1. Dall'angolo in alto a sinistra
    2. Dall'angolo in basso a sinistra

``` txt
0 1 2 3
1 2 3 4
2 3 4 5
```

---

![](http://fondinfo.github.io/images/algo/calc.svg)
# Calcolatrice

- Leggere un'operazione nella forma `a op b`
    - Es. `3.5 * 2`
- Operatori: `+ - * /`
- Usare `switch` sull'operatore
- Divisione per zero: messaggio di errore
- Ripetere finché l'input è valido

---

![](http://fondinfo.github.io/images/games/climbing.svg)
# Free climbing

- Gara tra due arrampicatori, in forma testuale
- Ripetutamente, generare due numeri casuali in $[-1, 3]$
    - Seme impostato una volta sola
- Il livello non scende mai sotto $0$
- Vince chi arriva prima in cima (`#define TOP 30`)
- Suddividere il codice in funzioni
    - Es. `int jump(int level)`
