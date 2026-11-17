# Linguaggio C
## File, stream e progetti

---

# Stream

---

![](http://fondinfo.github.io/images/repr/audio-cassette.png)
# 💡 Stream

- **Stream**: sequenza di caratteri, letta o scritta *in ordine*
    - Come un nastro 📼: si va avanti, un carattere dopo l'altro
- Tastiera, schermo, file: tutti *stream*
- Python: `input()`, `print()`, `open()`
- C: tipo **`FILE *`**, in `<stdio.h>`

---

![](http://fondinfo.github.io/images/sys/peripherals.svg)
# ⭐ I tre stream standard

- **`stdin`**: input (di solito, la tastiera)
- **`stdout`**: output (di solito, lo schermo)
- **`stderr`**: *errori* (di solito, lo schermo)

``` c
printf("Hello\n");                      // = fprintf(stdout, ...)
fprintf(stderr, "Something went wrong\n");
```

- `scanf` legge da `stdin`
- Python: `sys.stdin`, `sys.stdout`, `sys.stderr`

---

# ⭐ Redirezione

``` sh
./prog < in.txt           # stdin da file
./prog > out.txt          # stdout su file (sovrascrive)
./prog >> out.txt         # stdout in aggiunta al file
./prog 2> err.txt         # stderr su file
./prog < in.txt > out.txt 2> err.txt
```

- Il programma *non cambia*: decide la shell
- `stderr` separato: gli errori non si mescolano ai dati
- ❓ Con `./prog > out.txt`, dove appare un messaggio di errore?

---

# 🧪 Filtro: maiuscole

``` c
#include <ctype.h>

int c;
while ((c = getchar()) != EOF) {
    putchar(toupper(c));
}
```

``` sh
./upper < in.txt > out.txt
```

- Un carattere alla volta, fino a *fine input* (`EOF`)
    - Da tastiera: Ctrl-D (Windows: Ctrl-Z)
- Python: `for line in sys.stdin`
- ❓ Perché `int c`, e non `char c`?

---

# ⚠️ EOF e tipo int

``` c
char c;                                    // ⚠️
while ((c = getchar()) != EOF) { /* ... */ }
```

- `getchar` restituisce un **`int`**
    - Un carattere (da `0` a `255`) *oppure* `EOF` (`-1`)
- Con `char c`, il byte `0xFF` (es. `ÿ`) viene scambiato per `EOF`
    - Su altre piattaforme, il ciclo può non finire mai
- Vale anche per `fgetc` (lettura da file)

---

# ⭐ Pipe

``` sh
cat in.txt | ./upper | sort
```

- **`|`**: lo `stdout` di un programma diventa lo `stdin` del successivo
- Piccoli programmi *componibili* : i **filtri**
- Filosofia Unix: ogni programma fa *una cosa*, bene
- Windows: `type` al posto di `cat`

---

# File di testo

---

![](http://fondinfo.github.io/images/repr/file-system.svg)
# 💡 File e percorsi

- File di testo: sequenza di righe, ognuna terminata da `\n`
- Percorso *relativo* (`data/prod.csv`) o *assoluto* (`/home/ana/prod.csv`)
    - Relativo: rispetto alla cartella da cui si *lancia* il programma
- Python: `with open("prod.csv") as f:`

---

# ⭐ fopen e fclose

``` c
FILE *f = fopen("data.txt", "r");
if (f == NULL) {
    fprintf(stderr, "Cannot open data.txt\n");
    return 1;
}
/* ... use f ... */
fclose(f);
```

- `fopen`: apre il file, restituisce un `FILE *`
- `NULL` se l'apertura fallisce
- `fclose`: *sempre*, a fine uso

---

# ⚠️ Controllare fopen

``` c
FILE *f = fopen("data.txt", "r");
if (f == NULL) {
    perror("data.txt");   // data.txt: No such file or directory
    return 1;
}
```

- File inesistente, o permessi mancanti
- `perror`: messaggio dettagliato, su `stderr`
- Python: eccezione `FileNotFoundError`
- C: nessuna eccezione, solo `NULL`... *da controllare*

---

# ⭐ Modalità di apertura

| Modo | Significato | Se il file... |
|---|---|---|
| `"r"` | lettura | deve esistere |
| `"w"` | scrittura | viene creato, o *svuotato* |
| `"a"` | aggiunta in fondo | viene creato se manca |

- Gli stessi modi di Python
- ⚠️ `"w"` cancella il contenuto precedente

---

# ⭐ Leggere righe

``` c
char line[200];
while (fgets(line, sizeof(line), f) != NULL) {
    printf("%s", line);   // line already ends with '\n'
}
```

- `fgets` restituisce `NULL` a fine file
- Python: `for line in f:`
- Riga più lunga del buffer: letta *a pezzi*

---

# ⚠️ Il ciclo con feof

``` c
while (!feof(f)) {            // ⚠️
    fgets(line, sizeof(line), f);
    printf("%s", line);
}
```

- File con righe `a` e `b`: stampa `a`, `b`, `b`!
- `feof` è vero solo *dopo* una lettura fallita
- Soluzione: testare il *valore restituito* da `fgets`
- ❓ Perché la `b` è duplicata?

---

# 🧪 Numeri da file

``` c
int v, total = 0, count = 0;
while (fscanf(f, "%d", &v) == 1) {
    total += v;
    count++;
}
printf("%d values, sum %d\n", count, total);
```

- `fscanf`: come `scanf`, ma da qualsiasi stream
- Stesso ciclo visto con `scanf` e la sentinella

---

# ⭐ Scrivere su file

``` c
FILE *out = fopen("squares.txt", "w");
for (int i = 1; i <= 5; i++) {
    fprintf(out, "%d %d\n", i, i * i);
}
fclose(out);
```

- `fprintf`: come `printf`, ma su un file
- Python: `print(i, i * i, file=out)`
- `fputs(str, out)`: scrive una stringa

---

# ⚠️ Non dimenticare fclose

- Le scritture sono *bufferizzate*: restano in memoria
- Senza `fclose` il file può risultare *incompleto*
- Un'uscita anomala del programma può far perdere dati
- A ogni `fopen` deve corrispondere un `fclose`
- Python: `with` lo fa in automatico

---

# ⭐ sscanf: scanf da stringa

``` c
char name[50];
int age;
if (sscanf(line, "%49[^,],%d", name, &age) == 2) {
    printf("%s is %d\n", name, age);
}
```

- Interpreta una *stringa*, come `scanf` con l'input
- `%[^,]`: legge fino alla virgola
- Restituisce il numero di campi letti
- Python: `name, age = line.split(",")`

---

# 🧪 Copia di un file

``` c
int main(int argc, char *argv[]) {
    if (argc != 3) {
        fprintf(stderr, "Usage: %s src dst\n", argv[0]);
        return 1;
    }
    FILE *in = fopen(argv[1], "r"), *out = fopen(argv[2], "w");
    if (in == NULL || out == NULL) {
        perror("copy");
        return 1;
    }
    int c;
    while ((c = fgetc(in)) != EOF) {
        fputc(c, out);
    }
    fclose(in); fclose(out);
    return 0;
}
```

---

# Progetti con più file

---

![](http://fondinfo.github.io/images/oop/modules.png)
# 💡 Dividere in moduli

- Programmi grandi: *molti file*, ciascuno con il suo compito
- Vantaggi
    - Leggibilità e riuso
    - Compilazione *separata*
    - Lavoro di squadra
- Python: `import mylib`
- C: *header* (`.h`) + *implementazione* (`.c`)

---

# ⭐ Un progetto di tre file

| File | Contenuto |
|---|---|
| `mylib.h` | *interfaccia*: dichiarazioni (prototipi) |
| `mylib.c` | *implementazione*: definizioni |
| `main.c` | programma che *usa* la libreria |

- Chi usa la libreria vede solo `mylib.h`
- `mylib.c` può cambiare, senza toccare `main.c`

---

# ⭐ mylib.h

``` c
#ifndef MYLIB_H
#define MYLIB_H

int square(int x);
double average(const int v[], int n);

#endif
```

- Solo *dichiarazioni*: nomi e tipi
- Le tre righe `#ifndef`... `#endif`: *include guard*, tra poche slide

---

# ⭐ mylib.c

``` c
#include "mylib.h"

int square(int x) {
    return x * x;
}

double average(const int v[], int n) {
    int total = 0;
    for (int i = 0; i < n; i++) {
        total += v[i];
    }
    return (double) total / n;
}
```

- `"mylib.h"` tra virgolette: file del *progetto*
- `<stdio.h>` tra parentesi angolari: librerie di *sistema*

---

# ⭐ main.c

``` c
#include <stdio.h>
#include "mylib.h"

int main(void) {
    int v[] = {3, 7, 5, 6};
    printf("%d\n", square(7));
    printf("%.2f\n", average(v, 4));
    return 0;
}
```

- Basta includere l'header per usare le funzioni
- Python: `from mylib import square`

---

# ⭐ Compilare più file

``` sh
gcc -std=c11 -Wall -Wextra -pedantic main.c mylib.c -o prog
./prog
```

- Tutti i `.c` sulla stessa riga
- Un solo `main` in tutto il progetto
- I `.h` *non* si compilano: sono inclusi dal preprocessore

---

# 💡 Compilazione separata

``` sh
gcc -Wall -c main.c           # main.o
gcc -Wall -c mylib.c          # mylib.o
gcc main.o mylib.o -o prog    # linking
```

- `.o`: *file oggetto*, codice macchina non ancora collegato
- **Linker**: unisce i `.o` (e le librerie) in un eseguibile
- Cambia solo `mylib.c`? Si ricompila solo quello

![](http://fondinfo.github.io/images/comp/build.svg)

---

# 🧪 Errori del linker

``` txt
main.c:(.text+0x54): undefined reference to `square'
collect2: error: ld returned 1 exit status
```

- **`undefined reference`**: dichiarata, ma *mai definita*
    - Es. dimenticato `mylib.c` nella compilazione

``` txt
multiple definition of `square'
```

- **`multiple definition`**: definita due volte
- ❓ Errore del compilatore o del linker? Quando compare?

---

# 💡 Dichiarazione e definizione

- **Dichiarazione**: *cosa* esiste, nome e tipi
    - `int square(int x);`
- **Definizione**: *come* funziona, il corpo
    - `int square(int x) { return x * x; }`
- Nell'header: *solo dichiarazioni*
- Nel `.c`: le definizioni
- ⚠️ Definizioni in un header incluso da più file → `multiple definition`

---

# ⭐ Include guard

``` c
#ifndef MYLIB_H
#define MYLIB_H

/* declarations */

#endif
```

- Un header può essere incluso *più volte* (anche indirettamente)
- Prototipi ripetuti: innocui
- Ma `struct`, `enum`, `typedef` ripetuti → `redefinition of ...`
- **Guard**: il contenuto si legge *una sola volta*
- Convenzione: nome del file, in maiuscolo

---

# ⭐ static: nomi privati

``` c
static int calls = 0;   // visible only in mylib.c

int square(int x) {
    calls++;
    return x * x;
}

int square_calls(void) {   // getter
    return calls;
}
```

- `static` fuori da funzioni: nome *privato del file*
    - Come `_x` nelle classi Python
- Variabili globali non `static`: da evitare

---

# ⭐ L'header come contratto

``` c
/* Precondition: n > 0
 * Postcondition: returns the mean of v[0..n-1] */
double average(const int v[], int n);
```

- `const int v[]`: la funzione *non modifica* l'array
- Contratto documentato nell'header
- Verificato con `assert` nel `.c`

``` c
#include <assert.h>

assert(n > 0);
```

---

# 🧪 Collaudo della libreria

``` c
#include <assert.h>
#include <math.h>
#include "mylib.h"

int main(void) {
    int v[] = {3, 7, 5, 6};
    assert(square(7) == 49);
    assert(fabs(average(v, 4) - 5.25) < 0.001);
    return 0;
}
```

``` sh
gcc -Wall test_mylib.c mylib.c -o test && ./test
```

- Nessun output: test *superati*
- Violazione: il programma si ferma con un messaggio

---

# ⭐ Makefile

``` make
prog: main.o mylib.o
    gcc main.o mylib.o -o prog

main.o: main.c mylib.h
    gcc -Wall -c main.c

mylib.o: mylib.c mylib.h
    gcc -Wall -c mylib.c
```

- Regola: `target: dipendenze`, poi il comando, dopo un **TAB**
- `make`: ricompila solo ciò che è *più vecchio* delle dipendenze
- ❓ Se modifico `mylib.h`, quali file vengono ricompilati?

---

# 🧪 Makefile con variabili

``` make
CC = gcc
CFLAGS = -std=c11 -Wall -Wextra -pedantic

prog: main.o mylib.o
    $(CC) main.o mylib.o -o prog

main.o: main.c mylib.h
    $(CC) $(CFLAGS) -c main.c

mylib.o: mylib.c mylib.h
    $(CC) $(CFLAGS) -c mylib.c

clean:
    rm -f *.o prog
```

- `make clean`: elimina i file generati

---

# ⚠️ Librerie da collegare

``` sh
gcc main.c -o prog -lm
```

``` txt
undefined reference to `pow'
```

- Alcune librerie standard (`<math.h>`) vanno *collegate*
- Opzione **`-lm`**, dopo i file sorgente
- Anche questo è un errore del *linker*

---

# 💡 Riepilogo

- **Stream**: `stdin`, `stdout`, `stderr`; redirezione e pipe
- **File**: `fopen` (e `NULL`!), `fgets`, `fscanf`, `fprintf`, `fclose`
- Fine input: valore restituito, *mai* `feof` nel ciclo
- **Moduli**: `.h` per dichiarare, `.c` per definire
- Include guard, `static`, header come contratto
- Compilazione separata, linker, `make`

---

# 🏊 Esercizi

---

# Numerare le righe

- Leggere lo `stdin`, riga per riga
- Stampare ogni riga preceduta dal suo numero
- Provare con redirezione e con pipe
    - `./numbered < in.txt`
    - `cat in.txt | ./numbered`
- Errori e avvisi: su `stderr`

---

# Contare righe, parole, caratteri

- Il nome del file è in `argv[1]`
- Contare righe, parole e caratteri
- Se il file non si apre: `perror`, codice di uscita `1`
- Confrontare i risultati con il comando `wc`

---

# Filtro di caratteri

- Programma che legge `stdin` e scrive `stdout`
- Rimuove tutte le vocali
- Lascia invariato il resto, inclusi gli a capo
- Attenzione al tipo della variabile che riceve `getchar()`
- Provare con una pipe: `./novowels < in.txt | sort`

---

# Somma e media da file

- Il file ha un numero per riga; nome in `argv[1]`
- Con `fscanf`, calcolare
    - Quanti valori, somma, media, massimo
- File mancante: messaggio su `stderr`
- File vuoto: niente divisione per zero!

---

# Copia con filtro

- Programma `./copy src dst`
- Copia il file `src`, convertendo tutto in maiuscolo
- Se `dst` esiste già, *non* sovrascriverlo
    - Provare ad aprirlo in lettura
- Controllare tutti i possibili errori

---

# Note da riga di comando

- Programma `./note "buy milk"`
    - Aggiunge una riga al file `notes.txt`
    - Modo di apertura `"a"`
- Senza argomenti: stampa tutte le note, numerate
- Se `notes.txt` non esiste ancora, non è un errore

---

# Massimo da CSV

- File con righe nel formato `nome,punteggio`
- Leggere con `fgets` e interpretare con `sscanf`
- Stampare nome e punteggio massimo
- Righe malformate: ignorate, con avviso su `stderr`
- Esempio di riga: `Anna,31`

---

# Libreria matematica

- File `mymath.h`, `mymath.c`, `main.c`
- Funzioni
    - `int gcd(int a, int b)`: massimo comun divisore
    - `int is_prime(int n)`: `1` se primo, `0` altrimenti
- `main` legge interi da `stdin`, stampa i risultati
- Include guard nell'header
- Compilare con `gcc -Wall main.c mymath.c -o prog`

---

# Libreria di stringhe

- File `strutil.h`, `strutil.c`
- Riutilizzare esercizi del capitolo precedente
    - `reverse`, `is_palindrome`, `count_vowels`
- Documentare pre- e postcondizioni nell'header
- Scrivere `test_strutil.c`, con `assert`
- Compilare ed eseguire i test

---

# Makefile del progetto

- Scrivere un `Makefile` per il progetto di stringhe
    - Un file oggetto per ciascun `.c`
    - Variabili `CC` e `CFLAGS`
- Target `clean`: elimina i file generati
- Target `test`: compila ed esegue i test
- Modificare solo `strutil.c`, poi eseguire `make`
    - Quali file vengono ricompilati?
