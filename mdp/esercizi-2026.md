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
- Memorizza la direzione in un campo `angle`
- Metodo `move`
    - Aggiornare la posizione
    - Ogni 2 frame, incrementare `angle` di `90/8`
    - Ogni 64 frame, passare da rotazione oraria a antioraria e viceversa
- Metodo `sprite`
    - Ritagliare l'immagine da [`super-sprint.png`](https://fondinfo.github.io/sprites/super-sprint.png)
    - Scegliere l'immagine in base al valore attuale del campo `angle`
