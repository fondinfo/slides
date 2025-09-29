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

![](https://fondinfo.github.io/images/misc/random-circles.svg)
# 1.3 Cerchi casuali

- Chiedere all'utente un numero `n`
- In un canvas 500×500, disegnare `n` cerchi
    - Tutti con raggio di 50 pixel
    - Ciascuno con posizione casuale e colore casuale
    - Con centro all'interno del canvas

>

Cominciare a disegnare un solo cerchio, in posizione casuale

---

![](https://fondinfo.github.io/images/misc/shadowed-squares.svg)
# 1.4 Quadrati con ombra

- Chiedere all'utente un numero `n`
- In un canvas 500×500, disegnare `n` quadrati
	- Tutti di lato 50
    - Ciascuno con posizione e colore casuale
    - Ciascuno con un ombra grigia spostata a destra e in basso di 5 pixel

>

Fare in modo che i quadrati e le ombre siano completamente all'interno nel canvas

---

![](https://fondinfo.github.io/images/misc/shadows.png)
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

![large](https://fondinfo.github.io/images/misc/center-target.svg)
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

