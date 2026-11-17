# LEZIONE 04: VINCOLI LOGICI, FUNZIONI A TRATTI E VALORE ASSOLUTO

> **Istruzione per NotebookLM Audio Overview**: Genera una lezione audio approfondita con UN SOLO SPEAKER (un singolo docente/tutor chiaro, fluido e diretto). NON usare due persone o dialoghi a due voci. La voce guida deve spiegare in modo lineare ogni teorema e passaggio matematico a voce, usando analogie brevi, calzanti e strettamente coerenti con l'esercizio (senza perdersi in racconti lunghi). Svolgi la teoria e affronta gli esercizi dal livello base fino ai casi limite da esame.

---

## 1. PANORAMICA DELLA LEZIONE E OBIETTIVI (5 Minuti Audio)
* **Argomento Principale**: Disuguaglianze Alternativamente Attive (OR logico), Linearizzazione del Valore Assoluto, Funzioni Concave/Convesse a Tratti.
* **Obiettivo Esame**: Padroneggiare i concetti teorici per l'orale e saper risolvere gli esercizi numerici per lo scritto.

---

## 2. TRATTAZIONE TEORICA ED INTUIZIONE (10 Minuti Audio)
### 1. Vincoli Disgiuntivi (Logica OR)
Per imporre che il sistema soddisfi il Vincolo A ($g_1(x) \le 0$) OPPURE il Vincolo B ($g_2(x) \le 0$), si usa una variabile binaria $y \in \{0, 1\}$:
$$g_1(x) \le M y$$
$$g_2(x) \le M (1 - y)$$

### 2. Linearizzazione del Valore Assoluto
Minimizzare $Z = |x_1 - a|$:
Si sostituisce $|x_1 - a|$ con $t \ge 0$ introducendo due vincoli lineari:
$$t \ge x_1 - a \quad 	ext{e} \quad t \ge -(x_1 - a)$$

### 3. Funzioni Costo a Tratti
Costo dell'energia elettrica a scaglioni (primi 100 kWh a 0.10€/kWh, i successivi a 0.20€/kWh).

---

## 3. ESERCIZI GUIDATI PROGRESSIVI (10 Minuti Audio)
### Esercizio 1 (Valore Assoluto)
Minimizzare la deviazione da un target: $\min Z = |x_1 + x_2 - 10|$.
- **Formulazione**:
  $$\min Z = t$$
  $$	ext{s.t. } t \ge x_1 + x_2 - 10$$
  $$t \ge 10 - x_1 - x_2$$
  $$t \ge 0$$

### Esercizio 2 (Ordinamento Lavori / Disgiuntivo)
Due macchine $J_1$ e $J_2$ hanno tempi di lavorazione $p_1 = 4$ e $p_2 = 5$.
Siano $t_1, t_2$ i tempi di inizio. Modellare l'impossibilità di sovrapposizione.
- **Formulazione**:
  $$t_1 + 4 \le t_2 + M(1 - y)$$
  $$t_2 + 5 \le t_1 + My$$
  $$y \in \{0, 1\}, \quad t_1, t_2 \ge 0$$

### Esercizio 3 (Scaglioni di Costo)
Un fornitore vende farina a 2€/kg per i primi 50 kg, e 1.5€/kg per i kg eccedenti i 50.
- **Formulazione**:
  Sia $x = x_1 + x_2$ con $0 \le x_1 \le 50$ e $0 \le x_2 \le M y_1$ dove $x_1 \ge 50 y_1$.
  $$	ext{Costo Total} = 2 x_1 + 1.5 x_2$$

---

## 4. DOMANDE FREQUENTI E TRABOCCHETTI ALL'ORALE (5 Minuti Audio)
* **Domanda del Professore**: "Qual è l'errore più comune che uno studente fa su questo argomento all'esame?"
* **Risposta d'Esame**: "Glossare sui presupposti di ammissibilità (es. scordare i vincoli di non-negatività o scambiare un vincolo di uguaglianza per disuguaglianza) o fare errori di calcolo matriciale nei cambi di base."
