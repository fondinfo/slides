![](http://fondinfo.github.io/images/algo/bulb.svg)
# Problem solving
## Introduzione alla programmazione

---

# Problemi e algoritmi

---

![](http://fondinfo.github.io/images/hist/polya.jpg)
# 💡️ Problem solving

- George Polya, [“How to solve it”](https://www.dropbox.com/s/86ua0v7mbr6tkgm/Polya_How-to-solve-it.pdf?dl=1), 1945
- Soluzione di problemi (matematici): processo raramente lineare

> Esempio. Trovare la diagonale di un parallelepipedo rettangolo, di cui sono note lunghezza, larghezza e altezza. *(Polya, pag. 23)*

---

![](http://fondinfo.github.io/images/dev/problem-solving.svg) ![](http://fondinfo.github.io/images/algo/space-diagonal.svg)
# 💡 Analisi del problema

- **➊ See.** Capire il problema
    - Quali dati, incognite, condizioni?
    - Figure, notazione… *modello*

> Bisognerebbe rendere tutto il più semplice possibile, ma non troppo semplice. *(A. Einstein)*

> Per ogni problema complesso c'è sempre una soluzione chiara, semplice… e sbagliata! *(H.L. Mencken)*

Ad esempio, per il calcolo della diagonale di un parallelepipedo, <br> una buona figura può dare suggerimenti importanti

---

![](http://fondinfo.github.io/images/dev/problem-solving.svg)
# 💡 Dal problema alla soluzione

- **➋ Plan.** Elaborare un progetto
    - Mettere in relazione dati e incognite
    - Riduzione, analogia, divide et impera, composizione, astrazione… *Pensiero computazionale*
    - Cominciare a risolvere un problema *più semplice*
- **➌ Do.** Implementare il progetto
    - Realizzare il sistema da sperimentare

> Se non riesci a risolvere un problema, ce ne sarà uno più facile che puoi risolvere: trovalo. *(G. Polya)*

> [La risposta è dentro di te… (Quelo)](https://www.youtube.com/watch?v=WGQ7JZRZ65M)

---

![](http://fondinfo.github.io/images/dev/problem-solving.svg) ![](http://fondinfo.github.io/images/hist/david-michelangelo.jpg) David di Michelangelo
# 💡 … E ritorno

- **➍ Check.** Controllare la soluzione
    - Corretta? Ottenibile in altro modo?
    - Metodo utile per altri problemi?

> Vi scrivo una lunga lettera perché non ho tempo di scriverne una breve. *(Voltaire)*

> La perfezione si raggiunge non quando non c'è più niente da aggiungere, ma quando non c'è più niente da togliere. *(De Saint-Exupéry)*

> La scultura è quella che si fa per forza di levare. *(Michelangelo)*

Una soluzione più breve e chiara si ottiene dopo più iterazioni

---

# ⚠️ Un avvertimento sull'IA

- L'IA generativa **non può sostituire** l'allenamento al *problem solving* e al *pensiero computazionale*
    - Quelle abilità si sviluppano solo risolvendo i problemi da soli
- ✅ Va bene farsi *spiegare* un concetto, chiedere *esempi* ed *esercizi* mirati
- ⛔ Non va bene usarla come “spalla” nella **soluzione** degli esercizi
- Rischio: delegare proprio il ragionamento che dovreste allenare
    - Risolvere un problema con la guida di un compagno o della IA <br> non allena a *generare le idee* per risolverlo
- Gli studi recenti confermano il rischio
    - Chi usa l'IA migliora i voti dei compiti a casa…
    - Ma **peggiora ai test in aula** (-20%)

>

👉 [Strömberg et al., "The generative AI learning penalty in secondary school", VoxEU/CEPR](https://cepr.org/voxeu/columns/generative-ai-learning-penalty-secondary-school)
<br>
👉 [OECD, PISA 2025 — risultati su IA e apprendimento](https://www.thestar.com.my/tech/tech-news/2026/09/09/school-students-who-use-ai-get-worse-test-scores-oecd-warns)

---

![large](http://fondinfo.github.io/images/algo/origami.svg) Gli origami sono algoritmi
# 💡️ Elementi di un algoritmo

- 🤖️ *Algoritmo*: procedimento che risolve un determinato problema attraverso un numero finito di passi elementari (al-Khwarizmi, ~800)
- **Dati**: iniziali (istanza problema), intermedi, finali (soluzione)
- **Passi** elementari: azioni atomiche non scomponibili in azioni più semplici
- **Processo**, o anche esecuzione: sequenza ordinata di passi
- *Proprietà*: finitezza, non ambiguità, realizzabilità, efficienza…

>

<https://en.wikipedia.org/wiki/Muhammad_ibn_Musa_al-Khwarizmi>

---

![](http://fondinfo.github.io/images/algo/spaghetti-flowchart.svg)
# 💡️ Diagramma di flusso

- **Flow-chart**: *grafo orientato*, nodi + archi
    - Passi di un algoritmo + loro sequenza
- Rappresentazione *grafica* anzichè verbale
    - Più efficace, meno ambigua
- Tre tipi di nodi
    - I/O: lettura e scrittura dati
    - Operazioni aritmetico-logiche
    - Controllo del flusso di esecuzione

![small](http://fondinfo.github.io/images/algo/nodes.svg)

---

![](http://fondinfo.github.io/images/algo/recipe.png)
# ⭐️ Programmazione strutturata

![](http://fondinfo.github.io/images/algo/structures.svg)

> Si può implementare qualunque algoritmo con queste sole strutture *(Böhm-Jacopini, 1966)*

> Goto considered harmful *(Dijkstra, 1968)*

- ❗ Strutture con: 1 ingresso, 1 uscita
- 🧑‍🍳 Ricette: algoritmi quotidiani, con `if` e `while`
    - “Se non c'è il lievito, usare due cucchiaini di bicarbonato”
    - “Battere gli albumi finché non montano”


---

# 🧪 Programmazione a blocchi

![](http://fondinfo.github.io/images/algo/blockly.png)

>

<https://blockly.games/maze?lang=it> — Problemi 3, 4, 6, 7, 9
