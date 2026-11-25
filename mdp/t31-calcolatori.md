![](http://fondinfo.github.io/images/sys/motherboard-example.jpg)
# Calcolatori
## Introduzione all'informatica <br> Michele Tomaiuolo @ Ingegneria UniPR

---

![](http://fondinfo.github.io/images/hist/1837-analytical-engine.jpg)
# 💡️ Calcolatore

- Macchina *programmabile*
    - Memorizza ed elabora automaticamente…
    - Dati in formato discreto (I/O)…
    - Secondo istruzioni di un programma
- Diversi *modelli di calcolo*
    - Operazioni elementari e concetto di algoritmo
    - Def. calcolabilità: problema risolvibile, o no
- 1837, Charles Babbage, *Analytical Engine*
    - Solo progetti: ALU, CU, memoria, base decimale
    - Modello “Turing completo” con *branching* e *loop*
    - Ada Lovelace, “programma” per numeri di Bernoulli

---

![](http://fondinfo.github.io/images/hist/zuse.jpg) ![](http://fondinfo.github.io/images/hist/eniac.jpg)
# 💡️ Primi calcolatori

- 1941, *Z3* (Berlino, Konrad Zuse)
    - Primo calcolatore programmabile
    - Float binari, senza salti, a *relè*
    - Programma su nastro, memoria scarsa
- 1946, *ENIAC* (Philadelphia)
    - Base 10, branching, programma a cavi
    - 6 programmatrici: Jean Bartik, Kay McNulty, Betty Snyder…
- Impulso da *WWII* e Guerra Fredda
    - Balistica, meteo, Manhattan project, bomba H…

---

![](http://fondinfo.github.io/images/hist/von-neumann.jpg) ![](http://fondinfo.github.io/images/sys/von-neumann-architecture.svg)
# 💡️ Architettura di von Neumann

- Dati e codice in *Random Access Memory*
    - Modello teorico UTM (Turing, 1936)
    - Ma RAM → *salti*, *branching*, *subroutine*
- 1945, JvN: “*Draft di report per EDVAC*”
    - 1951, seguito di ENIAC, consulenza JvN
    - Progetti di Eckert & Mauchly @ UPenn
- 1948, *SSEM* o *Manchester “baby”*
    - Dati e programmi in memoria RAM
    - → 1949, Mark 1

>

[Henin (2013). “Il programma memorizzato”. Mondo digitale #46.](https://www.dropbox.com/s/iayjm8k60o1vf9z/06_Henin.pdf?dl=1)

---

# 💡️ Computer girls

![large](http://fondinfo.github.io/images/hist/women-in-cs.jpg)

>

Grace Hopper, Margaret Hamilton — Donne in corsi CS: 37%, 1983 → 18%, 2013

---

# ⭐ Central Processing Unit

- CPU: “cervello” del calcolatore
    - Esegue i programmi
    - Comanda le altre parti del calcolatore
- Composta da due parti:
    - **Control Unit (CU)**: interpreta le istruzioni, comanda le altre parti della CPU, controlla il flusso tra CPU e memoria
    - **Arithmetic Logical Unit (ALU)**: esegue le operazioni aritmetiche e logiche, esegue i confronti tra dati

---

# ⭐ Architettura CPU

![large](http://fondinfo.github.io/images/sys/cpu-architecture.svg)

---

![](http://fondinfo.github.io/images/sys/settling-time.svg) ![](http://fondinfo.github.io/images/sys/propagation-delay.png)
# 🔬 Circuiti logici sincroni

- Ritardo di commutazione delle porte logiche
    - Passaggio `0→1 / 1→0`
    - Transizione segnale ≠ gradino
    - Ritardo, overshooting, ringing
    - Per capacità e induttanze parassite
- *Clock* regola l'intero circuito
    - Tempo per stabilizzare tutti i segnali

---

# ⭐ Ciclo principale della CPU

- **Caricamento**: CU preleva l’istruzione dalla locazione di memoria indicata dal registro PC (Program Counter) e la memorizza in IR (Instruction Register)
- **Decodifica**: CU interpreta l’istruzione, legge eventualmente dalla memoria i dati necessari
- **Esecuzione**: CU comanda le parti
- **Memorizzazione**: risultati memorizzati nella memoria centrale o in registri della CPU

---

# ⭐ Lettura dalla memoria

![large](http://fondinfo.github.io/images/sys/cpu-memory.svg)

---

# 🔬 Sequenza di lettura

![large](http://fondinfo.github.io/images/sys/cpu-read-1.svg)

---

# 🔬 Sequenza di lettura

![large](http://fondinfo.github.io/images/sys/cpu-read-2.svg)

---

# 🔬 Sequenza di scrittura

![large](http://fondinfo.github.io/images/sys/cpu-write-1.svg)

---

# 🔬 Sequenza di scrittura

![large](http://fondinfo.github.io/images/sys/cpu-write-2.svg)

---

# 🔬 Fetch istruzioni

![large](http://fondinfo.github.io/images/sys/cpu-fetch.svg)

---

# 🔬 Interpretazione istruzioni

- Al termine della fase di *fetch*, IR contiene l'istruzione da eseguire
    - **Codice operativo + operandi**
    - *Linguaggio macchina*: il significato dipende dalla CPU
- Nell'esempio: **`5`** `012$_{hex}$` = **`0101`** `0000 0001 0010$_{bin}$`
    - Codice operativo = **`0101$_{bin}$`**
    - Es. Leggi una parola dal registro accumulatore...
    - E memorizzala in un indirizzo di memoria (operando)

---

# 🔬 Esecuzione istruzioni

![large](http://fondinfo.github.io/images/sys/cpu-exec.svg)

---

# ⭐ Mini-ISA didattica (16 bit)

- **Parole a 16 bit** (4 cifre hex): 4 bit *op-code* + 12 bit operando
    - Operandi a 12 bit (`xxx` / `vvv`): estensione del segno (MSB) a 16 bit
- **Registri**: `PC`, `IR`, `ACC` (accumulatore), `R0`–`R3` (4 registri generali)

| Hex | Mnemonico | Operazione | Note |
| :--- | :--- | :--- | :--- |
| **`100r`** | `MOV ACC, Rr` | `ACC ← Rr` | Copia `Rr` in `ACC` (`r` ∈ `0..3`) |
| **`200r`** | `MOV Rr, ACC` | `Rr ← ACC` | Copia `ACC` in `Rr` (`r` ∈ `0..3`) |
| **`3vvv`** | `LDI vvv` | `ACC ← sext(vvv)` | Load immediato (costante 12 bit) |
| **`4xxx`** | `LOAD xxx` | `ACC ← MEM[xxx]` | Carica da RAM in `ACC` |
| **`5xxx`** | `STORE xxx` | `MEM[xxx] ← ACC` | Salva `ACC` in RAM |
| **`6xxx`** | `JMP xxx` | `PC ← xxx` | Salto incondizionato |
| **`7xxx`** | `JZ xxx` | se `ACC == 0`, `PC ← xxx` | Salto se zero |
| **`800r`** | `ADD Rr` | `ACC ← ACC + Rr` | Somma `Rr` ad `ACC` |
| **`900r`** | `SUB Rr` | `ACC ← ACC - Rr` | Sottrae `Rr` da `ACC` |
| **`A00r`** | `MUL Rr` | `ACC ← ACC * Rr` | Moltiplicazione intera |
| **`B00r`** | `DIV Rr` | `ACC ← ACC / Rr` | Divisione intera |

---

![large](http://fondinfo.github.io/images/sys/motherboard.svg)
# ⭐ Architettura PC

![small](http://fondinfo.github.io/images/sys/motherboard-example.jpg)

- *Northbridge*, ora integrato nella CPU
    - Graphics & Memory Controller Hub (GMCH) : ~ 50 GB/s
- *Southbridge*, o “chipset”
    - Dischi e periferiche di I/O : ~ 500 MB/s

---

![large](http://fondinfo.github.io/images/sys/flynn.svg)
# ⭐ Classificazione di Flynn

- **Parallelismo**: ↑ prestazioni, a parità di velocità su singola istruzione
    - S/M: single/multiple
    - I/D: instruction/data
- *SISD*: una operazione alla volta; macchine tradizionali a singolo processore e core
- *MISD*: insolite, per tolleranza ai guasti; sistemi eterogenei, sugli stessi dati, devono dare gli stessi risultati
- *SIMD*: operazioni naturalmente parallelizzabili; unità di calcolo vettoriale e GPU
- *MIMD*: istruzioni diverse su dati diversi; architetture con più core o processori autonomi, sistemi distribuiti

---

# ⭐ Assembler

- **Linguaggio macchina**: definisce il set di istruzioni comprensibile dalla CPU
    - *CISC*: Complex Instruction Set Computing
    - *RISC*: Reduced instruction set Computing
- Assembler: traduce da **linguaggio assembly** (mnemonico) a linguaggio macchina (mapping 1~1)
- Es. *Assembly x86* → macchina (istruzioni di varia lunghezza)

``` asm
MOV AH, 11 → 1011 0 100 00001011
```

- 4 bit di op-code (`1011`), tipo di istruzione
- Bit `w` (`0`): operazione a 8 o 16 bit, (0 o 1 risp.)
- 3 bit per registro destinazione (`100`)
- 8 bit di dato per operando: `11$_{dec}$` = `00001011$_{bin}$`
