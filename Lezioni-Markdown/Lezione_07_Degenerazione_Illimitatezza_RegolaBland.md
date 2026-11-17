# LEZIONE 07: DEGENERAZIONE, ILLIMITATEZZA E REGOLA ANTI-CICLO DI BLAND

> **Istruzione per NotebookLM Audio Overview**: Genera una lezione audio approfondita con UN SOLO SPEAKER (un singolo docente/tutor chiaro, fluido e diretto). NON usare due persone o dialoghi a due voci. La voce guida deve spiegare in modo lineare ogni teorema e passaggio matematico a voce, usando analogie brevi, calzanti e strettamente coerenti con l'esercizio (senza perdersi in racconti lunghi). Svolgi la teoria e affronta gli esercizi dal livello base fino ai casi limite da esame.

---

## 1. PANORAMICA DELLA LEZIONE E OBIETTIVI (5 Minuti Audio)
* **Argomento Principale**: Basi Degeneri, Ciclaggio del Simplesso, Regola di Bland, Riconoscimento di Problemi Illimitati.
* **Obiettivo Esame**: Padroneggiare i concetti teorici per l'orale e saper risolvere gli esercizi numerici per lo scritto.

---

## 2. TRATTAZIONE TEORICA ED INTUIZIONE (10 Minuti Audio)
### 1. Degenerazione Algebrica e Geometrica
Una SBA è **Degenere** se almeno una delle sue variabili in base ha valore nullo ($x_{B_i} = 0$).
Geometricamente significa che nel vertice corrente concorrono più di $n$ iperpiani vincolanti.

### 2. Il Fenomeno del Ciclaggio
Se una base è degenere, durante il test del rapporto minimo si può avere $\lambda = 0$.
La variabile entra in base, un'altra esce, la matrice $\mathbf{B}$ cambia, ma la soluzione spaziale $x$ e il valore $Z$ RIMANGONO IDENTICI. Il simplesso può entrare in un ciclo infinito di basi senza progredire.

### 3. Regola Anti-Ciclo di Bland
Per evitare il ciclaggio, in caso di parità nella scelta delle variabili:
1. **Variabile Entrante**: Scegli la variabile con il MINIMO indice $j$ tra quelle con $ar{c}_j > 0$.
2. **Variabile Uscente**: Scegli la variabile con il MINIMO indice $i$ tra quelle che raggiungono il rapporto minimo.

---

## 3. ESERCIZI GUIDATI PROGRESSIVI (10 Minuti Audio)
### Esercizio 1 (Riconoscimento Illimitatezza)
Se durante il pivoting su colonna $x_h$ tutti i valori $ar{a}_{ih} \le 0$:
- **Risposta d'Esame**: La direzione $d = (-ar{a}_{\cdot h}, e_h)$ è una direzione estrema di illimitatezza. Il problema è illimitato ($Z 	o +\infty$).

### Esercizio 2 (Applicazione Regola di Bland)
Parità costi ridotti entranti: $x_2$ ($ar{c}_2 = 5$) e $x_4$ ($ar{c}_4 = 5$).
- Con regola del costo ridotto max: indifferente.
- Con **Regola di Bland**: Scegliere tassativamente $x_2$ perché $2 < 4$.

---

## 4. DOMANDE FREQUENTI E TRABOCCHETTI ALL'ORALE (5 Minuti Audio)
* **Domanda del Professore**: "Qual è l'errore più comune che uno studente fa su questo argomento all'esame?"
* **Risposta d'Esame**: "Glossare sui presupposti di ammissibilità (es. scordare i vincoli di non-negatività o scambiare un vincolo di uguaglianza per disuguaglianza) o fare errori di calcolo matriciale nei cambi di base."
