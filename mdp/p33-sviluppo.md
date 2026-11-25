![](http://fondinfo.github.io/images/dev/bug-feature.png)
# Sviluppo del software
## Introduzione alla programmazione

---

![large](http://fondinfo.github.io/images/dev/waterfall-model.svg) Waterfall model
# 🌱 Ciclo di vita a cascata

- **Analisi**
    - Modello, requisiti, fattibilità
- **Progetto e implementazione**
    - Componenti architetturali... dettaglio classi
- **Collaudo**
    - Rispetto requisiti, qualità sw
- **Rilascio e manutenzione**
    - 40%-80% del costo totale (DoD, HP)
    - Non noti o non colti correttamente i requisiti
    - Cambiano le condizioni operative …

>

[Winston W. Royce, 1970](https://univpr-my.sharepoint.com/:b:/g/personal/michele_tomaiuolo_unipr_it/EQfW_uuaEK1CqznE8JhlhPYB_0to41SqFooYximIZLitxw?e=Znuk0A) - [Robert L. Glass, 2001](http://www.eng.auburn.edu/~kchang/comp6710/readings/Forgotten_Fundamentals_IEEE_Software_May_2001.pdf)

---

![large](http://fondinfo.github.io/images/dev/rup-cycle.png)
# 🌱 Evoluzione di un software

- Evoluzione ineliminabile per molti sistemi
    - Prestazioni, qualità, funzionalità (manutenzione *perfettiva*, ~60%)
    - Anomalie ed errori (manutenzione *correttiva*, ~20%)
    - Mutamenti dell’ambiente (manutenzione *adattativa*, ~20%)
- Sviluppo iterativo e metodologie agili
    - Rilascio frequente e incrementale
    - <http://agilemanifesto.org/>

---

![large](http://fondinfo.github.io/images/dev/programmer.svg)
# 🌱 Qualità del software

- Le qualità su cui si basa la valutazione di un sistema software possono essere:
    - **Interne**, riguardano le caratteristiche legate al **processo** di sviluppo e non sono direttamente visibili agli utenti
    - **Esterne**, riguardano le funzionalità fornite dal **prodotto** sw e sono direttamente visibili agli utenti
- Le categorie sono legate:
    - *Product quality is process quality*

---

# ⭐ Qualità esterne

- **Correttezza e affidabilità**: il sistema rispetta le specifiche, in maniera assoluta o con una certa probabilità
- **Robustezza**: il sistema si comporta in modo ragionevole anche fuori dalle specifiche
- **Efficienza**: usa bene le risorse di calcolo
- **Scalabilità**: migliori prestazioni con più risorse
- **Sicurezza**: riservatezza, autenticazione, autorizzazione, accounting
- **Usabilità**: interfaccia utente permette di interagire in modo naturale

---

# ⭐ Qualità interne

- **Verificabilità**: sistema basato su modello formale
- **Riusabilità**: parti per costruire nuovi sistemi
- **Manutenibilità**: riparabilità, evolvibilità (nuove specifiche), adattabilità (cambiamenti ambiente)
- **Interoperabilità**: capacità di co-operare con altri sistemi, anche di altri produttori
- **Portabilità**: adatto a più piattaforme hw/sw
- **Comprensibilità**: codice leggibile, documentato
- **Modularità**: interazione tra componenti coesi

---

![](http://fondinfo.github.io/images/dev/gearwheel.png)
# 🌱 Specifiche

- Rispetto a cosa valutiamo **correttezza** o **affidabilità** di un programma?
- Idea del programmatore
    - Non formulata, non documentata
    - Incompleta, mutevole, facilmente dimenticata
- Specifiche (formali o informali)
    - Formulate, scritte, studiate e condivise <br> → Parte del progetto e del programma
    - Spec. assiomatiche: espressioni logiche o asserzioni <br> → **Precondizioni, postcondizioni e invarianti**

---

# 🌱 Pre- e post-condizioni

- **Precondizioni**
    - Stabiliscono se è possibile chiamare un metodo
    - Prerequisiti per l’attivazione
- **Postcondizioni**
    - Stabiliscono se il metodo restituisce il valore atteso, cioè se produce l’effetto desiderato
    - … In relazione ai parametri (che soddisfano le precondizioni)
    - Definiscono il significato del metodo
- **Divisione delle responsabilità** tra moduli
    - Errore del codice *chiamante* (*client*) se precondizioni non soddisfatte
    - Errore del codice *chiamato* (*server*), se postcondizioni non soddisfatte

---

# 🌱 Responsabilità e contratti

- **Precondizioni + postcondizioni = contratto**
    - … tra modulo chiamante e modulo chiamato
- Infrazione di un contratto: problema serio
    - Errore rispetto alle specifiche
    - Eccezione e/o terminazione
- No **divisione responsabilità** → sovrapposizioni
    - Tutti i moduli assumono molte responsabilità
    - *Programmazione difensiva*: tutte le parti del programma controllano tutte le condizioni
    - Grosso programma → ancora più grosso

---

# 🛠️ Esempio di contratto

``` py
def sqrt(x: float) -> float
```

- Precondizioni: `x >= 0`
- Postcondizioni: `abs(result * result - x) <= 0.00001`
- Codice chiamante
    - Obblighi: deve passare un numero non negativo
    - Benefici: riceve la radice del numero
- Codice chiamato
    - Obblighi: restituisce un numero `r` tale che `r * r ≃ x`
    - Benefici: può assumere che `x` non è negativo

---

![](http://fondinfo.github.io/images/qt/fifteen-puzzle.jpg)
# 🛠️ Invariante di classe

- Vincolo sullo stato interno di un oggetto
    - Per tutto il ciclo di vita, per ogni stato *stabile*
    - Soddisfatto dal costruttore e dai metodi pubblici
    - Ma non per forza dai metodi privati
- “*Criterio di sanità*” dell’oggetto
    - Rafforzamento di pre- e post-condizioni
- Es.: classe per il *Gioco del Quindici*
    - Posizione `x` della cella vuota: sempre tra `0` e `cols-1`
    - Posizione `y` della cella vuota: sempre tra `0` e `rows-1`
    - In quella posizione è sempre memorizzato il valore `0`

---

# ⭐ Ereditarietà e contratti

![](http://fondinfo.github.io/images/dev/contract-inherit.svg)

- ❓ *Che relazione c’è tra le asserzioni di una classe e quelle dei suoi discendenti?*

---

# ⭐ Principio di sostituibilità

- Polimorfismo: possibile esecuzione metodo di una sottoclasse, anziché della classe base
    - I metodi delle sottoclassi possono ridefinire i metodi delle classi base... ma non arbitrariamente
- I contratti della sottoclasse devono *rispettare i contratti della classe base* (“sottocontratti”)
    - *Precondizioni* : non devono essere più forti
    - *Postcondizioni* : non devono essere più deboli
    - *Invarianti di classe* : non devono essere più deboli

> Require no more, promise no less

---

# 💡 Design by contract

- Paradigma proposto nel linguaggio *Eiffel* (Bertrand *Meyer*, 1986)
- Uso di asserzioni in varie fasi di sviluppo
    - *Progetto* : approccio pragmatico alle specifiche
    - *Implementazione* : guida per la programmazione
    - *Documentazione* : interfacce con info aggiuntive
    - *Collaudo* : DbC delimita i casi da testare (per affidabilità)
    - *Manutenzione* : DbC fa emergere prima gli errori
    - *Uso finale* : sollevate eccezioni se violazioni

---

# 🛠️ Asserzioni Python

- Espressioni booleane, simili a predicati matematici
- Esprimono proprietà semantiche di classi e metodi
- Utili per collaudo e debugging, ma anche documentazione
    - Esprimono l'intenzione del programmatore
- Violazione → **AssertionError**
    - Normalmente: *abort*, terminazione programma

``` py
assert age > 0
```

---

# 🛠️ Asserzioni e contratti

- Asserzioni in genere utili per:
    - Precondizioni, postcondizioni, invarianti di classe
    - Invarianti interne e di controllo del flusso
- Argomenti di metodi pubblici sbagliati → eccezione
    - `ValueError` o `TypeError`
- Di solito, asserzioni usate per debug, ma disabilitate in produzione
    - `python -O some_code.py`

---

# 🛠️ Pre- e post-condizioni

``` py
def sqrt(x: float) -> float:
    '''
    Precondition: x >= 0
    Postcondition: abs(result * result - x) <= 0.00001
    '''
    if x < 0:
        raise ValueError("sqrt: arg < 0")

    # ...

    assert abs(result * result - x) <= 0.00001
    return result
```

---

# 🛠️ Eccezioni

- Oltre a parametri sbagliati, varie situazioni inattese
- **try** per gestire separatamente queste situazioni
- In caso di errore in `try`, esecuzione si interrompe subito
- Viene eseguito il blocco `except`

``` py
x = None
while x is None:
    try:
        x = int(input("Please enter a number: "))  # ValueError?
        print("That's fine")
    except:
        print("Oops! That was not a valid number. Try again...")
print("The square is", x ** 2)
```

---

# 🥷 Eccezioni diverse

- In `try` possibili diversi tipi di errori
- Seguito da vari blocchi `except`
- Se manca gestore errore, il programma termina bruscamente

``` py
try:
    x = float(input("Please enter a number: "))  # ValueError?
    y = 1 / x
    print("Inverse: ", y)
except ValueError:
    print("Oops! That was not a valid number.")
except ZeroDivisionError:
    print("Oops! Cannot divide by 0.")
```

---

# Verifica e validazione

---

![large](http://fondinfo.github.io/images/dev/v-model.svg)
# 🌱 Verifica e validazione

- Mostrare che il sistema...
    - È conforme alle specifiche
    - Soddisfa i bisogni dell’utente

> Verification: Are we building the product right? <br> Validation: Are we building the right product? <br> *(Barry  Boehm)*

- Comprende revisione e collaudo del sistema
- **Test case**, derivati dalle specifiche

---

![large](http://fondinfo.github.io/images/dev/first-bug.jpg) Report del primo “bug” <br> Gruppo di Grace Hopper
# 🌱 Costo dei bug

- Scovare bug, difficile e frustrante 😫
    - Testing: ~ 20-40% costi di un progetto
    - Tempo e risorse
- B. Boehm: **far emergere** bug in prime fasi dello sviluppo!
    - Se trovare un problema in fase di specifica dei requisiti costa 1$...
    - 5$ in progetto
    - 10$ in programmazione
    - 20$ in unit testing
    - Fino a 200$ dopo consegna
    - Molti errori già in specifica requisiti

>

[nationalgeographic.org](https://www.nationalgeographic.org/thisday/sep9/worlds-first-computer-bug)
–
[newyorker.com](https://www.newyorker.com/magazine/2018/12/10/the-friendship-that-made-google-huge)

---

# 💡 Prove formali

- Dimostrazione matematica di un programma
    - Alternativa (~ accademica) al testing
    - Annotazione del programma con asserzioni matematiche: comportamento atteso
    - Proprietà valide per i vari costrutti del programma
    - Spesso per *linguaggi funzionali* (privi di effetti collaterali)
- Prova che post-condizioni verificate, se:
    - Precondizioni verificate
    - Programma termina
- Dimostrazioni automatiche
    - Se a mano → errori (più che nel programma?)

>

<https://coq.inria.fr/about-coq>

---

# ⭐ Revisione del software

- Analisi del codice da parte di *colleghi* 🧐
    - Per valutarne caratteristiche e funzionalità
- **Code walk-through**
    - Selezione porzioni di codice e valori di input
    - Simulazione su carta comportamento del sistema
- **Code inspection**, più formale e focalizzato
    - Uso di variabili non inizializzate
    - Loop infiniti
    - Letture di porzioni di memoria non allocata
    - Rilascio improprio della memoria
