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

