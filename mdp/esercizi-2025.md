![](https://fondinfo.github.io/images/dev/geek-girl.svg)
# Esercizi 2025
## Introduzione alla programmazione

---

# Esercitazione 1 (2025-09-29)

---

![large](https://fondinfo.github.io/images/algo/holy-grail.jpg)
# 1.1 Lancelot

- Porre una domanda all'utente:
    - `"What is your name?"`
- Se la risposta è `"Lancelot"`, stampare:
    - `"Right. Off you go."`
- Altrimenti, stampare:
    - `"Down into the Gorge of Ethernal Peril!"`

---

![](https://fondinfo.github.io/images/misc/slope.svg) y = m·x + b
# 1.2 Pendenza tra due punti

- Chiedere all'utente le coordinate di due punti sul piano cartesiano
    - `x1, y1, x2, y2`
- Calcolare la pendenza `m` della retta passante
    - *Δy / Δx*
- Considerare separatamente il caso limite di retta verticale

---

![](https://fondinfo.github.io/images/draw/random-circles.svg)
# 1.3 Cerchi casuali

- Chiedere all'utente un numero `n`
- In un canvas 500×500, disegnare `n` cerchi
    - Tutti con raggio di 50 pixel
    - Ciascuno con posizione casuale e colore casuale
    - Con centro all'interno del canvas

>

Cominciare a disegnare un solo cerchio, in posizione casuale

---

![](https://fondinfo.github.io/images/draw/shadowed-squares.svg)
# 1.4 Quadrati con ombra

- Chiedere all'utente un numero `n`
- In un canvas 500×500, disegnare `n` quadrati
    - Tutti di lato 50
    - Ciascuno con posizione e colore casuale
    - Ciascuno con un ombra grigia spostata a destra e in basso di 5 pixel

>

Fare in modo che i quadrati e le ombre siano completamente all'interno nel canvas

---

![](https://fondinfo.github.io/images/draw/shadowed-rects.svg)
# 1.5 Rettangoli con ombra

- Chiedere all'utente un numero `n`
- Disegnare `n` rettangoli
    - Ciascuno con dimensione casuale: base e altezza *∈ [100, 199]*
    - Posizione casuale, tenendo conto della dimensione
    - Colore casuale
    - Ombra grigia spostata a destra e in basso di 5 pixel

>

Fare in modo che i rettangoli e le ombre siano tutti all'interno nel canvas

---

![](https://fondinfo.github.io/images/misc/quadratic-eq.svg) ![](https://fondinfo.github.io/images/misc/quadratic-formula.svg)
# 1.6 Equazione di secondo grado

- Chiedere all'utente i tre coefficienti `a, b, c` di una equazione di secondo grado
    - `ax² + bx + c = 0`
- Comunicare all'utente che tipo di soluzioni presenta l'equazione
    - Due soluzioni reali
    - Un'unica soluzione reale
    - Nessuna soluzione reale

>

Valutare `Δ = b² - 4·a·c`. Non è richiesto il valore delle soluzioni.

---

![](https://fondinfo.github.io/images/misc/quadratic-eq.svg) ![](https://fondinfo.github.io/images/misc/quadratic-formula.svg)
# 1.7 Equazione di 2° grado, con ciclo

- Riprendere l'esercizio precedente
- In caso di soluzioni reali, mostrare all'utente il loro valore
- Chiedere infine all'utente se vuole valutare altre equazioni
    - Eventualmente, ripetere tutto dall'inizio (`while`)

---

# 1.8 Divisori

- Chiedere all'utente un numero `n`
- Mostrare tutti i divisori di `n`

>

`n` è divisibile per `m` se `n % m == 0`

---

![large](https://fondinfo.github.io/images/draw/center-target.svg)
# 1.9 Bersaglio al centro

- Su un canvas 500×500, disegnare vari cerchi casuali
    - Tutti con raggio 20
    - Posizione e colore casuali
    - Il numero di cerchi non è noto
- Il disegno termina quando…
    - Il centro dell'ultimo cerchio disegnato è vicino al centro del canvas
    - Distanza minore di 20

>

Usare il teorema di Pitagora per calcolare la distanza tra due punti
<br>
<https://fondinfo.github.io/images/misc/slope.svg>

---

# Esercitazione 2 (2025-10-06)

---

![](https://fondinfo.github.io/images/misc/greek-pi.png)
# 2.1 Funzione, circonferenza

- Definire una funzione `circumference`
    - Parametro: raggio come `float`
    - Risultato: circonferenza come `float` (*2·π·r*)
    - Generare un `ValueError` in caso di raggio negativo
- Invocare la funzione dalla shell interattiva
    - Controllare il risultato, fornendo raggio 10
- Aggiungere poi al programma una funzione `main`
    - Chiedere all'utente la misura del raggio
    - Poi chiamare `circumference` con questo parametro
    - Infine mostrare all'utente il risultato

>

Tenere le operazioni di I/O fuori dalla funzione `circumference`

---

![](https://fondinfo.github.io/images/misc/characters.png)
# 2.2 Caratteri alfabetici

- Definire una funzione `all_alpha` (*predicato*)
    - Parametro: un testo
    - Risultato: un booleano
    - I caratteri del testo sono tutti alfabetici?
    - Cioè, tutti in [A-Z] o [a-z]?
- Aggiungere al programma una funzione `main`
    - Chiedere all'utente una riga di testo
    - Verificare il testo con `all_alpha` e mostrare il risultato

---

![](https://fondinfo.github.io/images/draw/n-points.svg)
# 2.3 Punti allineati

- Chiedere all'utente il numero *n* di punti da visualizzare
- Chiedere le coordinate del primo e dell'ultimo punto
- Mostrare *n* punti su canvas 400×400
    - Punti allineati ed equispaziati
    - Ciascun punto è un cerchietto di raggio 5

---

![](https://fondinfo.github.io/images/draw/n-points.svg)
# 2.4 Punti colorati

- Riprendere l'esercizio precedente
- Chiedere all'utente i colori del primo e dell'ultimo punto
- Cambiare il colore gradualmente da un punto all'altro
    - Variare ciascuna componente di colore
    - Dal livello iniziale fino a quello finale
- Per esempio: primo punto rosso saturo, ultimo punto blu saturo

---

![](https://fondinfo.github.io/images/games/play-pause.svg)
# 2.5 Pallina in pausa

- Partire dall'animazione della pallina vista a lezione
    - Direzione iniziale, verso destra di 2 px
    - Senza rimbalzi
    - Partire da *(200, 200)* in un canvas *400×400*
- Al click del mouse, la pallina si mette in pausa
    - Resta ferma per 30 frame
    - Poi riparte automaticamente
    - Scartare il click, quando la pallina è già in pausa

>

Usare una variabile contatore globale, `countdown`
<br>
Conteggio alla rovescia, da 30 a 0

---

![](https://fondinfo.github.io/images/games/anim-right.svg)
# 2.6 Svolta casuale

- Partire dall'animazione della pallina vista a lezione
    - Direzione iniziale, verso destra di 2 px
    - Senza rimbalzi
    - Partire da *(200, 200)* in un canvas *400×400*
- Aggiungere un cambio di direzione casuale
    - Nuova direzione: alto, basso, destra, o sinistra
- Cambiare direzione solo in certi punti
    - Quando `x` e `y` sono entrambe multiple di 20

---

![](https://fondinfo.github.io/images/fun/sin-cos.png)
# 2.7 Oscillazione

- Partire dall'animazione della pallina vista a lezione
    - Direzione iniziale, verso destra di 2 px
    - Senza rimbalzi
    - Partire da *(200, 200)* in un canvas *400×400*
- Aggiungere una oscillazione in verticale
    - Oscillazione con *ampiezza* 10 px e *periodo* 80 px
    - In base alla formula: *y = y₀ + a · sin(x · 2π/p)*
- Inoltre, quando la pallina esce completamente dal bordo destro
    - Riparte dal bordo sinistro del canvas

---

![](https://raw.githubusercontent.com/fondinfo/fondinfo/master/sprites.png)
# 2.8 Scelta sprite

- Continuare l'esercizio 2.7
- Disegnare un fantasma anzichè una pallina
    - Ritagliare l'immagine da `sprites.png`
    - [`g2d.draw_image`](https://github.com/fondinfo/fondinfo#images-and-sounds)
- Casualmente, il fantasma cambia sprite
    - Solo in posizioni `x` multiple di 20
    - Probabilità ⅓ di cambiare stato
    - Se è visibile diventa invisibile e viceversa
    - Mantiene lo stesso sprite fino al prossimo cambiamento casuale

>

Usare una variabile globale booleana, `visible`

---

![](https://fondinfo.github.io/images/misc/characters.png)
# 2.9 Gruppi di lettere

- Definire una funzione `count_groups`
- Parametro: un testo
- Risultato: due valori
    - Quante lettere del testo sono comprese nel gruppo `A-M`
    - Quante lettere del testo sono comprese nel gruppo `N-Z`
    - Senza distinguere maiuscole e minuscole
- Definire una funzione `main`
    - Chiamare `count_groups` con un testo fornito dall'utente e mostrare i risultati
    - Ripetere queste operazioni in un ciclo
    - Finchè l'utente non fornisce una riga vuota, che non deve essere elaborata

---

# Esercitazione 3 (2025-10-13)

---

![](https://fondinfo.github.io/images/algo/space-diagonal.svg)
# 3.1 Parallelepipedo

- Classe che modella un parallelepipedo
    - Campi privati per *largezza*, *profondità* e *altezza* ($l, w, h$)
    - Metodo per calcolare il volume
    - Metodo per calcolare la diagonale
- Nella funzione `main`
    - Chiedere all'utente le dimensioni del parallelepipedo
    - Passare queste dimensioni al costruttore, come parametri
    - Mostrare volume e diagonale del parallelepipedo creato

>

$ V = l · w · h$
<br>
$z^2 = l^2 + w^2; d^2 = z^2 + h^2 = l^2 + w^2 + h^2$

---

![](https://fondinfo.github.io/images/comp/orders.svg)
# 3.2 Modello esponenziale

- Creare una classe delle curve esponenziali
    - $y = a\cdot e^{b x} + c$
    - Coefficienti $a, b, c$ come campi, da inizializzare nel costruttore
- Metodo `estimate`, con parametro $x$
    - Risultato: valore della funzione in $x$
- Nella funzione `main`
    - Istanziare un *singolo* modello esponenziale con coefficienti forniti dall'utente
    - Valutare il modello, chiamando `estimate`, in diversi punti $x$ forniti iterativamente dall'utente
    - Terminare il ciclo quando l'utente fornisce una stringa vuota

```
from math import e, exp
```

---

![](https://fondinfo.github.io/images/games/anim-bounce.svg)
# 3.3 Pallina colorata

- Partire dalla classe `Ball` vista a lezione
- Aggiungere un campo per il colore
    - Scelto casualmente nel costruttore
    - Al momento del rimbalzo, scegliere un nuovo colore casuale
- Aggiungere un metodo *getter* `color`, per ottenere il colore
    - Similmente a `pos`
- Nel `tick`, disegnare un quadrato colorato al posto di ogni pallina
- Mostrare l'animazione di tre palline (quadrati)

---

![](https://fondinfo.github.io/images/games/anim-right.svg)
# 3.4 Mai indietro

- Riprendere l'esercizio 2.6
- Definire una classe `RandomWalker`
    - Incapsulare il comportamento del personaggio
    - Arrotondare $x$ e $y$ iniziali a un multiplo di 2, per difetto
    - Direzione iniziale, verso destra di 2 px
- Nella scelta della direzione casuale…
    - Escludere la direzione opposta a quella attuale
    - Cioè, la pallina non può tornare direttamente indietro

>

Consiglio: usare come bozza iniziale la classe `Ball`

---

![](https://fondinfo.github.io/images/draw/green-squares.svg)
# 3.5 Sequenza di quadrati

- Chiedere all'utente un numero `n`
- Su un canvas 500×500, disegnare `n` quadrati
    - Quadrati con lato decrescente
    - L'ultimo ha lato `500/n`
    - Tutti allineati in alto e a sinistra
- Far variare il colore dei quadrati
    - Dal nero del quadrato più grande
    - Fino al verde del quadrato più piccolo

>

Determinare automaticamente le variazioni migliori per lato e colore, prima di iniziare il ciclo

---

![](https://fondinfo.github.io/images/draw/hflip-squares.svg)
# 3.6 Quadrati allineati a destra

- Ripetere l'esercizio 3.5, però…
- Allineare i quadrati in alto e a destra (anzichè sinistra)
- Lasciare attorno al disegno un margine bianco di 10 pixel
    - Da ogni bordo del canvas

---

![](https://fondinfo.github.io/images/misc/characters.png)
# 3.7 Codici pari e dispari

- Data una stringa inserita dall'utente
- Contare le minuscole con codice Unicode dispari
    - `a, c, e…`
- Contare le minuscole con codice Unicode pari
    - `b, d, f…`
- Es. `"Python"`: 3 minuscole con codice pari, 2 con codice dispari

---

![](https://fondinfo.github.io/images/algo/guard.png)
# 3.8 Sentinella

- Riprendere l'esercizio precedente
- Continuare il conteggio su più righe di testo inserite dall'utente
- Il programma si interrompe quando l'utente inserisce una riga vuota
- Mostrare i due conteggi complessivi
    - Minuscole con codice dispari
    - Minuscole con codice pari

---

![](https://raw.githubusercontent.com/fondinfo/fondinfo/master/sprites.png)
# 3.9 Oscillazione e sprite

- Riprendere gli esercizi 2.7 e 2.8
- Definire una classe `OscillatingGhost`
    - Incapsulare il comportamento del personaggio
    - Aggiungere campo per visibilità
- Aggiungere alla classe un metodo *getter* `size`
    - Restituisce tupla *(w, h)* : larghezza e altezza
- Aggiungere alla classe un metodo *getter* `sprite`
    - Restituisce tupla *(x, y)* : posizione dello sprite in `sprites.png`
- In `tick`, usare questi metodi per disegnare

---

# Esercitazione 4 (2025-10-20)

---

![](https://fondinfo.github.io/images/misc/gold-price.svg)
# 4.1 Sopra e sotto la media

- Chiedere all'utente una sequenza di interi
    - Sequenza terminata da $0$ (*sentinella*)
- Calcolare e mostrare il valore medio
- Elencare i valori sotto alla media
- Elencare i valori sopra (o uguali) alla media

>

Aggiungere ciascun valore a una lista inizialmente vuota, con `append`

---

![](https://fondinfo.github.io/images/draw/n2-circles.svg)
# 4.2 Figure affiancate

- Definire una funzione `draw_figure`
    - Parametri per: centro, raggio, $n$
    - Disegnare una figura di $n$ cerchi concentrici
    - Il raggio più interno è $\frac{1}{n}$ rispetto al più esterno
    - Colorare i cerchi in grigio: dal nero esterno al bianco interno
- In `main`:
    - Chiedere all'utente un numero $n$
    - In un canvas $500×500$, disegnare $n$ figure uguali affiancate

---

![](https://fondinfo.github.io/images/oop/personal-data.png)
# 4.3 Dati anagrafici

- Creare classe `Person`: dati anagrafici di una persona
    - Nome, cognome: testo
    - Data di nascita: anno, mese, giorno
- Costruttore con parametri per tutti i campi
- Metodo `age` per calcolare l'età in anni
    - Parametro/i per data attuale: *non è un campo!*
    - Controllare se è passato il giorno del compleanno
- Metodo `describe` per avere in un testo: nome, cognome ed età
- Nella funzione `main`
    - Utente fornisce dati per istanziare *tre* oggetti persona
    - Utente fornisce poi varie date attuali
    - Per ciascuna data, decrivere ciascuna persona, se maggiorenne
    - Il programma termina all'inserimento di una riga vuota

---

![](https://fondinfo.github.io/images/draw/segments-4.svg)
# 4.4 Linea spezzata

- Funzione `randline`
    - Prende le coordinate $(x, y)$ di un punto $p_1$
    - Genera un punto casuale $p_2$
    - Distanza $100$ tra $p_1$ e $p_2$, ma angolo casuale
    - Disegna una linea da $p_1$ a $p_2$
    - Restituisce $p_2$ come risultato
- In `main`
    - Chiedere all'utente un numero $n$
    - A partire dal centro di un canvas $400×400$…
    - Disegnare una linea spezzata di $n$ segmenti
    - Sfruttare la funzione `randline`

---

![](https://fondinfo.github.io/images/misc/letters.png)
# 4.5 Stringa casuale

- Definire una funzione `add_letter`
    - Stringa come parametro
    - Restituisce la stessa stringa…
    - Ma con una lettera minuscola casuale aggiunta in fondo
- Nella funzione `main`
    - Chiedere all'utente un numero $n$
    - Chiamare ripetutamente la funzione `add_letter`
    - Per generare una stringa casuale di $n$ lettere

>

`chr/ord`, oppure `string.ascii_lowercase`

---

![](https://fondinfo.github.io/images/games/ghost.svg)
# 4.6 Fantasma a casa

- Modificare la classe `Ghost` dell'esempio “*bounce*”
- Posizione iniziale
    - Nel costruttore, scelta casualmente, attorno al centro del canvas
    - Distanza $100$ dal centro, con angolo casuale
    - Memorizzata in opportuni campi
- Alla pressione del tasto “`h`”, ogni fantasma ritorna alla sua posizione iniziale

>

<https://fondinfo.github.io/play/?c07_bounce.py>

---

![](http://fondinfo.github.io/images/games/viewport.svg)
# 4.7 Focus su un personaggio

- Risolvere l'esercizio “*Scroll della vista*” *(✶)*
- Inoltre, spostare automaticamente la vista
    - Mantentere la vista centrata sulla *prima pallina* della lista, quando possibile
    - Però, la vista non esce mai dai limiti dall'*arena*

>

(✶) <https://fondinfo.github.io/slides/p32-relazioni.html#/24>

---

![](https://fondinfo.github.io/images/games/ghosts-goblins.png)
# 4.8 Arthur - Salti [P1]

- Gioco “*Ghosts 'N Goblins*”
- Creare personaggio **`Arthur`** *(✶)*
- Si può muovere a sinistra o a desta, sul fondo del canvas
- Alla pressione della freccia in alto (p.es.), salta
- Poi ricade sul fondo, per forza di gravità
- Istanziare il personaggio in un oggetto `Arena`
- Variare lo sprite in base all'azione

>

(✶) Tutti i personaggi sono sottoclassi di `Actor`
<br>
Partire da `Turtle` dell'esempio “`bounce`”
<br>
Sprite: <https://github.com/fondinfo/sprites>
<br>
Gioco: <https://archive.org/details/GNG_DOS>

---

![](https://fondinfo.github.io/images/games/ghosts-goblins.png)
# 4.9 Zombie [P1]

- Creare personaggio **`Zombie`**
- Inizializzazione
    - Riceve parametro per direzione: *destra/sinistra*
    - Sceglie distanza casuale da percorrere $\in [150, 300]$
- Comportamento
    1. Sorge dal terreno in alcuni frame
    2. Si sposta sempre nella stessa direzione
    3. Sprofonda nel terreno in alcuni frame
- Uno *zombie* può essere generato nella funzione `tick`
    - In ogni frame, con probabilità $\frac{1}{500}$
    - A distanza non superiore a $200$ da *Arthur*
    - Si sposta in direzione di *Arthur*

>

Regolare i valori numerici a piacere

---

# Esercitazione 5 (2025-10-27)

---

![](https://fondinfo.github.io/images/games/ghosts-goblins.png)
# 5.1 Piattaforme [P1]

- Creare personaggio **`Platform`**
    - Immobile e già parte dello sfondo
    - Restituisce `None` nel metodo `sprite`
    - Gli altri personaggi collidono e atterrano sulle piattaforme
- Creare personaggio **`Gravestone`**
    - Immobile e già parte dello sfondo
    - Restituisce `None` nel metodo `sprite`
    - *Arthur* non può attraversarle, ma ci può salire sopra
    - Gli *zombie* le attraversano

---

![](https://fondinfo.github.io/images/games/ghosts-goblins.png)
# 5.2 Fiaccole [P1]

- *Arthur* può lanciare delle *fiaccole*
    - Verso destra, o verso sinistra
    - Dopo aver lanciato una fiaccola…
    - Aspetta 10 frame prima di poter lanciarne un'altra
- Creare personaggio **`Torch`**
    - Cade per forza di gravità
    - Uccide il primo *zombie* che tocca
    - Se colpisce qualcosa, sparisce
    - Se finisce a terra, genera una *fiammata*
- Creare personaggio **`Flame`**
    - Immobile, sparisce dopo 60 frame
    - Uccide tutti gli *zombie* che tocca

---

# Esercitazione 6 (2025-11-03)

---

![](https://fondinfo.github.io/images/misc/troll-key.png)
# 6.1 Maiuscole tra asterischi

- Scrivere una funzione `shout` che:
    - Riceve in input una stringa di testo
    - Produce in output la stesso testo, ma...
    - Trasforma in maiuscolo tutto il testo compreso tra asterischi
- Es. “`I want *this text* to be uppercase`”
    - → “`I want THIS TEXT to be uppercase`”
- Da una funzione `main`, applicare la funzione `shout` su una stringa inserita dall'utente

>

Segnare in un `bool` se si è incontrato un asterisco iniziale, ma non ancora un asterisco finale

---

# 6.2 Lettere iniziali uguali

- Scrivere una funzione `len_common_prefix`
    - Parametri: due stringhe da confrontare
    - Risultato: numero di lettere iniziali uguali tra le due stringhe
- Scrivere una funzione `main`
    - Chiedere all'utente due stringhe di testo
    - Invocare `len_common_prefix` sulle due stringhe
    - Mostrare all'utente il risultato
- Es. `“carta”` vs. `“carota”` → 3 (`“car”`)

---

![](https://fondinfo.github.io/images/algo/red-dice.svg)
# 6.3 Risultati casuali

- Simulare `n` lanci di una coppia di dadi
    - `n` scelto dall'utente
- Contare quante volte si presenta ciascun risultato
    - Risultati possibili: da 2 a 12
    - Somma dei due dadi
    - Quante volte è uscito il 2? Quante il 3? … Quante il 12?

>

Per conteggiare i vari risultati, usare una lista di 13 interi (al massimo)

---

# 6.4 Quadrati sovrapposti

- Disegnare dei quadrati casuali su un canvas 400×400
    - Posizione e colore casuale
    - Tutti di lato 20
- Il numero dei quadrati non è fissato
    - Il programma termina quando…
    - L'ultimo quadrato interseca uno dei precedenti

>

Memorizzare in una lista le posizioni dei quadrati

---

![](https://fondinfo.github.io/images/misc/histogram-rot.svg)
# 6.5 Istogramma in orizzontale

- Chiedere all'utente una sequenza di valori (positivi)
    - La sequenza termina all'inserimento di un valore negativo (*sentinella*)
- Mostrare un istogramma, in un canvas 500×500
    - Lunghezza di ciascuna barra proporzionale al valore corrispondente
    - La barra più lunga occupa tutto lo spazio disponibile
    - L'altezza del canvas è divisa equamente tra le barre

>

Memorizzare i valori in una lista

---

![](https://fondinfo.github.io/images/misc/clamp.svg)
# 6.6 Clamp su lista

- Definire una funzione con due parametri
    - Una lista di `float`
    - Un limite superiore fissato, come `float`
    - Senza risultato esplicito: lista modificata *in place*
- Per ciascun valore nella lista
    - Se il valore supera il limite…
    - Esso viene troncato, cioè sostituito con il limite stesso
- Per esempio. con limite fissato a 3
    - `[2, 3, 5, 1, 4]` → `[2, 3, 3, 1, 3]`

---

# 6.7 Lista di cifre

- Definire una funzione `digits`
    - Parametro: numero intero positivo
    - Risultato: lista di `int`
    - Cifre che compongono il numero, dalle unità in su
- Es. `6543 → [3, 4, 5, 6]`

---

![](https://fondinfo.github.io/images/games/ghosts-goblins.png)
# 6.8 Scale [P1]

- Creare personaggio **`Ladder`**
    - Immobile e già parte dello sfondo
    - Restituisce `None` nel metodo `sprite`
- *Arthur* può arrampicarsi sulla *scala*
    - Mentre è sulla *scala* non salta e non spara
    - Può muoversi solo in verticale

---

![](https://fondinfo.github.io/images/games/ghosts-goblins.png)
# 6.9 Piante [P1]

- Creare personaggio **`Plant`**
    - Stazionario
    - In momenti casuali, spara un *occhio* in direzione di *Arthur*
- Creare personaggio **`Eyeball`**
    - Non devia mai dalla sua direzione originale
    - Se colpisce *Arthur*, lo uccide

---

# Esercitazione 7 (2025-11-10)

---

![](https://fondinfo.github.io/images/fun/matryoshka.png)
# 7.1 Potenze con ricorsione

- Definire una funzione ricorsiva `recursive_pow` per calcolare la potenza intera positiva di un numero
- Per qualsiasi numero $x$, $x^0 = 1$
- La potenza $n$-esima di un numero $x$ si può calcolare come:
    - Prodotto tra $x$ e la potenza $n-1$ di $x$ (*ricorsione*)
- In una funzione `main`
    - Chiedere i dati all'utente
    - Mostrare il risultato

>

Saranno accettate esclusivamente le soluzioni ricorsive

---

![](https://fondinfo.github.io/images/misc/characters.png)
# 7.2 Carattere casuale

- Definire funzione `randchar`
- Due parametri di tipo carattere
    - Estremi dell'intervallo di caratteri possibili
    - Estremi *inclusi* (l'intervallo è *chiuso*)
- Risultato: carattere casuale scelto dall'intervallo dato

---

# 7.3 Matrice casuale

- Chiedere all'utente le dimensioni $w, h$ di una matrice
- Riempire con una *comprehension* una lista
    - Con $w·h$ lettere minuscole casuali, con possibili ripetizioni
- Mostrare a console la lista come una matrice, riga per riga, in formato *CSV*
    - Caratteri separati da virgola (ma senza virgola a fine riga)
- In un ciclo
    - Chiedere un carattere all'utente
    - Contare quante volte è presente ovunque nella matrice
    - Contare quante volte è presente nelle celle di bordo <br> (celle in prima o ultima colonna, o riga)

``` txt
a,c,r,a
r,r,t,a
t,r,e,f
```

---

![](https://fondinfo.github.io/images/draw/rec-circles.svg)
# 7.4 Cerchi ricorsivi

- Definire funzione `rec_circles`
    - Parametri: centro $p$ e raggio $r$
- Se $r \leq 5$, non disegna niente
- Altrimenti
    - Disegna il cerchio specificato
    - Disegna ricorsivamente altri 4 cerchi
    - Spostati in orizzontale e in verticale di $\pm r$
    - Con raggio ridotto al 42% ($\sqrt{2}-1$)

>

Saranno accettate esclusivamente le soluzioni ricorsive

---

# 7.5 Lista di cifre

- Definire una funzione `digits`
    - Parametro: numero intero positivo
    - Risultato: lista di `int`
    - Cifre che compongono il numero, dalle unità in su
- Divedere il numero ripetutamente per 10
    - A ogni passaggio, la cifra è il resto della divisione
    - *Non* usare la rappresentazione come `str`!
    - Es. `6543 → [3, 4, 5, 6]`
- Chiamare la funzione da `main`
    - Chiedere dei numeri all'utente, fino a riga vuota
    - Di volta in volta, mostrare la lista risultante

---

# 7.6 Verifica di cifre

- Ottenere la lista di cifre di un numero dalla funzione `digits` (es. 7.5)
- Verificare la correttezza del risultato
    - Ciclo sulla lista con `enumerate`
    - Moltiplicare ogni cifra per la corrispondente potenza di 10

$$6543 \to [3, 4, 5, 6]$$
$$[3, 4, 5, 6] \to 3 \cdot 10^0 + 4 \cdot 10^1 + 5 \cdot 10^2 + 6 \cdot 10^3$$

---

# 7.7 Selezione di caratteri

- Definire funzione `select_chars`
    - Parametro: un testo
    - Risultato: un nuovo testo
- Selezione per il risultato
    - Esclusi dal testo dato i caratteri con codice Unicode…
    - Minore del carattere precedente o del carattere successivo
- Es. “`testo di prova`” → “`ttirv`”

---

![](https://fondinfo.github.io/images/games/ghosts-goblins.png)
# 7.8 GnG - Gioco e GUI [P1]

- Classe `GngGame`, sottoclasse di `Arena` specializzata per *Ghosts'n Goblins*
    - Inizializzare i personaggi (in base a un file testuale di configurazione)
    - Controllare la conclusione della partita, positiva o negativa
- Classe `GngGui` per la rappresentazione del gioco
    - Disegno immagini e funzionalità legate a `g2d`
    - Metodi `tick` etc.
- Prendere spunto (…) da `BounceGame` e `BounceGui`
    - <https://fondinfo.github.io/play/?c07_bouncegame.py>

---

# 7.8 GnG - Test [P1]

- Creare degli *unit test* per il gioco *Ghosts'n Goblins*
    - Sono consigliati *test parametrizzati*
- Cercare di testare ciascun personaggio separatamente
    - Chiamare direttamente `move`, `pos` ecc., in varie situazioni
- Es. Testare il protagonista simulando varie sequenze di comandi
    - Percorre sempre la traiettoria prevista?
    - Sceglie sempre lo sprite corretto?
    - Reagisce correttamente alle diverse collisioni?

---

![](https://fondinfo.github.io/images/misc/handwriting.jpg)
# 7.8 GnG - Bella copia [P1]

- **Codice leggibile**
    - *Costanti*, anzichè numeri “*magici*” sparsi nel codice
    - *Nomi esplicativi*, semplici, in inglese
    - *Regole di stile* : `variable_name`, `function_name`, `ClassName`, `CONSTANT_NAME`
    - *Commenti*, quando utili: *function annotation*, *docstring*
- **Codice ben organizzato**
    - *No copia&incolla* del codice: funzioni parametrizzate e/o cicli
    - *Programmazione strutturata* : preferibilmente, cicli senza `break`
    - *OOP* : *incapsulamento*, *ereditarietà*, *polimorfismo*

---

![](https://fondinfo.github.io/images/games/tents.png)
# 7.9 Tents puzzle [P2]

- Definire sottoclasse di `BoardGame`
- Inizializzazione con *alberi* 🌳 prefissati
    - Come in figura
- Metodo `play` per inserire *tende* ⛺
    - Liberamente, senza restrizioni
- Metodo `finished` : controllare che…
    - Le tende sono tante quanti gli alberi
    - Ogni albero è adiacente (✜) ad almeno una tenda
    - Ogni tenda è adiacente (✜) ad almeno un albero
    - Per ora, trascurare le altre regole
- Implementare gli altri metodi, tutti *getter*

>

<http://www.brainbashers.com/tentshelp.asp>

---

# Esercitazione 8 (2025-11-17)

---

![](https://fondinfo.github.io/images/fun/matryoshka.png)
# 8.1 Somma ricorsiva di cifre

- Definire una funzione ricorsiva `sum_digits`
    - Riceve come parametro un numero naturale $n$
- Se $n < 10$, $n$ è il risultato
- Altrimenti, si calcola la somma $s$ delle cifre di $n$
    - Su $s$ si applica lo stesso algoritmo
    - Per sommarne ricorsivamente le cifre
- Esempi
    - *f(41)=f(4+1)=f(5)=5*
    - *f(327)=f(12)=f(3)=3*
    - Infatti, *3+2+7=12* e *1+2=3*

---

![](https://fondinfo.github.io/images/draw/palette-circles.svg)
# 8.2 Tavolozza di colori

- Leggere da un file una sequenza di colori
    - In ogni riga ci sono tre valori separati da virgola, per le componenti *R, G, B*
    - I colori vengono memorizzati in una lista (di tuple)
- Chiedere all'utente un numero $n$
- Su un canvas 400×400, disegnare $n$ cerchi in maniera concentrica
    - Il raggio decresce linearmente, da $200$ a $\frac{200}{n}$
    - I colori dei cerchi sono presi in sequenza dalla lista
    - Se si esaurisce la sequenza, si ricomincia dal primo colore

---

![](images/fun/matryoshka.png)
# 8.3 Liste annidate, massimo

- Definire una funzione *ricorsiva* `find_max`
    - Parametro: semplice stringa o lista annidata di stringhe
    - Risultato: stringa maggiore, anche nelle liste annidate
- Una stringa semplice coincide con il risultato
- In una lista, si applica la ricerca del massimo (ricorsivamente) a ogni elemento
    - Il risultato sarà il massimo, tra i risultati ottenuti per ogni elemento
- Esempio : `["Ann", ["Bart", ["Carol", "Cindy"], "Bob", "Art"], ["Bea"], "Bill"]`
    - → Risultato: *Cindy*

---

![](https://fondinfo.github.io/images/draw/rec-circles-2.svg)
# 8.4 Cerchi ricorsivi con palette

- Riprendere l'esercizio 7.4
- Definire un livello massimo di ricorsione
    - Aggiungere un parametro `depth` alla funzione di disegno
    - Per esempio, con `depth=4` si disegnano cerchi di 4 dimensioni diverse
- Il colore dei cerchi dipende dal livello di ricorsione
    - Stesso colore per cerchi della stessa dimensione
    - Prendere i colori da una palette casuale (~ es. 8.2)
- Evitare di disegnare cerchi nella direzione del cerchio grande di provenienza
    - Aggiungere un parametro `skip_dir` alla funzione di disegno
    - Per esempio come tupla $(\pm 1, \pm 1)$

>

Saranno accettate esclusivamente le soluzioni ricorsive

---

![](https://fondinfo.github.io/images/games/minesweeper.svg)
# 8.5 Mines

- Chiedere all'utente numeri $w, h, n$
- Creare una matrice $w×h$ contenente $n$ valori 1 (💣)
    - Valori 1 in posizioni casuali, altre celle a 0
- Salvare la matrice in un file `output.csv`
- Poi, iterativamente chiedere all'utente varie coppie $(x, y)$
    - Valori $x$ e $y$ forniti su una sola riga, separati da spazio
    - Riga vuota per terminare
- Per ogni coppia $(x, y)$ fornita…
    - Comunicare se nella cella scelta c'è 1 (💣)
    - Altrimenti, comunicare quanti 1 ci sono *intorno* a $(x, y)$
    - In orizzontale, verticale e diagonale

---

![](https://fondinfo.github.io/images/repr/file-system.svg)
# 8.6 Profondità albero

- Partire dall'albero di documenti e cartelle
- Aggiungere a tutti i *nodi* un metodo `depth`
    - Riporta la profondità della struttura
    - Livello di annidamento massimo
- Astratto nella classe base
- Per un *documento*: 0
- Per una *cartella*: 1 + profondità massima dei sottonodi
- Rispetto alla struttura raffigurata a fianco
    - Calcolare `depth` della cartella radice (*3*, nell'esempio)

>

<https://fondinfo.github.io/play/?c12_folders.py>

---

![](https://fondinfo.github.io/images/games/tents.png)
# 8.7 Tents, click [P2]

- Rotazione al click
    - Prato 🟩 / tenda ⛺ / niente
- A `BoardGameGui` si possono passare due parametri opzionali
    - Dizionario `actions` per definire *azioni* corrispondenti a tasti
    - Dizionario `annots` per definire *colorazioni* delle celle
- Eventualmente, modificare `BoardGameGui` a piacere

---

# 8.8 Tents, regole [P2]

- Verificare i vincoli numerici per righe e colonne
- Verificare che tende non siano vicine
    - Nè in orizzontale, nè in verticale, nè in diagonale
- Verificare associazioni, non ambigue
    - Tenda adiacente (✜) a un solo albero, oppure…
    - Albero adiacente (✜) a una sola tenda e nessuna cella libera
    - $\implies$ albero e tenda *marcati*, eliminati iterativamente dal computo

---

# 8.9 Tents, automatismi [P2]

- Tasto `g` per marcare automaticamente le celle con *prato*
    - Vincolo di riga/colonna pari alle tende già poste: tutte le celle libere sono *prato*
    - Cella libera vicina a una tenda (anche diagonalmente): *prato*
    - Cella non adiacente a un albero (non assegnato): *prato*
- Tasto `t` per marcare automaticamente le celle con *tende*
    - Vincolo di riga/colonna pari alla somma delle celle libere e delle tende già poste: le celle libere sono *tende*
    - Albero senza tende attorno, con una sola cella libera adiacente: *tenda*

---

# Esercitazione 9 (2025-11-24)

---

# 9.1 Matrice casuale

- Chiedere all'utente le dimensioni `w, h` di una matrice
- Riempire la matrice con i numeri da `1` a `w*h`
    - Ciascuno presente una sola volta, ma in posizione casuale
- Salvare la matrice in un file di testo (*CSV*)
    - Ogni riga della matrice in una riga del file
    - Valori separati tra loro da una virgola

---

# 9.2 Colonne normalizzate

- Leggere da file una matrice di numeri
    - Per es. la matrice salvata nell'es. 9.1
- Per ogni colonna della matrice
    - Stampare il valore massimo
    - Stampare il valore minimo
- Riscrivere inoltre la matrice in un secondo file
    - Ma con valori normalizzati in ogni colonna
    - $v_{norm} = \frac{v - v_{min}}{v_{max} - v_{min}}$ <br> $v_{norm} \in [0, 1]$
- Esempio di normalizzazione:
    - $[2, 4, 6, 5] → [0.0, 0.5, 1.0, 0.75]$

---

# 9.3 In tutte le colonne

- Chiedere all'utente le dimensioni `w, h` di una matrice
- Riempire la matrice con numeri compresi tra 0 e 9, con possibili ripetizioni
- Visualizzare la matrice
- Elencare i numeri che sono presenti in tutte le colonne
- P.es.: nella seguente matrice, i numeri 6 e 7 sono presenti in tutte le colonne

```
7,7,1
6,2,7
4,6,6
3,7,8
```

---

# 9.4 Conteggio parole

- Leggere il contenuto del file `g2d.py`
- Ottenerne le parole, in base alla separazione con qualsiasi carettere bianco
    - Contare le occorrenze di tutte le parole trovate
    - Mostrare le 10 parole più comuni assieme ai relativi conteggi
- Per confronto, ripetere le operazioni, ma…
    - Separare le parole usando `re.split(r"\W+", text)`

---

![](http://fondinfo.github.io/images/fun/polygon.svg) ![](http://fondinfo.github.io/images/fun/move-around.svg)
# 9.5 Poligono in rotazione

- Definire una funzione `regular_poly`
    - Parametri: numero $n$ dei lati, centro $p$ e raggio $r$ del cerchio circoscritto, angolo $a$ del primo vertice
    - Trovare gli $n$ vertici attorno al centro con `move_around`, tutti a distanza $r$
    - Restituire una lista con tutti i punti del poligono, ciascuno rappresentato come una tupla
- Funzioni `main` e `tick`
    - Chiamare `regular_poly` con dati dell'utente
    - Unire i vertici (anche l'ultimo al primo) per disegnare un poligono al centro del canvas
    - Mostrare rotazione del poligono attorno al centro

---

![](https://fondinfo.github.io/images/repr/file-system.svg)
# 9.6 Documento più grande

- Partire dall'esempio di cartelle e documenti
- Aggiungere metodo `largest` ai *nodi*
    - Risultato: tupla `(size, relative_path)` del doc più grande nei sottonodi
- Astratto nella classe base
- Per un *documento*: dimensione del suo contenuto, suo nome
- Per una *cartella*: risultato maggiore, tra i sottonodi
    - Inserisce il suo nome davanti al path
- Rispetto alla struttura raffigurata a fianco
    - Cercare il `largest` a partire dalla cartella radice
    - Es.: `(16, "Desktop/Personal/a1.txt")`

>

Strutture gerarchiche, ma il file system non c'entra

---

# 9.7 Tutti sotto soglia

- Definire una funzione *ricorsiva* `all_below`
    - Parametri: una lista di numeri *data* e un numero *limit*
    - Controllare che tutti i numeri in *data* siano minori della soglia *limit*
- Algoritmo:
    - Una lista vuota non ha valori sopra la soglia
    - Altrimenti, separare il primo elemento *head* dal resto della lista *tail*
    - Se *head* maggiore di *limit*, risultato *falso*
    - Altrimenti, infine, controllare gli altri valori

>

Saranno accettate solo le soluzioni ricorsive

---

![](https://fondinfo.github.io/images/misc/dead-end.jpg)
# 9.8 Tents, vicolo cieco [P2]

- Metodo booleano `wrong`, senza parametri
- Controlla se una delle annotazioni inserite impedisce la soluzione del gioco
    - *Non si può risolvere il gioco senza rimuovere una annotazione*
    - Es. Due tende vicine
    - Es. Una riga completa che non soddisfa vincolo numerico
    - Es. Un albero senza tenda e senza celle libere vicine
- Può restituire `False` anche se la partita non è finita
    - Non ci sono violazioni evidenti, dovute ai simboli già inseriti
    - Ci sono però delle celle ancora non marcate

---

# 9.9 Tents, test [P2]

- Creare degli *unit test* per il gioco Tents
- Verificare il gioco dopo varie chiamate a `play`
    - Usare `read` per osservare lo stato
- Verificare il funzionamento di `finished` rispetto alle regole
    - Nessun valore ripetuto, tra quelli non anneriti
    - Celle annerite non adiacenti
    - Contiguità tra tutte le celle bianche

---

# Esercitazione 10 (2025-12-01)

---

![](https://fondinfo.github.io/images/misc/artificial-intelligence.png)
# 10.1 Tents, suggerimenti [P2]

- Cercare automaticamente la prossima mossa
    - Ragionamento simile a giocatore umano
    - Avviare la ricerca col tasto `a`
- *Provare* a inserire una *tenda* in una cella non annotata
    - Applicare gli automatismi dell'es. 8.9
    - Se le regole sono violate (`wrong`), inserire un prato
- *Provare* un prato in una cella non annotata
    - Applicare gli automatismi dell'es. 8.9
    - Se le regole sono violate (`wrong`), inserire una tenda

>

Se invece una ipotesi non risulta `wrong`, non è detto che sia giusta; non si possono trarre conclusioni!

---

![](https://fondinfo.github.io/images/misc/artificial-intelligence.png)
# 11.2 Tents, altri suggerimenti [P2]

- Considerare ogni cella non annotata, singolarmente
- *Provare a inserire tenda*
    - Applicare gli automatismi dell'es. 8.9
- *Provare a inserire prato*
    - Applicare gli automatismi dell'es. 8.9
- *Confrontare* tutte le annotazioni, aggiunte nei due casi
    - Se una qualsiasi cella diventa *tenda* in entrambe le ipotesi ⇒ *tenda* nel gioco
    - Se una qualsiasi cella diventa *prato* in entrambe le ipotesi ⇒ *prato* nel gioco

---

# 11.3 Tents, test soluzione [P2]

- Permettere di inizializzare il gioco da un file di testo
    - Usare gli schemi in `tents-games.zip` su Elly
- Provare inoltre a risolvere quegli schemi automaticamente
    - Per ogni mossa, applicare i suggerimenti
    - Suggerimenti degli es. 11.1 e 11.2
- Ricordarsi…
    - Inizializzare la partita da un *file* (parametro)
    - Preparare vari *unit test*, per le principali funzionalità
