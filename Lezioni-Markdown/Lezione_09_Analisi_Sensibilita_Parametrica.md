# LEZIONE 09: ANALISI DI SENSIBILITÀ E PROGRAMMAZIONE PARAMETRICA

> **Istruzione per NotebookLM Audio Overview**: Genera una lezione audio approfondita con UN SOLO SPEAKER (un singolo docente/tutor chiaro, fluido e diretto). NON usare due persone o dialoghi a due voci. La voce guida deve spiegare in modo lineare ogni teorema e passaggio matematico a voce, usando analogie brevi, calzanti e strettamente coerenti con l'esercizio (senza perdersi in racconti lunghi). Svolgi la teoria e affronta gli esercizi dal livello base fino ai casi limite da esame.

---

## 1. PANORAMICA DELLA LEZIONE E OBIETTIVI (5 Minuti Audio)
* **Argomento Principale**: Variazione dei Costi $c$, Variazione dei Termini Noti $b$, Intervalli di Stabilità della Base.
* **Obiettivo Esame**: Padroneggiare i concetti teorici per l'orale e saper risolvere gli esercizi numerici per lo scritto.

---

## 2. TRATTAZIONE TEORICA ED INTUIZIONE (10 Minuti Audio)
### 1. Cos'è l'Analisi di Sensibilità?
Valuta come varia la soluzione ottima $x^*$ e il valore $Z^*$ al variare dei parametri di ingresso senza dover ripartire da capo con il simplesso.

### 2. Variazione del Termine Noto $b 	o b + \Delta b$
La base $\mathbf{B}$ rimane ammissibile finché:
$$ar{b}' = \mathbf{B}^{-1}(b + \Delta b) \ge 0$$

### 3. Variazione dei Coefficienti di Costo $c 	o c + \Delta c$
La base $\mathbf{B}$ rimane ottima finché i nuovi costi ridotti rimangono non-positivi:
$$ar{c}_N' = c_N'^T - c_B'^T \mathbf{B}^{-1}\mathbf{N} \le 0$$

---

## 3. ESERCIZI GUIDATI PROGRESSIVI (10 Minuti Audio)
### Esercizio 1 (Intervallo di Stabilità di $b$)
Sia $\mathbf{B}^{-1} = egin{pmatrix} 1 & -0.5 \ 0 & 0.5 \end{pmatrix}$ e $ar{b} = egin{pmatrix} 2 \ 3 \end{pmatrix}$.
Di quanto può variare $b_1$ ($\Delta b_1$) mantenendo la stessa base?
- $ar{b}' = egin{pmatrix} 2 \ 3 \end{pmatrix} + \Delta b_1 egin{pmatrix} 1 \ 0 \end{pmatrix} = egin{pmatrix} 2 + \Delta b_1 \ 3 \end{pmatrix} \ge 0 \implies \Delta b_1 \ge -2$.

---

## 4. DOMANDE FREQUENTI E TRABOCCHETTI ALL'ORALE (5 Minuti Audio)
* **Domanda del Professore**: "Qual è l'errore più comune che uno studente fa su questo argomento all'esame?"
* **Risposta d'Esame**: "Glossare sui presupposti di ammissibilità (es. scordare i vincoli di non-negatività o scambiare un vincolo di uguaglianza per disuguaglianza) o fare errori di calcolo matriciale nei cambi di base."
