![](https://fondinfo.github.io/images/dev/geek-girl.svg)
# Esercizi 2026
## Introduzione alla programmazione

---

# Esercitazione 1 (2026-09-28)

---

![](https://fondinfo.github.io/images/oop/personal-data.png)
# 1.1 Sconto al cinema

- Creare un programma Python che verifichi se un utente può acquistare un biglietto ridotto per il cinema
- Chiedere all'utente la sua età: “*Quanti anni hai?*”
- Fino a 25 anni compiuti (cioè, meno di 26), mostrare all'utente il messaggio: “*Hai diritto allo sconto giovani!*”
- Altrimenti, mostrare il messaggio: “*Prezzo intero*”

---

![large](https://fondinfo.github.io/images/draw/three-circles.svg)
# 1.2 Raggi decrescenti

- Scrivere un programma Python basato su `g2d`
- Chiedere all'utente le misure di tre raggi
- Se i raggi sono forniti in ordine decrescente…
    - Disegnare tre cerchi concentrici, con i tre raggi dati
    - Tutti al centro di un canvas 500×500
    - Primo cerchio di colore magenta, secondo giallo, terzo ciano
- Altrimenti, mostrare un messaggio di errore

---

![large](https://fondinfo.github.io/images/draw/three-circles.svg)
# 1.3 Cerchi in loop

- Scrivere un programma Python basato su `g2d`
- Chiedere all'utente le misure di tre raggi
- Usare un ciclo `for` per…
    - Disegnare tre cerchi concentrici, con i tre raggi dati
    - Tutti al centro di un canvas 500×500
    - Per ogni cerchio, scegliere un colore casuale

---

![](https://fondinfo.github.io/images/misc/leap-centuries.svg)
<br>
Bisestili: 2000, 2004, 2008…
<br>
Non bisestili: 2001, 1900, 2100…
# 1.4 Anni bisestili

- Chiedere all'utente di inserire un anno
- Dire se è bisestile oppure no <br> <br>

>

Un anno è bisestile se è divisibile per 4, con l'eccezione degli anni secolari (quelli divisibili per 100) che non sono divisibili per 400
<br>
<https://it.wikipedia.org/wiki/Anno_bisestile#Definizione>
<br>
<br>
<br>
`n` è divisibile per `x` se `n % x == 0`

---

![large](http://fondinfo.github.io/images/misc/slope.svg)
# 1.5 Distanza tra due punti

- Chiedere all'utente le coordinate di due punti sul piano cartesiano
    - $x_1, y_1, x_2, y_2$
- Calcolare la distanza euclidea $d$ tra i due punti
- Comunicare inoltre se i due punti sono allineati…
    - Orizzontalmente, verticalmente, oppure su nessuno dei due assi

---

![](https://fondinfo.github.io/images/draw/random-circles.svg)
# 1.6 Cerchi casuali

- Chiedere all'utente un numero `n`
- In un canvas 500×500, disegnare `n` cerchi
    - Tutti con raggio di 50 pixel
    - Ciascuno con posizione casuale e colore casuale
    - Con centro all'interno del canvas

>

Cominciare a disegnare un solo cerchio, in posizione casuale

---

![](https://fondinfo.github.io/images/draw/shadowed-circles.svg)
# 1.7 Cerchi con ombra

- Chiedere all'utente un numero `n`
- In un canvas 500×500, disegnare `n` cerchi
    - Tutti di raggio 50
    - Ciascuno con posizione e colore casuale
    - Ciascuno con un ombra grigia spostata a destra e in basso di 5 pixel
- Cerchi e ombre completamente visibili all'interno nel canvas

---

![](https://fondinfo.github.io/images/draw/numbered-circles.svg)
# 1.8 Cerchi numerati

- Chiedere all'utente un numero `n`
- Disegnare `n` cerchi casuali, con ombra
    - Come nell'esercizio precedente
- Scrivere su ciascun cerchio un numero progressivo, a partire da 1
    - Se il cerchio è chiaro, scrivere in nero
    - Se il cerchio è scuro, scrivere in bianco

>

Considerare la somma delle componenti *R, G, B*

---

![](https://fondinfo.github.io/images/draw/random-radius.svg)
# 1.9 Cerchi concentrici casuali

- Disegnare un cerchio di raggio 200 e colore casuale
- Disegnare dei cerchi concentrici, via via più piccoli
- Per ognuno, scegliere casualmente raggio e colore
- Fermarsi quando il raggio diventa più piccolo di 10

---

# Esercitazione 2 (2026-10-05)

---

![](https://fondinfo.github.io/images/misc/solids.png)
# 2.1 Funzione, volume del cilindro

- Definire una funzione `cylinder_volume` per il calcolo del volume di un cilindro
    - Parametri: raggio e altezza come `float`
    - Risultato: volume ($\pi r^2h$) come `float`
    - Validazione: generare un `ValueError` con messaggio esplicativo se raggio o altezza negativi
- Invocare la funzione dalla shell interattiva
    - Verificare con diversi valori di prova
    - Sia argomenti corretti che errori
- Aggiungere poi al programma una funzione `main`
    - Chiedere all'utente i due valori
    - Chiamare `cylinder_volume` con questi parametri
    - Infine mostrare all'utente il risultato

---

# 2.2 Fattoriale

- Definire una funzione `factorial`
    - Parametro: intero positivo $n$
    - Se $n$ è $0$, il risultato è $1$ per definizione matematica
    - Altrimenti, è il prodotto tra i primi $n$ numeri naturali
- Definire una funzione `main`
    - Chiedere un numero all'utente e mostrarne il fattoriale

>

Memorizzare in una variabile il risultato parziale; a ogni ciclo, moltiplicarla per il nuovo numero

---

![](https://fondinfo.github.io/images/misc/letters.png)
# 2.3 Gruppi di lettere

- Definire una funzione `count_groups`
- Parametro: un testo
- Risultato: due valori
    - Quante lettere del testo sono comprese nel gruppo `A-M`
    - Quante nel gruppo `N-Z`
    - Senza distinguere maiuscole e minuscole
- Definire una funzione `main`
    - Chiamare `count_groups` con un testo fornito dall'utente e mostrare i risultati
    - Ripetere queste operazioni in un ciclo
    - Finchè l'utente non fornisce una riga vuota, che non deve essere elaborata

---

![](https://fondinfo.github.io/images/draw/n-points.svg)
# 2.4 Punti allineati

- Chiedere all'utente il numero *n* di punti da visualizzare
- Chiedere le coordinate del primo e dell'ultimo punto
- Mostrare *n* punti su canvas 400×400
    - Punti allineati ed equispaziati
    - Ciascun punto è un cerchietto di raggio 5

---

![](https://fondinfo.github.io/images/draw/n-points.svg)
# 2.5 Punti colorati

- Riprendere l'esercizio precedente
- Chiedere all'utente i colori del primo e dell'ultimo punto
- Cambiare il colore gradualmente da un punto all'altro
    - Variare ciascuna componente di colore
    - Dal livello iniziale fino a quello finale
- Per esempio: primo punto rosso saturo, ultimo punto blu saturo

---

![](https://fondinfo.github.io/images/misc/characters.png)
# 2.6 Carattere Unicode

- Chiedere all'utente un *numero*
- Visualizzare il carattere Unicode corrispondente
- Ripetere le operazioni in un ciclo, finchè l'utente non inserisce una *riga vuota*

>

Usare la funzione `chr` per convertire un codice nel carattere corrispondente

---

![](https://fondinfo.github.io/images/misc/gold-price.svg)
# 2.7 Valori sopra e sotto la media

- Chiedere all'utente una sequenza di interi
    - Sequenza terminata da $0$ (*sentinella*)
- Calcolare e mostrare il valore medio
- Elencare i valori sotto alla media
- Elencare i valori sopra (o uguali) alla media

>

Aggiungere ciascun valore a una lista inizialmente vuota, con `append`

---

![](https://fondinfo.github.io/images/games/diff-angle.svg)
# 2.8 Super Sprint, direzione [P1]

- Partire dall'animazione della pallina vista a lezione
    - Partire da *(200, 200)* in un canvas *400×400*
- Impostare variabili globali `v = 4`, `angle = 0`
    - `v` per ampiezza dello spostamento
    - `angle` per direzione dello spostamento
    - Usare `move_around` da `polar`
- Cambio di direzione, in base al puntatore del mouse
    - Se è a sinistra, diminuire `angle` di `90/8`
    - Se è a destra, aumentare `angle` di `90/8`

>

Da `polar` <https://fondinfo.github.io/play/?polar.py>
<br>
`d_tgt, a_tgt = to_polar(dist_vec(pos, tgt))`
<br>
Distanza tra pos attuale e target; angolo che indirizza verso target
<br>
Poi, valutare la differenza rispetto all'angolo attuale

---

![](https://fondinfo.github.io/images/games/super-sprint.png)
# 2.9 Super Sprint, sprite [P1]

- Continuare l'esercizio 2.8
- Disegnare un'automobile anzichè una pallina
    - Ritagliare l'immagine da [`super-sprint.png`](https://fondinfo.github.io/sprites/super-sprint.png)
    - [`g2d.draw_image`](https://github.com/fondinfo/fondinfo#images-and-sounds)
- Scegliere l'immagine in base al valore attuale di `angle`

---

# Esercitazione 3 (2026-10-12)

---

![](https://fondinfo.github.io/images/misc/triangle-notations.svg)
# 3.1 Classe triangolo

- Creare una classe `Triangle`
    - Campi: misure dei tre lati
    - Metodo per il calcolo del perimetro
    - Metodo per il calcolo dell'area
- Definire una funzione `main`
    - Chiedere all'utente le misure dei tre lati
    - Istanziare un oggetto di classe `Triangle`
    - Usarne i metodi per calcolare perimetro e area
    - Mostrare all'utente i risultati

>

$area = \sqrt{s \cdot (s-a) \cdot (s-b) \cdot (s-c)}, s = \frac{a+b+c}{2}$

---

![](https://fondinfo.github.io/images/oop/ball-object.svg) ![](https://fondinfo.github.io/images/oop/ball-uml.svg) Class diagram UML
# 3.2 Pallina al centro

- Modificare la classe `Ball` presente negli esempi
- Parte al centro, in direzione casuale
    - Alto, basso, sinistra, destra
    - Costruttore senza parametri (oltre a `self`)
- Arrivata al bordo, riparte dal centro
    - Nuova direzione casuale
- Gestire l'animazione di una pallina
    - Come nel codice di esempio

---

![](https://fondinfo.github.io/images/oop/ball-object.svg) ![](https://fondinfo.github.io/images/oop/ball-uml.svg) Class diagram UML
# 3.3 Ritorno a casa

- Riprendere l'esercizio precedente
- Parametri del costruttore per posizione iniziale
    - La posizione iniziale è la *home* della pallina
- Arrivata al bordo, la pallina riparte dalla sua *home*
    - Anzichè dal centro
- Creare ed animare due palline
    - Con due *home* diverse

---

# 3.4 Somma di cifre

- Definire una funzione `sum_digits`, che prende come parametro un numero naturale $n$ e restituisce la somma delle sue cifre decimali
- Definire inoltre una funzione `main`, in cui chiedere all'utente un numero iniziale
    - Poi, invocare ripetutamente la funzione `sum_digits`, usando di volta in volta come argomento il risultato precedente
    - Mostrare all'utente ciascun risultato ottenuto
    - Il programma termina quando si ottiene un numero con una sola cifra
- Per esempio, la sequenza ottenuta a partire da $9875$ è: $29, 11, 2$.

---

# 3.5 Tabella delle distanze

- Considerare tutti gli accoppiamenti tra due numeri: `x` e `y`
    - Ciascun numero compreso tra 1 e 5
- Mostare in tabella la distanza (`abs`) tra i due numeri
    - Una riga per ogni valore di `y`
    - Una colonna per ogni valore di `x`

``` text
0   1   2   3   4
1   0   1   2   3
2   1   0   1   2
3   2   1   0   1
4   3   2   1   0
```

>

Usare due cicli for annidati; cominciare a scrivere il solo ciclo sulla `x`, con `y` costante

---

![](https://fondinfo.github.io/images/draw/blue-row.svg)
# 3.6 Cerchi blu

- Chiedere all'utente un numero $n$
- Disegnare una riga di $n$ cerchi blu
    - Affiancati, su canvas 500×500
    - Intensità di blu linearmente crescente
- Disegno simile alla figura, però…
    - Lasciare un margine di 25px rispetto ai bordi laterali del canvas
    - Intensità di blu del primo cerchio: 50
    - Intensità dell'ultimo: 200

---

![](https://fondinfo.github.io/images/draw/n2-circles.svg)
# 3.7 Figure affiancate

- Definire una funzione `draw_figure`
    - Parametri per: centro, raggio, $n$
    - Disegnare una figura di $n$ cerchi concentrici
    - Il raggio più interno è $\frac{1}{n}$ rispetto al più esterno
    - Colorare i cerchi in grigio: dal nero esterno al bianco interno
- In `main`:
    - Chiedere all'utente un numero $n$
    - In un canvas $500×500$, disegnare $n$ figure uguali affiancate
    - Occupare tutto lo spazio, in orizzontale

---

![](https://fondinfo.github.io/images/misc/characters.png)
# 3.8 Codici pari e dispari

- Per ogni riga di testo inserita dall'utente, stampare:
    - Il numero delle minuscole con codice Unicode dispari: `a, c, e…`
    - Il numero delle minuscole con codice Unicode pari: `b, d, f…`
    - Es. `"Python"`: 3 minuscole con codice pari, 2 con codice dispari
- Il programma si interrompe quando l'utente inserisce una *riga vuota*
- Mostrare infine anche i conteggi complessivi
    - Minuscole con codice dispari
    - Minuscole con codice pari
    - Numero di righe non vuote

---

![](https://fondinfo.github.io/images/games/super-sprint.png)
# 3.9 Super Sprint, classe Car [P1]

- Creare una classe `Car`, partendo dall'esempio `Ball`
    - Modulo della velocità sempre pari a 4
- Campo `angle` per memorizzare la direzione
- Metodo `move`, per aggiornare la posizione
    - Ogni 2 frame, incrementare `angle` di una quantità fissa
    - Inizialmente l'incremento angolare è di `90/8`
    - Ogni 64 frame, passare da rotazione oraria a antioraria e viceversa (cambiare il segno dell'incremento angolare)
- Metodo `sprite`
    - Ritagliare l'immagine da [`super-sprint.png`](https://fondinfo.github.io/sprites/super-sprint.png)
    - Scegliere l'immagine in base al valore attuale del campo `angle`

---

# Esercitazione 4 (2026-10-19)

---

![](https://fondinfo.github.io/images/comp/orders.svg)
# 4.1 Modello esponenziale

- Creare una classe delle curve esponenziali
    - $y = a\cdot e^{b x} + c$
- Campi per $a, b, c$, da inizializzare nel *costruttore*
    - Se $a=0$ o $b=0$, il modello non è exp
    - ⇒ `ValueError` con messaggio esplicativo
- Metodo `predict`, con parametro $x$
    - Risultato: valore della funzione in $x$
- Nella funzione `main`
    - Istanziare un *singolo* modello exp, con coefficienti forniti dall'utente
    - Valutare il modello con `predict`, in diversi punti $x$ forniti dall'utente
    - Il programma termina all'inserimento di una riga vuota

```
from math import e, exp  # use either one of them
```

---

![](https://fondinfo.github.io/images/misc/calendar-rows.png)
# 4.2 Calendario da tavolo

- L'utente inserisce:
    - La lunghezza del mese (28-31)
    - Il primo giorno del mese <br> (lunedì=0 ... domenica=6)
- Visualizzare il calendario del mese
    - Sulla console *testuale*, senza grafica
    - Disporre i giorni in una griglia, una riga alla volta
    - 7 colonne, la prima per i lunedì, l'ultima per le domeniche

>

Procedere sempre una riga alla volta (come macchina da scrivere)
<br>
Partire con il caso più semplice: lunedì come primo giorno

---

![](https://fondinfo.github.io/images/draw/xmas-triangle.svg)
# 4.3 Triangolo di cerchi colorati

- Chiedere all'utente un numero `n`
- Generare `n` righe di cerchi, allineate a sinistra
- La prima riga contiene un solo cerchio
- Ogni riga successiva contiene un cerchio in più
- Ogni cerchio ha un colore casuale

---

![](https://fondinfo.github.io/images/draw/xmas-tree.svg)
# 4.4 Albero di cerchi colorati

- Chiedere all'utente un numero `n`
- Generare `n` righe di cerchi, allineate al centro
- Il numero di riga corrisponde al numero di cerchi da disegnare
- Ogni cerchio ha un colore casuale
- Aggiungere in fondo una riga con un solo cerchio

---

![](https://fondinfo.github.io/images/games/anim-bounce.svg)
# 4.5 Pallina che cresce

- Modificare `Ball` nell'esempio `bounce` (con `Arena`)
    - <https://fondinfo.github.io/play/?c07_bounce.py>
    - Mantenere gli stessi campi: *x, y, w, h, dx, dy*
    - A ogni rimbalzo, il *raggio* aumenta di 2 pixel
    - Fino a un massimo di 20 pixel, poi torna a 10
- Definire metodo `grow`, senza parametri oltre `self`
    - Calcolare la posizione centrale e il raggio attuali
    - Modificare il raggio come richiesto (var locale)
    - Rivalutare *x, y, w, h* della pallina
- Restituire `None` nel metodo `sprite`
- Nel `tick`, disegnare un rettangolo quando lo sprite è `None`

---

![](http://fondinfo.github.io/images/fun/polygon.svg) ![](http://fondinfo.github.io/images/fun/move-around.svg)
# 4.6 Poligono in rotazione

- Definire una funzione `regular_poly`
    - Parametri: numero $n$ dei lati, centro $p$ e raggio $r$ del cerchio circoscritto, angolo $a$ del primo vertice
    - Trovare gli $n$ vertici attorno al centro con `move_around`, tutti a distanza $r$
    - Restituire una lista con tutti i punti del poligono, ciascuno rappresentato come una tupla
- Funzioni `main` e `tick`
    - Chiamare `regular_poly` con dati dell'utente
    - Unire i vertici (anche l'ultimo al primo) per disegnare un poligono al centro del canvas
    - Mostrare rotazione del poligono attorno al centro

---

![](https://fondinfo.github.io/images/games/super-sprint.png)
# 4.7 Super Sprint, guida [P1]

- Rendere la classe `Car` un *actor*
- Aggiungerla all'arena fornita, 500×500, con `spawn`
- Sterzata: cambio di direzione *graduale*
    - Variazione fissa a ogni frame
    - Se utente preme freccia verso destra, o sinistra
- Accelerazione e frenata: cambio di velocità *graduale*
    - Variazione fissa a ogni frame
    - Se utente preme freccia verso alto, o basso
- Prendere i tasti da `arena.current_keys()`

---

# 4.8 Super Sprint, avversari [P1]

- Creare un personaggio `Opponent`, per le auto avversarie
- Aggiungerla all'arena fornita, 500×500, con `spawn`
- 🔁 Traiettoria fissa di tre punti da seguire, come *target* consecutivi
    - *Waypoints*: (100, 100), (400, 100), (250, 360)
    - Target attuale abbastanza vicino? (~ 25px)
    - ⇒ Waypoint successivo nella traiettoria diventa target
- Orientare *gradualmente* l'auto verso il target
- Rallentare *gradualmente*, se l'auto è molto disallineata dal target

---

# 4.9 Super Sprint, collisioni [P1]

- Gestire la collisione tra due auto
    - In metodo `move`, controllare `arena.collisions()`
- Cambio direzione e velocità semplicistico, p.es.:
    - Perturbare casualmente di ±1 la posizione
    - Se altra auto è a sinistra/destra, aumentare/diminuire direzione di 1
    - Se altra auto è dietro/avanti, aumentare/diminuire velocità di 1

```
o_dist, o_angle = to_polar(dist_vec(self.pos(), other.pos()))
diff_angle = coterminal(o_angle - self._angle * rot) # …
```

---

# Esercitazione 5 (2026-10-26)

---

![](https://fondinfo.github.io/images/misc/clamp.svg)
# 5.1 Clamp su lista

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

# 5.2 Lista di cifre

- Definire una funzione `digits`
    - Parametro: numero intero positivo
    - Risultato: lista di `int`
    - Cifre che compongono il numero, dalle unità in su
- Divedere il numero ripetutamente per 10
    - Ad ogni passaggio, la cifra è il resto della divisione
    - *Non* usare la rappresentazione come `str`!
    - Es. `6543 → [3, 4, 5, 6]`
- Chiamare la funzione da `main`
    - Chiedere dei numeri all'utente, fino a riga vuota
    - Di volta in volta, mostrare la lista risultante

---

# 5.3 Lettere iniziali uguali

- Scrivere una funzione `len_common_prefix`
    - Parametri: due stringhe da confrontare
    - Risultato: numero di lettere iniziali uguali tra le due stringhe
- Scrivere una funzione `main`
    - Chiedere all'utente due stringhe di testo
    - Invocare `len_common_prefix` sulle due stringhe
    - Mostrare all'utente il risultato
- Es. `“carta”` vs. `“carota”` → 3 (`“car”`)

---

# 5.4 Classe per quadratiche

- Definire una classe delle espressioni quadratiche
- Campi per memorizzare i tre coefficienti
- Metodo `predict` per valutare l'espressione in un punto dato
    - Parametro per il valore di *x*
- Nella parte principale del programma
    - Chiedere all'utente i coefficienti per istanziare un unico oggetto
    - In un ciclo, valutare l'espressione per vari valori *x* inseriti dall'utente

![large](https://fondinfo.github.io/images/misc/quadratic.svg)

---

# 5.5 Classe per polinomi

- Definire una classe delle espressioni polinomiali
- Campo per la *lista* dei coefficienti
    - Parametro del costruttore
    - Lunghezza: *n+1* (*n*: grado)
- Metodo `predict` per valutare l'espressione in un punto dato
    - Parametro per il valore di *x*
- Nella parte principale del programma
    - Chiedere all'utente i coefficienti per istanziare un unico oggetto
    - In un ciclo, valutare l'espressione per vari valori *x* inseriti dall'utente

![large](https://fondinfo.github.io/images/misc/polynomial.svg)

---

![](https://fondinfo.github.io/images/games/super-sprint.png)
# 5.6 Super Sprint - Checkpoint [P1]

- Definire una sequenza di *checkpoint* lungo il circuito (traguardo compreso)
- L'auto deve attraversarli in ordine, per far avanzare il conteggio di un *giro*
    - Attraversare un checkpoint “sbagliato” (fuori ordine) non ha effetto
- Dopo 3 giri completi, la gara termina
- Mostrare a schermo: giro corrente e tempo trascorso

>

Un checkpoint può essere un *actor*, per sfruttare il controllo delle collisioni

---

# 5.7 Super Sprint - Fuoripista [P1]

- Il circuito è definito da oggetti che ne formano i bordi (interno ed esterno)
    - <https://fondinfo.github.io/sprites/super-sprint-bg.png>
- Se l'auto tocca un bordo esterno o un muro…
    - La velocità si riduce bruscamente (l'auto "sbatte")
- Opzionalmente, definire alcuni tratti *fuoripista*
    - Se l'auto è fuori dai bordi della pista (sull'“erba”)…
    - La velocità massima raggiungibile si riduce (per es. a un terzo)

>

Un bordo può essere un *actor*, per sfruttare il controllo delle collisioni

---


# Esercitazione 6 (2026-11-02)

---

![](https://fondinfo.github.io/images/misc/censorship.jpg)
# 6.1 Censura di testo

- Chiedere all’utente una riga di testo
- Il testo compreso tra asterischi (`*`) è considerato “*riservato*”
- Scrivere in output l’intera riga, ma sostituendo ogni carattere riservato con un `#`
- Gli asterischi stessi non vanno scritti in output
- Esempio:

```
La password di Marco è *tigre2024* e il suo PIN è *4821*.
La password di Marco è ######### e il suo PIN è ####.
```

>

Segnare in un bool se si è dentro una parte riservata (cioè se si è letto un asterisco di apertura, ma non ancora quello di chiusura)

---

# 6.2 Conteggio per iniziale

- Leggere varie righe di testo inserite dall'utente
    - Fino all'inserimento di una riga vuota
- Dividere il testo in parole in base alla presenza di spazi
- Calcolare il numero delle parole…
    - Raggruppate in base alla loro prima lettera
    - Indifferentemente, maiuscola o minuscola (*case-insensitive*)
- Per esempio
    - Le parole che iniziano con “`a`” sono 18
    - Quelle con “`b`” sono 3
    - Quelle con “`c`” sono 13 …
- Dopo ogni riga mostrare i conteggi aggiornati, su tutte le righe precedenti

>

Usare lista di 26 contatori

---

# 6.3 Lettere finali uguali

- Scrivere una funzione `len_common_suffix`
    - Parametri: due stringhe da confrontare
    - Risultato: numero di lettere finali uguali tra le due stringhe
- Fornire due implementazioni di `len_common_suffix`
    - Indice, o `zip`
- Scrivere una funzione `main`
    - Chiedere all'utente due stringhe di testo
    - Invocare `len_common_suffix` sulle due stringhe
    - Mostrare all'utente il risultato
- Es. `"lucertola"` vs. `"pistola"` → 4 (`"tola"`)

---

![](https://fondinfo.github.io/images/misc/dice.png)
# 6.4 Sequenze di dado

- Simulare `n` lanci di un singolo dado
    - `n` scelto dall'utente
- Contare la lunghezza massima di una sequenza di lanci consecutivi con lo stesso risultato
- Es. `[3, 3, 5, 1, 1, 1, 6, 2]` → 3 (i tre `1` consecutivi)

>

Mantenere due contatori: la sequenza corrente e la sequenza massima trovata finora

---

# 6.5 Cerchi sovrapposti

- Disegnare dei cerchi casuali su un canvas 400×400
    - Posizione e colore casuale
    - Tutti di raggio 15
- Il numero dei cerchi non è fissato
    - Il programma termina quando…
    - L'ultimo cerchio disegnato interseca uno dei precedenti

>

Memorizzare in una lista le posizioni dei cerchi

---

![](https://fondinfo.github.io/images/games/super-sprint.png)
# 6.6 Super Sprint, gioco e GUI [P1]

- Classe `SuperSprintGame`, per gestire il gioco
    - Inizializzare i personaggi, prendendo i dati da un file di configurazione
    - Incapsulare personaggi e arena
    - Controllare la conclusione della partita, positiva o negativa
- Classe `SuperSprintGui` per la rappresentazione del gioco
    - Disegno immagini e funzionalità legate a `g2d`
    - Metodi `tick` etc.
- Prendere spunto (…) da `BounceGame` e `BounceGui`
    - <https://fondinfo.github.io/play/?c07_bouncegame.py>

---

# 6.7 Estensioni opzionali [P1]

- *Pozze d'olio* 🫟 lungo il circuito
    - L'auto perde il controllo dello sterzo
    - L'angolo varia in modo casuale (“testacoda”)
    - Dopo ~ 30 frame, il controllo torna normale
- *Chiavi inglesi* 🔧 raccoglibili lungo il circuito
    - Ogni 3 chiavi raccolte, si ottiene un potenziamento casuale
    - Velocità massima più alta, oppure…
    - Accelerazione più rapida, oppure…
    - Sterzata più reattiva
- Mostrare a schermo il numero di chiavi raccolte e i potenziamenti attivi

---

# 6.8 Modello fisico opzionale [P1]

- In `move`, controllare ulteriormente se auto abbastanza vicine
    - P.es.: distanza tra i *centri* è sotto una certa soglia?
    - Cioè, trascurare gli alettoni, per la collisione
- Calcolare direzione in base all'asse tra i due centri (…)
    - <https://en.wikipedia.org/wiki/Elastic_collision#Two-dimensional>
- Considerare la forma allungata delle auto (…)
- Concedere alle auto un tempo di *grazia* dopo una collisione

---

![](https://fondinfo.github.io/images/games/nurikabe.svg)
# 6.9 Nurikabe puzzle [P2]

- Definire sottoclasse di `BoardGame`
- Inizializzazione con *vincoli* numerici prefissati
    - Come in figura
- Metodo `play` per *annerire* o *marcare* una cella
    - Liberamente, senza restrizioni
    - Ma non su celle con numero
    - Per esempio: 0 □ / -1 ■ / -2 •
- Metodo `finished` : controllare le regole del gioco
    - Per ora, sempre `False`
- Implementare gli altri metodi, tutti *getter*
- Visualizzare la matrice con `boardgamegui`

---

# Nurikabe, regole [P2]

- ① A number tells the number of continuous white cells
- ② Each area of white cells contains only one number
- ③ The black cells are linked to be a continuous wall
- ④ Black cells cannot be linked to be 2×2 square or larger

>

<https://www.nikoli.co.jp/en/puzzles/nurikabe/>

---

# Esercitazione 7 (2026-11-09)

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

# 7.2 Lettere finali con ricorsione

- Scrivere una funzione ricorsiva `rec_common_suffix`
    - Parametri: due stringhe da confrontare
    - Risultato: numero di lettere finali uguali tra le due stringhe
- Idea
    - Confrontare gli ultimi caratteri (*last*)
    - Applicare lo stesso procedimento al resto (*init*)
- Invocare da shell la funzione con diversi argomenti

>

Saranno accettate solo le soluzioni ricorsive

---

![](https://fondinfo.github.io/images/misc/characters.png)
# 7.3 Matrice casuale

- Definire funzione `randchar`
- Due parametri di tipo carattere
    - Estremi dell'intervallo di caratteri possibili
    - Estremi *inclusi* (l'intervallo è *chiuso*)
- Risultato: carattere casuale scelto dall'intervallo dato
- Chiedere all'utente le dimensioni $w, h$ di una matrice
- Riempire con una *comprehension* una lista
    - Con $w·h$ lettere minuscole casuali, con possibili ripetizioni

---

# 7.4 Analisi matrice

- Partire da una matrice simile a es. 7.3
- Mostrare a console la lista come una matrice, riga per riga, in formato *CSV*
    - Caratteri separati da virgola (ma senza virgola a fine riga)
- Salvare la stessa matrice in un file di testo `matrix.csv`
- In un ciclo
    - Chiedere un carattere all'utente
    - Elencare le posizioni in cui il carattere è presente
    - Marcare con asterisco le posizioni trovate che siano celle di bordo <br> (celle in prima o ultima colonna, o riga)
- Es.: la `r` è presente 4 volte in tutto, 3 volte su celle di bordo

``` txt
a,c,r,a
r,r,t,a
t,r,e,f
```

---

![](https://fondinfo.github.io/images/draw/palette-circles.svg)
# 7.5 Tavolozza di colori

- Leggere da un file una sequenza di colori
    - In ogni riga ci sono tre valori separati da virgola, per le componenti *R, G, B*
    - I colori vengono memorizzati in una lista (di tuple)
- Chiedere all'utente un numero $n$
- Su un canvas 400×400, disegnare $n$ cerchi in maniera concentrica
    - Il raggio decresce linearmente, da $200$ a $\frac{200}{n}$
    - I colori dei cerchi sono presi in sequenza dalla lista
    - Se si esaurisce la sequenza, si ricomincia dal primo colore

---

# 7.6 Scomposizione in cifre

- Scrivere una funzione ricorsiva `digits`, che prende un numero $n$
    - Restituisce una *lista* di cifre che compongono il numero, dalle unità in su
- Se $n$ è zero, il risultato è una lista vuota
- Altrimenti
    - Calcolare quoziente $q$ e resto $r$ di $n / 10$
    - Il risultato parziale è una lista contenente il resto $r$
    - Per ottenere la restante parte del risultato, si applica lo stesso procedimento al quoziente $q$
- Es. `345` → `[5, 4, 3]`

>

Usare divisione e resto, **non** usare la rappresentazione come `str`!
<br>
Saranno accettate solo le soluzioni ricorsive

---

# 7.7 Verifica di cifre

- Definire funzione ricorsiva `rebuild`
    - Riceve lista di cifre, ordinate a partire dalle unità (vedi 7.6)
    - Restituisce il numero che esse compongono
- Caso base: `[]` → 0
- Passo ricorsivo: separare *head* e *tail*
    - Risultato: $head + 10 · r$
    - $r$ è ottenuto per ricorsione su *tail*

$$6543 \to [3, 4, 5, 6]$$
$$[3, 4, 5, 6] \to 3 \cdot 10^0 + 4 \cdot 10^1 + 5 \cdot 10^2 + 6 \cdot 10^3$$

---

# 7.8 Super Sprint - Test [P1]

- Creare degli *unit test* per il gioco *Super Sprint*
    - Usare il modulo `unittest`
    - Sono consigliati *test parametrizzati*
- Cercare di testare ciascun personaggio separatamente
    - Chiamare direttamente `move`, `pos` ecc., in varie situazioni
- Es. Testare il protagonista simulando varie sequenze di comandi
    - Percorre sempre la traiettoria prevista?
    - Sceglie sempre lo sprite corretto?
    - Reagisce correttamente alle diverse collisioni?

>

<https://fondinfo.github.io/slides/p34-collaudo.html#/16>

---

![](https://fondinfo.github.io/images/games/nurikabe.svg)
# 7.9 Nurikabe, quadrati neri [P2]

- Aggiungere al gioco un metodo booleano `black_2x2`, senza parametri
    - Vero se $\exists$ quadrato 2×2 di celle nere
    - Regola ④: *Black cells cannot be linked to be 2×2 square or larger*
- Controllare ogni cella, come angolo in alto a sinistra del quadrato
    - Attenzione ai bordi della matrice
- Verificare il metodo dopo varie chiamate a `play`
    - Usare per ora `status` per segnalare 2×2 nere

>

Il metodo servirà poi per `finished`

---

![](https://fondinfo.github.io/images/misc/handwriting.jpg)
# Progetti in bella copia [P1, P2]

- **Codice leggibile**
    - *Costanti*, anzichè numeri “*magici*” sparsi nel codice
    - *Nomi esplicativi*, semplici, in inglese
    - *Regole di stile* : `variable_name`, `function_name`, `ClassName`, `CONSTANT_NAME`, `_private_field`
    - *Commenti*, quando utili: *function annotation*, *docstring*
- **Codice ben organizzato**
    - *No copia&incolla* del codice: funzioni parametrizzate e/o cicli
    - *Programmazione strutturata* : preferibilmente, cicli senza `break`
    - *OOP* : *incapsulamento*, *ereditarietà*, *polimorfismo*

---

# Esercitazione 8 (2026-11-16)

---

![](https://fondinfo.github.io/images/draw/rec-circles.svg)
# 8.1 Cerchi ricorsivi

- Funzione *ricorsiva* `rec_circles`
    - Parametri: centro $p$ e raggio $r$
- Se $r \leq 5$, non disegna niente
- Altrimenti
    - Disegna il cerchio specificato
    - Disegna ricorsivamente altri 4 cerchi
    - Spostati in orizzontale e in verticale di $\pm r$
    - Con raggio ridotto al 42% ($\sqrt{2}-1$)

---

![](https://fondinfo.github.io/images/fun/matryoshka.png)
# 8.2 Somma ricorsiva di cifre

- Funzione *ricorsiva* `sum_digits`
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

![](http://fondinfo.github.io/images/misc/numbers.png)
# 8.3 Cifra di controllo

- Funzione `is_valid(digits)`
    - Stringa di cifre → `bool`
    - `ValueError` se vuota o con altri caratteri
- Algoritmo di Luhn (carte di credito…)
    - A partire dalla *2ᵃ da destra*, verso sinistra, raddoppiare una cifra sì e una no <br> (se supera 9, sottrarre 9)
    - Valido se somma di tutte le cifre è multipla di 10
- In `main`, chiedere righe fino a riga vuota; mostrare se ognuna è valida
- Opzionale: `check_digit`, che calcola la cifra da aggiungere in fondo

>

Es. `"79927398713"` è valido (somma 70); `"79927398710"` no (67)
<br>
Es. `check_digit("7992739871")` → `3`
<br>
Utile: `enumerate` e `reversed`, per avere a disposizione cifra e posizione

---

![large](https://fondinfo.github.io/images/fun/sin-cos.png) ![](https://fondinfo.github.io/images/misc/interpolation.svg)
# 8.4 Classe FastSin

- Classe `FastSin`
    - Alla creazione, precalcola `sin` per gli angoli interi 0-359° (lista di 360 valori)
- Metodo `eval`, con param. $x$ in gradi
    - $x$: `float`, anche $<0$ o $>360$
- `eval` approssima `sin` con *interpolazione lineare*
    - $v = (1-f) \cdot v_i + f \cdot v_j$
    - $f$: parte frazionaria di $x$
    - $i$: parte intera di $x$ (0-359)
    - $j$: successore di $i$ (dopo 359, 0);
- Confrontare `eval` con `math.sin`

>

<https://fondinfo.github.io/slides/p12-basi.html#/30>

---

![](https://fondinfo.github.io/images/games/minesweeper.svg)
# 8.5 Mines

- Chiedere all'utente numeri $w, h, n$
- Creare matrice $w×h$ con…
    - Esattamente $n$ valori 1 (💣) in posizioni casuali
    - Altre celle a 0
- Salvare matrice in file `output.csv`
- Chiedere una posizione per riga, fino a riga vuota
    - Posizione: coppia $(x, y)$ con spazio separatore
- Per ogni posizione, comunicare:
    - Se la cella contiene 1 (💣)
    - Altrimenti, quanti 1 ci sono *intorno* (in orizzontale, verticale e diagonale)

---

# 8.6 Tutti sotto soglia

- Funzione *ricorsiva* `all_below`
    - Parametri: una lista di numeri $data$ e un numero $limit$
    - Controllare che tutti i numeri in $data$ siano minori della soglia $limit$
- Algoritmo:
    - Una lista vuota non ha valori sopra la soglia
    - Altrimenti, separare il primo elemento *head* dal resto della lista *tail*
    - Se *head* non è minore di $limit$, risultato *falso*
    - Altrimenti, infine, controllare gli altri valori

>

Saranno accettate solo le soluzioni ricorsive

---

![](https://fondinfo.github.io/images/draw/rec-cross.svg)
# 8.7 Quadrati a croce

- Funzione *ricorsiva* `rec_squares`
    - Parametri: $p$, $s$, $depth$, $skipdir$
- Se $depth$ è 0, non disegna niente
- Altrimenti, disegna il quadrato di lato $s$ centrato in $p$
    - Poi 4 quadrati *adiacenti* (destra, sinistra, sopra, sotto), con lato $s/2$ e livello $depth - 1$
    - Non disegnare dalla parte del quadrato di provenienza
- Colore in base al livello (palette globale casuale, ~ es. 7.5)
- In `main`: canvas 400×400, centro $(200, 200)$, lato 120, $depth$ 4

>

Centro dei 4 quadrati: spostato di ¾·s nella direzione scelta
<br>
Direzioni come tuple $(\pm 1, 0)$, $(0, \pm 1)$; per il primo quadrato, nessuna da evitare: $(0, 0)$
<br>
Stesso colore per quadrati della stessa dimensione
<br>
Saranno accettate esclusivamente le soluzioni ricorsive

---

![](https://fondinfo.github.io/images/games/nurikabe.svg)
# 8.8 Nurikabe, regole [P2]

- Metodo `finished`: vero solo se tutte e 4 le regole sono rispettate
- Celle nere tutte connesse (in orizzontale e verticale)
    - Cercare con la ricorsione l'*area contigua* di una cella nera (come `find_area`)
    - Confrontarne la dimensione col numero totale di celle nere
- Ogni *area* contigua di celle bianche ha un solo numero, uguale alla sua dimensione (num. di celle)
- Considerare nere solo le celle annerite: le altre sono bianche

>

<https://fondinfo.github.io/play/?c11_findarea.py>

---

![](https://fondinfo.github.io/images/games/nurikabe.svg)
# 8.9 Nurikabe, automatismi [P2]

- *“Isola marcata”* : numero e marcature • adiacenti
- Automatismo tasto `w`, *opzionale*
    - Marcare • (*bianca*) la cella libera…
    - Quarta di un quadrato 2×2 con 3 nere, o…
    - Unica adiacente a un'*isola marcata* incompleta
    - …
- Automatismo tasto `b`, *opzionale*
    - Annerire ■ (*nera*) la cella libera…
    - Adiacente a un'*isola marcata* completa, o…
    - Adiacente a due *isole marcate* (le unirebbe), o…
    - Non raggiungibile da nessun numero
    - …

>

Alcuni schemi si risolvono ripetendo `b` e `w`, finché non cambia più nulla
<br>
<https://www.conceptispuzzles.com/index.aspx?uri=puzzle/nurikabe/techniques>

---

# Esercitazione 9 (2026-11-23)

---

# 9.1 Matrice simmetrica

- Leggere da un file CSV una matrice quadrata di interi
    - Inoltre, $\forall$ riga, stessa lunghezza
    - Se non è quadrata, sollevare `ValueError` con messaggio
- Salvare in un file `transposed.csv` la matrice *trasposta*
    - Righe e colonne scambiate
- Verificare se è *simmetrica*
    - Cella $(x, y)$ sempre uguale alla cella $(y, x)$
    - Altr., mostrare *prima* cella $(x, y)$ in ordine di riga diversa da $(y, x)$
    - Mostrare entrambi i valori

``` txt
1,2,3        1,4,7
4,5,6   →    2,5,8
7,8,9        3,6,9
```

>

Per il primo esempio: cella $(1, 0)$ vale `2`, ma $(0, 1)$ vale `4`

---

# 9.2 Matrice a serpentina

- Chiedere all'utente le dimensioni $w$ e $h$ di una matrice
- Riempirla con i numeri da $1$ a $w \cdot h$, *a serpentina*
    - Prima riga da sinistra a destra
    - Seconda riga da destra a sinistra
    - E così via, alternando il verso
- Mostrare la matrice a console, con le colonne incolonnate

``` txt
w = 4, h = 3

 1   2   3   4
 8   7   6   5
 9  10  11  12
```

>

Usare una lista semplice: cella $(x, y)$ in posizione $x + y \cdot w$

---

# 9.3 Conteggio parole

- Leggere il contenuto del file `g2d.py` e ottenerne le parole
- *V1* : Separazione con qualsiasi carettere bianco
    - Contare le occorrenze di tutte le parole trovate
    - Mostrare le 10 parole più comuni assieme ai relativi conteggi
- *V2* : Ripetere le operazioni, separando le parole con *regex*:
    - `words = re.split(r"\W+", text)` <br> <br>
- Poi, usando gli insiemi su *V2*
    - Quante parole *distinte* ci sono in `g2d.py`? Quante in `license.txt`?
    - Quante sono presenti solo in `g2d.py` e non in `license.txt`?
    - Infine, tra le parole presenti in *entrambi* i file… <br> mostrarne le prime 10, in ordine alfabetico

---

![](https://fondinfo.github.io/images/fun/matryoshka.png)
# 9.4 Liste annidate, più lunga

- Definire una funzione *ricorsiva* `find_max`
    - Parametro: semplice stringa o lista annidata di stringhe
    - Risultato: stringa più lunga, anche nelle liste annidate
    - In caso di parità, la prima in ordine alfabetico
- Una stringa semplice coincide con il risultato
- In una lista, si applica la ricerca (ricorsivamente) a ogni elemento
- Esempio : `["Ann", ["Bart", ["Carol", "Cindy"], "Bob", "Art"], ["Bea"], "Bill"]`
    - → Risultato: *Carol*

---

![](https://fondinfo.github.io/images/repr/file-system.svg)
# 9.5 Profondità albero

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

![](https://fondinfo.github.io/images/draw/sierpinski-carpet.svg)

# 9.6 Tappeto di Sierpinski

- Funzione ricorsiva `carpet` con parametri:
    - Angolo in alto a sinistra $(x, y)$, lato $s$, livello $i$
- Se $i = 0$, non disegna niente
- Altrimenti, divide il quadrato in 3×3 di lato $\frac{s}{3}$
    - Disegna quello *centrale* in bianco
    - Sugli altri 8, stesso procedimento con livello $i - 1$
- In `main`, canvas grigio scuro di lato 532 e bordo 10
    - Tappeto da $(10, 10)$, lato 512, livello 4
- In aggiunta, *palette* globale di 16 colori casuali
    - A livello $i$, quadrato *centrale* di colore $i$ dalla *palette*

---

# 9.7 Tutti sotto soglia, con indice

- Riprendere `all_below` (es. 8.6)
    - Aggiungere terzo parametro $start$ (predefinito `0`)
    - Controllare gli elementi in $data$ dalla posizione $start$ in poi
- *Senza spezzare la lista* e senza *slice* : $start$ indica *head*, i successivi sono *tail*
    - Se $start$ è oltre l'ultimo indice → *vero*
    - Se il valore in $start$ non è minore di $limit$ → *falso*
    - Altrimenti, ricorsione con $start + 1$
- Esempi
    - `all_below([9, 2, 4], 5)` → `False`
    - `all_below([9, 2, 4], 5, 1)` → `True`

>

Niente `head, *tail = data`: la lista non viene copiata, cambia solo `start`
<br>
Da `main`, chiamare la funzione senza fornire `start` (`=0`)
<br>
Saranno accettate solo le soluzioni ricorsive

---

![](https://fondinfo.github.io/images/misc/dead-end.jpg)
# 9.8 Nurikabe, vicolo cieco [P2]

- Metodo booleano `wrong`, senza parametri
    - Controlla se le annotazioni inserite impediscono la soluzione del gioco
    - Può restituire `False` anche se la partita non è finita (celle ancora non marcate)
- Esempi
    - Quadrato 2×2 di celle nere
    - Isola marcata: contenente due numeri, oppure più grande del suo numero
    - Isola marcata senza celle libere adiacenti: incompleta, o senza numero
    - Gruppo isolato di celle nere senza celle libere adiacenti

>

*Non si può risolvere il gioco senza rimuovere una annotazione*
<br>
<https://www.conceptispuzzles.com/index.aspx?uri=puzzle/nurikabe/techniques>

---

![](https://fondinfo.github.io/images/games/nurikabe.svg)
# 9.9 Nurikabe, test [P2]

- Creare degli *unit test* per il gioco Nurikabe
    - Usare il modulo `unittest`
- Verificare il gioco dopo varie chiamate a `play`
    - Usare `read` per osservare lo stato
    - Le celle con numero non devono cambiare
- Verificare il funzionamento di `finished` rispetto alle regole
    - Nessun quadrato 2×2 di celle nere
    - Celle nere tutte contigue
    - Ogni area bianca con un solo numero, della dimensione giusta
- Verificare `wrong` su alcune configurazioni sbagliate

>

<https://fondinfo.github.io/slides/p34-collaudo.html#/16>
<br>
<https://fondinfo.github.io/play/?c21_fifteentest.py>

---

# Esercitazione 10 (2026-11-30)

---

![](https://fondinfo.github.io/images/fun/matryoshka.png)
# 10.1 Palindromo, con indice

- Funzione *ricorsiva* `is_palindrome`: testo e indice $start$ (predefinito $0$), risultato `bool`
    - *Palindromo*: testo uguale se letto al contrario
- *Senza creare nuove stringhe* (niente *slice*): <br> confrontare caratteri in $start$ e $-1 - start$
    - Se $start$ ha raggiunto la metà del testo: *vero*
    - Se i due caratteri sono diversi: *falso*
    - Altrimenti, controllare con $start + 1$
- Da `main`, chiedere righe fino a riga vuota; mostrare il risultato

---

# 10.2 Percorsi delle pagine

- Riprendere l'albero di dizionari `site` negli esempi (`"title"`, e `"children"` assente nelle foglie)
- Funzione *ricorsiva* `leaf_paths(node, prefix="")`
    - Risultato: lista dei percorsi dalla radice a ogni *foglia*, titoli separati da `"/"`
    - Ordine di visita: dall'alto verso il basso, da sinistra a destra
- Es. per `site`: `["Home/News/2026", "Home/News/Archive", "Home/About"]`
- In `main`, mostrare i percorsi, uno per riga

---

![](https://fondinfo.github.io/images/draw/rot-squares.svg)
# 10.3 Quadrati inscritti

- Funzione *ricorsiva* `inscribed`: lista $pts$ dei 4 vertici (tuple), livello $i$
- Se $i = 0$, non disegna niente
- Altrimenti
    - Disegna il *contorno* con `g2d.draw_polygon`, colore $(20 \cdot i, 0, 255 - 20 \cdot i)$
    - Nuovo quadrato inscritto: vertici a $⅕$ del lato, da ogni vertice verso il successivo
    - Stesso procedimento, livello $i - 1$
- In `main`, canvas 500×500: quadrato dell'intero canvas, livello 12

>

Per il solo contorno, indicare lo spessore in `set_color`

---

# 10.4 Frequenza di n-grammi

- Leggere per intero il file “`license.txt`”
- Ottenere le parole, in minuscolo, formate di sole lettere
- Contare i *bigrammi*: coppie di lettere consecutive, nella stessa parola
    - Es. “`copy`” contiene `co`, `op`, `py`
- Mostrare i 5 bigrammi più frequenti, con i relativi conteggi
- Estensione: chiedere all'utente la lunghezza $n$ dei gruppi
    - Contare *n-grammi* (con $n = 3$: “`cop`”, “`opy`”)

``` py
import re
words = re.findall(r"[a-z]+", text.lower())
```

>

Con una *slice* `word[i:i + n]` si estrae il gruppo che inizia in $i$

---

# 10.5 Celle libere al contorno

- Leggere matrice da file CSV, con soli valori 0, 1 e 2
    - 0 = cella libera, 1 = area da cercare, 2 = cella bloccata
- Funzione *ricorsiva* simile a `find_area` negli esempi
    - `find_border(board, x, y, area=None, border0=None)`
    - Memorizza in $border0$ l'insieme delle coordinate delle celle con valore 0 direttamente adiacenti all'area
- In `main`, chiedere le coordinate $(x, y)$ di partenza
    - Mostrare la matrice e marcare le celle di bordo a 0 trovate

``` txt
2,0,1,2        2,*,1,2
0,1,1,2   →    *,1,1,2
2,0,2,0        2,*,2,0
```

---

# 10.6 Pagare con le monete

- Funzione *ricorsiva* `pay(coins, amount)`
    - $coins$: singole monete disponibili, con possibili ripetizioni
    - Risultato: lista di monete (ciascuna usabile al più una volta) con somma $amount$, precisa senza resto, oppure `None`
- Se $amount$ è $0$, lista vuota; senza monete, `None`
- Altrimenti, separare la prima moneta *head* dalle altre *tail*
    - Se $head ≤ amount$, provare a pagare $amount - head$ con *tail*
    - Se non si riesce, provare solo con *tail*, stesso $amount$
- In `main`, chiedere monete tutte su una riga e poi importo su altra riga

>

Es. con `[5, 2, 2, 10, 1]`: 9 → `[5, 2, 2]`; 18 → `[5, 2, 10, 1]`; 21 → `None`
<br>
Attenzione: la lista vuota è un risultato valido, da distinguere da `None`

---

![](https://fondinfo.github.io/images/misc/artificial-intelligence.png)
# 10.7 Nurikabe, suggerimenti [P2]

- Cercare automaticamente la prossima mossa
    - Ragionamento simile a giocatore umano
    - Avviare la ricerca col tasto `a`
- *Provare* ad annerire una cella non annotata
    - Applicare automatismi (es. 8.9) e `wrong` (es. 9.8)
    - Se le regole sono violate (`wrong`), inserire un •
- *Provare* un • in una cella non annotata
    - Applicare automatismi e `wrong`
    - Se le regole sono violate (`wrong`), annerire la cella

>

Se invece un'ipotesi non risulta `wrong`, non è detto che sia giusta; non si possono trarre conclusioni!

---

# 10.8 Nurikabe, altri suggerimenti [P2]

- Considerare ogni cella non annotata, singolarmente
- *Provare ad annerire*
    - Applicare automatismi
- *Provare a marcare •*
    - Applicare automatismi
- *Confrontare* tutte le annotazioni, aggiunte nei due casi
    - Se una qualsiasi cella diventa *nera* in entrambe le ipotesi ⇒ *nera* nel gioco
    - Se una qualsiasi cella diventa • in entrambe le ipotesi ⇒ • nel gioco

---

# 10.9 Nurikabe, soluzione logica [P2]

- Permettere di inizializzare il gioco da un file di testo
    - Usare gli schemi in `nurikabe-games.zip` su Elly
- Provare inoltre a risolvere quegli schemi automaticamente
    - Per ogni mossa, applicare i suggerimenti
    - Suggerimenti degli es. 10.7 e 10.8
- Ricordarsi…
    - Inizializzare la partita da uno dei *file* forniti (parametro)
    - Preparare vari *unit test*, per le principali funzionalità
    
<https://elly2026.didattica.unipr.it/mod/resource/view.php?id=69111>
<br>
<https://www.syndicatedpuzzles.com/Nurikabe_Sample_Pack.pdf>
