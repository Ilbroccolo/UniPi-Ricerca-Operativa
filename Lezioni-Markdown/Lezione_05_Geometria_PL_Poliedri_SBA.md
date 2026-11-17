# LEZIONE 05: GEOMETRIA DELLA PROGRAMMAZIONE LINEARE E SOLUZIONI BASE AMMISSIBILI

> **Istruzione per NotebookLM Audio Overview**: Genera una lezione audio approfondita con UN SOLO SPEAKER (un singolo docente/tutor chiaro, fluido e diretto). NON usare due persone o dialoghi a due voci. La voce guida deve spiegare in modo lineare ogni teorema e passaggio matematico a voce, usando analogie brevi, calzanti e strettamente coerenti con l'esercizio (senza perdersi in racconti lunghi). Svolgi la teoria e affronta gli esercizi dal livello base fino ai casi limite da esame.

---

## 1. PANORAMICA DELLA LEZIONE E OBIETTIVI (5 Minuti Audio)
* **Argomento Principale**: Geometria dei Poliedri, Vertici, Direzioni Estreme, Forma Standard, Basi e Soluzioni Base Ammissibili (SBA).
* **Obiettivo Esame**: Padroneggiare i concetti teorici per l'orale e saper risolvere gli esercizi numerici per lo scritto.

---

## 2. TRATTAZIONE TEORICA ED INTUIZIONE (10 Minuti Audio)
### 1. Forma Standard della PL
Un problema di PL è in forma standard se:
$$\max Z = c^T x \quad 	ext{s.t. } \mathbf{A}x = b, \, x \ge 0, \, b \ge 0$$
Variabili di scarto ($s_i \ge 0$) aggiunte ai vincoli $\le$, variabili di surplus ($e_i \ge 0$) sottratte ai vincoli $\ge$.

### 2. Poliedri e Vertici
Un poliedro $P = \{x \in \mathbb{R}^n : \mathbf{A}x = b, x \ge 0\}$ è un insieme chiuso e convesso.
Un punto $x \in P$ è un **Vertice** se non può essere espresso come combinazione convessa stretta di due altri punti distinti di $P$.

### 3. Soluzioni Base Ammissibili (SBA)
Sia $\mathbf{A}$ una matrice $m 	imes n$ con $	ext{rank}(\mathbf{A}) = m$.
Scegliamo $m$ colonne linearmente indipendenti formanti una sottomatrice $\mathbf{B}$ ($m 	imes m$) detta **Base**.
- Variabili in base: $x_B = \mathbf{B}^{-1} b$.
- Variabili fuori base: $x_N = 0$.
- Se $x_B \ge 0$, la soluzione è una **Soluzione Base Ammissibile (SBA)** e corrisponde geometricamente a un vertice del poliedro.

---

## 3. ESERCIZI GUIDATI PROGRESSIVI (10 Minuti Audio)
### Esercizio 1 (Conversione Forma Standard)
Convertire in forma standard: $\min Z = 2x_1 - 3x_2$ s.t. $x_1 + x_2 \le 4$, $x_1 - 2x_2 \ge -2$, $x_1 \ge 0, x_2 	ext{ libera}$.
- **Passi**:
  1. Moltiplica il 2° vincolo per $-1$: $-x_1 + 2x_2 \le 2$.
  2. Sostituisci $x_2 = x_2^+ - x_2^-$ con $x_2^+, x_2^- \ge 0$.
  3. Trasforma $\min Z$ in $\max -Z = -2x_1 + 3x_2^+ - 3x_2^-$.
  4. Aggiungi scarti $s_1, s_2 \ge 0$.

### Esercizio 2 (Calcolo delle Basi)
Sistema: $x_1 + x_2 + s_1 = 3$, $2x_1 + x_2 + s_2 = 4$.
Estrarre la base $\mathbf{B} = (x_1, x_2)^T$.
- $\mathbf{B} = egin{pmatrix} 1 & 1 \ 2 & 1 \end{pmatrix}$, $\det(\mathbf{B}) = 1 - 2 = -1 
e 0$.
- $\mathbf{B}^{-1} = egin{pmatrix} -1 & 1 \ 2 & -1 \end{pmatrix}$.
- $x_B = \mathbf{B}^{-1} egin{pmatrix} 3 \ 4 \end{pmatrix} = egin{pmatrix} 1 \ 2 \end{pmatrix} \ge 0 \implies$ SBA ammissibile!

### Esercizio 3 (Domanda Orale)
Quante SBA al massimo può avere un poliedro con $n$ variabili e $m$ vincoli?
- **Risposta**: Al massimo $inom{n}{m} = rac{n!}{m!(n-m)!}$.

---

## 4. DOMANDE FREQUENTI E TRABOCCHETTI ALL'ORALE (5 Minuti Audio)
* **Domanda del Professore**: "Qual è l'errore più comune che uno studente fa su questo argomento all'esame?"
* **Risposta d'Esame**: "Glossare sui presupposti di ammissibilità (es. scordare i vincoli di non-negatività o scambiare un vincolo di uguaglianza per disuguaglianza) o fare errori di calcolo matriciale nei cambi di base."
