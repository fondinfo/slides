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

