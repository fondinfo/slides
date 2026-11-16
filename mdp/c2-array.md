# Linguaggio C
## Array, stringhe e puntatori

---

# Array

---

![](http://fondinfo.github.io/images/misc/number-train.png)
# 💡 Array: dimensione fissa

- Python `list`: dinamica, elementi di tipi diversi
- C **array**: dimensione *fissa*, elementi dello *stesso tipo*
    - Tutti *contigui* in memoria
- Variabile C = scatola; array = fila di scatole 📦📦📦

``` c
int v[5] = {3, 7, 5, 6, 2};
```

---

# ⭐ Dichiarare un array

``` c
int v[5];                  // 5 int, valori casuali!
int w[5] = {3, 7, 5, 6, 2};
int z[5] = {0};            // tutti a zero
int u[] = {1, 2, 3};       // dimensione dedotta: 3
```

- Python: `w = [3, 7, 5, 6, 2]`
- Dimensione: *costante* nota alla compilazione
- ⚠️ Senza inizializzatore, contenuto *indefinito*

---

# ⭐ Indici e cicli

``` c
int v[5] = {3, 7, 5, 6, 2};
int n = sizeof(v) / sizeof(v[0]);   // 5

for (int i = 0; i < n; i++) {
    printf("%d\n", v[i]);
}
```

- Indici da `0` a `n-1`
- Niente `len`: si calcola con `sizeof`
    - Solo dove l'array è dichiarato
- Python: `for x in v`

---

# ⚠️ Nessun controllo dei limiti

``` c
int v[5] = {3, 7, 5, 6, 2};
v[5] = 99;                // ???
printf("%d\n", v[-1]);    // ???
```

- Python: `IndexError`
- C: legge e scrive *memoria altrui*, senza avvisi
    - Crash, o peggio: dati *corrotti*
- Gli indici li controlla il programmatore

---

# 🧪 Massimo di un array

``` c
int v[] = {3, 7, 5, 6};
int n = sizeof(v) / sizeof(v[0]);

int largest = v[0];
for (int i = 1; i < n; i++) {
    if (v[i] > largest) {
        largest = v[i];
    }
}
printf("%d\n", largest);
```

- Python: `max(v)`
- ❓ Perché partire da `v[0]`? E se usassimo `INT_MIN`?

---

![](http://fondinfo.github.io/images/fun/dynamic-array.svg)
# ⭐ Array riempito in parte

``` c
#define MAX 100

int v[MAX];
int n = 0;
while (n < MAX && scanf("%d", &v[n]) == 1) {
    n++;
}
```

- **Capacità**: `MAX`, fissa
- **Dimensione effettiva**: `n`, contatore
- Python: `v.append(x)`

---

# ⭐ Array e funzioni

``` c
int largest(int v[], int n) {
    int best = v[0];
    for (int i = 1; i < n; i++) {
        if (v[i] > best) {
            best = v[i];
        }
    }
    return best;
}

printf("%d\n", largest(w, 5));
```

- La lunghezza **va passata** come parametro

---

# ⚠️ sizeof dentro una funzione

``` c
void f(int v[]) {
    printf("%zu\n", sizeof(v));   // 8, non 20!
}
```

- Il parametro `v` è un *indirizzo*, non l'array
- ❓ Una funzione può *modificare* l'array del chiamante: come mai?

>

Risposta: tra poche slide

---

![large](http://fondinfo.github.io/images/scipy/c-array-array.svg)
# ⭐ Matrici

``` c
#define ROWS 3
#define COLS 4

int m[ROWS][COLS] = {{1, 2, 3, 4},
                     {5, 6, 7, 8},
                     {9, 10, 11, 12}};

for (int y = 0; y < ROWS; y++) {
    for (int x = 0; x < COLS; x++) {
        printf("%3d", m[y][x]);
    }
    printf("\n");
}
```

- Righe consecutive in memoria
- Come parametro: `int m[][COLS]`

---

# Indirizzi e puntatori

---

![large](http://fondinfo.github.io/images/sys/pointer.svg)
# 💡 La memoria ha indirizzi

- Memoria: sequenza di celle *numerate*
- Ogni variabile occupa alcune celle, a un certo **indirizzo**
- **Puntatore**: variabile che contiene un indirizzo
- ❓ Una scatola ha un *contenuto* … e una *posizione*

---

# ⭐ Gli operatori & e *

``` c
int x = 5;
int *p = &x;    // p holds the address of x

printf("%d\n", *p);   // 5
*p = 10;              // x is now 10
printf("%d\n", x);    // 10
```

- **`&x`**: indirizzo di `x`
- **`int *p`**: `p` è un puntatore a `int`
- **`*p`**: il valore *puntato* (dereferenziazione)

---

# 🧪 Stampare un indirizzo

``` c
int x = 5;
printf("%p\n", (void *) &x);   // es. 0x7ffc5a3b1c24
printf("%zu\n", sizeof(&x));   // 8
```

- `%p`: indirizzo, in esadecimale
- Cambia a ogni esecuzione
- ❓ Quanto occupa un puntatore? Dipende dal tipo puntato?

---

# ⭐ Parametri per indirizzo

``` c
void inc(int *x) {
    (*x)++;
}

int n = 5;
inc(&n);
printf("%d\n", n);   // 6
```

- Risposta alla domanda di prima:
    - L'indirizzo *permette di modificare* l'originale
    - `scanf("%d", &n)`: stessa tecnica!

---

# 🧪 Scambio di due valori

``` c
void swap(int *a, int *b) {
    int tmp = *a;
    *a = *b;
    *b = tmp;
}

swap(&x, &y);
```

- Python: `a, b = b, a`
- ❓ Perché `swap(int a, int b)` non funzionerebbe?

---

# ⭐ Più risultati da una funzione

``` c
void min_max(int v[], int n, int *min, int *max) {
    *min = *max = v[0];
    for (int i = 1; i < n; i++) {
        if (v[i] < *min) {
            *min = v[i];
        }
        if (v[i] > *max) {
            *max = v[i];
        }
    }
}

int lo, hi;
min_max(w, 5, &lo, &hi);
```

- Python: `return lo, hi`
- *Parametri di output*

---

# 💡 Array e puntatori

``` c
int v[3] = {10, 20, 30};
int *p = v;                // come &v[0]

printf("%d\n", *p);        // 10
printf("%d\n", *(p + 1));  // 20
printf("%d\n", p[2]);      // 30
```

- Il nome di un array è l'*indirizzo del primo elemento*
- `v[i]` equivale a `*(v + i)`
- Per questo una funzione riceve l'array *senza copiarlo*

---

# ⚠️ Puntatori pericolosi

``` c
int *p;          // ⚠️ non inizializzato
*p = 5;          // ???

int *q = NULL;   // non punta a nulla
if (q != NULL) {
    *q = 5;
}
```

- Puntatore non inizializzato: indirizzo *casuale*
- `NULL`: “nessun indirizzo”
    - Dereferenziarlo → crash (*segmentation fault*)
- Mai restituire l'indirizzo di una variabile *locale*

---

# Stringhe

---

![](http://fondinfo.github.io/images/misc/letters.png)
# 💡 Stringhe in C

- Nessun tipo `str`
- Stringa = *array di `char`*, terminato da **`'\0'`**
    - Il carattere di codice `0`

``` c
char s[] = "Hi";   // 'H', 'i', '\0'
```

- ❓ Quanti byte occupa `"Hello"`?

---

# 🧪 Lunghezza e terminatore

``` c
#include <string.h>

char s[] = "Hello";
printf("%zu\n", sizeof(s));   // 6
printf("%zu\n", strlen(s));   // 5

s[2] = '\0';
printf("%s\n", s);            // He
```

- `strlen`: conta *fino al primo* `'\0'`
- `printf("%s")` si ferma allo stesso modo
- Le stringhe C sono *modificabili*

---

# ⭐ Cicli su stringhe

``` c
char s[] = "Python";
for (int i = 0; s[i] != '\0'; i++) {
    printf("%d\n", s[i]);
}
```

- Python: `for c in s: print(ord(c))`
- Si prosegue fino al terminatore
- ❓ E con `i < strlen(s)`? Funziona... ma a che costo?

---

# 🧪 Contare vocali e cifre

``` c
#include <ctype.h>

int digits = 0, vowels = 0;
for (int i = 0; s[i] != '\0'; i++) {
    char c = tolower(s[i]);
    if ('0' <= c <= '9')) {
        digits++;
    } else if (c == 'a' || c == 'e' || c == 'i' ||
               c == 'o' || c == 'u') {
        vowels++;
    }
}
```

- `<ctype.h>`: `isdigit`, `isalpha`, `isupper`, `tolower`, `toupper`
- Python: `c in "aeiou"`

---

# ⭐ Funzioni di string.h

| Python | C |
|---|---|
| `len(s)` | `strlen(s)` |
| `a == b` | `strcmp(a, b) == 0` |
| `a < b` | `strcmp(a, b) < 0` |
| `a = b` | `strcpy(a, b)` |
| `a += b` | `strcat(a, b)` |
| `b in a` | `strstr(a, b) != NULL` |

- In C la copia e la concatenazione sono *esplicite*

---

# ⚠️ Confronto tra stringhe

``` c
char a[] = "abc";
char b[] = "abc";

if (a == b) {                // ⚠️ confronta gli indirizzi
    printf("equal\n");
}
if (strcmp(a, b) == 0) {     // ✅
    printf("equal\n");
}
```

- `strcmp`: `0` se uguali, `< 0` se `a` precede `b`, `> 0` altrimenti
- Ordine *lessicografico*, come in Python

---

# ⚠️ Buffer overflow

``` c
char buf[5];
strcpy(buf, "Hello, world!");   // ⚠️
```

- 14 byte copiati in uno spazio da 5
- Python: le stringhe crescono da sole
- C: si scrive *oltre l'array* → crash, o *falla di sicurezza*
- Sempre controllare la capacità del buffer!

---

# ⭐ Comporre stringhe: snprintf

``` c
char msg[100];
double radius = 2.5;
snprintf(msg, sizeof(msg),
         "Circle with radius %.1f", radius);
```

- Come una *f-string*: stessa sintassi di `printf`
- Il secondo parametro è il *limite* di byte
- Python: `f"Circle with radius {radius:.1f}"`

---

# ⭐ Leggere una riga

``` c
char line[100];
fgets(line, sizeof(line), stdin);
```

- Legge *al massimo* 99 caratteri, più `'\0'`
- ⚠️ Conserva il `'\n'` finale
- `scanf("%s")`: una sola parola e *nessun limite*
    - Con limite: `scanf("%99s", word)`
- Python: `line = input()`

>

`stdin`: stream standard di input, nella prossima parte

---

# 🧪 Togliere il newline

``` c
char line[100];
fgets(line, sizeof(line), stdin);
line[strcspn(line, "\n")] = '\0';
```

- `strcspn`: posizione del primo `'\n'` (o della fine)
- Lì si mette il terminatore
- Python: `input()` non include il `'\n'`

---

# 🧪 Inversione di una stringa

``` c
void reverse(char s[]) {
    int i = 0, j = strlen(s) - 1;
    while (i < j) {
        char tmp = s[i];
        s[i] = s[j];
        s[j] = tmp;
        i++;
        j--;
    }
}
```

- Python: `s[::-1]` (nuova stringa)
- C: *sul posto*, con due indici
- ❓ Simuliamo con `"Python"`

---

# ⭐ Da stringa a numero

``` c
#include <stdlib.h>

char *end;
long k = strtol(s, &end, 10);
if (*end != '\0') {
    printf("Not a number\n");
}
```

- `strtol` (e `strtod` per `double`)
- `end`: punta al primo carattere *non convertito*
    - Come `scanf`, riceve un *indirizzo* da riempire
- `atoi("abc")` dà `0`, senza errori
- Python: `int(s)`, con `ValueError`

---

# Argomenti da riga di comando

---

# 💡 Programmi da terminale

``` sh
gcc -Wall hello.c -o hello
./sum 3 4 5
./greet Anna
```

- Molti comandi accettano *argomenti*
- Python: `sys.argv`
- La riga di comando arriva al programma già *divisa in parole*

---

# ⭐ argc e argv

``` c
int main(int argc, char *argv[]) {
    for (int i = 0; i < argc; i++) {
        printf("%d: %s\n", i, argv[i]);
    }
    return 0;
}
```

``` sh
$ ./args one two
0: ./args
1: one
2: two
```

- `argc`: numero di argomenti, *incluso* il nome del programma
- `argv`: array di stringhe

---

# 🧪 Controllo degli argomenti

``` c
int main(int argc, char *argv[]) {
    if (argc != 2) {
        fprintf(stderr, "Usage: %s name\n", argv[0]);
        return 1;
    }
    printf("Hello, %s!\n", argv[1]);
    return 0;
}
```

- `return 1`: *codice di uscita* di errore
- `stderr`: canale per gli errori, nella prossima parte

---

# ⭐ Argomenti numerici

``` c
long total = 0;
for (int i = 1; i < argc; i++) {
    char *end;
    long v = strtol(argv[i], &end, 10);
    if (*end != '\0') {
        fprintf(stderr, "Not a number: %s\n", argv[i]);
        return 1;
    }
    total += v;
}
printf("Sum: %ld\n", total);
```

- Gli argomenti sono *sempre stringhe*
- Python: `int(sys.argv[1])`

---

# 🧪 Codici di uscita

- `return 0`: successo; altro valore: errore
- La shell lo legge: `echo $?`
    - Windows: `echo %ERRORLEVEL%`
- **`&&`**: eseguire il secondo comando *solo se il primo ha successo*

``` sh
gcc -Wall hello.c -o hello && ./hello
```

---

# 💡 Riepilogo

- **Array**: dimensione fissa, *nessun controllo* dei limiti
- **Puntatori**: indirizzi; `&` e `*`
- **Stringhe**: `char[]` + `'\0'`, funzioni di `<string.h>`
- **`argc` / `argv`**: argomenti sempre *stringhe*, da convertire
- Gli errori di memoria sono *silenziosi*

---

# 🏊 Esercizi

---

# Statistiche di un array

- Leggere da input fino a 100 interi, in un array
    - Fino a fine input, o input non valido
- Calcolare minimo, massimo e media
    - Funzione `min_max` con parametri di output
- Stampare lo scarto di ogni valore dalla media

---

# Inversione di array

- Funzione `reverse(int v[], int n)`
    - Inverte l'ordine degli elementi, *sul posto*
    - Senza array di appoggio
- Provare con lunghezze pari e dispari
- Usare `swap` dell'esempio

---

# Ordinamento

- Leggere un array di interi, come nell'esercizio precedente
- Ordinarlo in modo crescente
    - *Selection sort*: trovare il minimo, scambiarlo con la prima posizione, ripetere sul resto
- Stampare l'array prima e dopo

---

# Matrice trasposta

- Matrice $3 \times 4$ di interi, con valori dati
- Stampare la matrice originale
- Calcolare e stampare la *trasposta* $4 \times 3$
    - $t[x][y] = m[y][x]$
- Usare costanti `ROWS` e `COLS`

---

# Vocali e cifre in una riga

- Leggere una riga con `fgets`
- Contare vocali, cifre e altri caratteri
    - Rivedere esempio in Python
    - Usare `tolower`, `isdigit`
- Togliere il `'\n'` finale prima dei conteggi

---

# Palindromi

- Leggere una riga di testo
- Verificare se è una frase *palindroma*
    - Ignorando maiuscole/minuscole e spazi
    - Es. "Anna", "I topi non avevano nipoti"
- Usare due indici, dall'inizio e dalla fine

---

# Parole di una riga

- Leggere una riga di testo
- Contare le parole, separate da spazi
- Stampare la parola più lunga
- Copiare la parola in un array con `strcpy`
    - Attenzione alla capacità!

---

![](http://fondinfo.github.io/images/hist/caesar-cipher.jpg)
# Cifrario di Cesare

- Leggere una frase e un intero $k$
- Cifrare ogni lettera, spostandola di $k$ posizioni
    - Es. $k = 3$: `A` → `D`, `Z` → `C`
    - Maiuscole e minuscole separate
    - Altri caratteri invariati
- Decifrare, usando $-k$

---

# Somma degli argomenti

- Programma `./sum 3 4 5`: stampa `12`
- Argomenti convertiti con `strtol`
- Se manca un argomento, o non è un numero
    - Messaggio di errore su `stderr`
    - Codice di uscita `1`

---

# Calcolatrice da riga di comando

- Programma `./calc 3.5 + 2`
    - Tre argomenti: numero, operatore, numero
- Operatori: `+ - x /`
- Convertire con `strtod`
- Divisione per zero, argomenti sbagliati: errore, con uso corretto
- ⚠️ La shell espande `*`: usare `x` oppure `'*'`
