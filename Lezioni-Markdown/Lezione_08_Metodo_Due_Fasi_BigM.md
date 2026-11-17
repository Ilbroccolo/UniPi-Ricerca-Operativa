# LEZIONE 08: METODO DELLE DUE FASI E METODO DEL BIG-M PER LA BASE INIZIALE

> **Istruzione per NotebookLM Audio Overview**: Genera una lezione audio approfondita con UN SOLO SPEAKER (un singolo docente/tutor chiaro, fluido e diretto). NON usare due persone o dialoghi a due voci. La voce guida deve spiegare in modo lineare ogni teorema e passaggio matematico a voce, usando analogie brevi, calzanti e strettamente coerenti con l'esercizio (senza perdersi in racconti lunghi). Svolgi la teoria e affronta gli esercizi dal livello base fino ai casi limite da esame.

---

## 1. PANORAMICA DELLA LEZIONE E OBIETTIVI (5 Minuti Audio)
* **Argomento Principale**: Ricerca della Prima SBA, Variabili Artificiali, Algoritmo delle 2 Fasi, Penalizzazione Big-M.
* **Obiettivo Esame**: Padroneggiare i concetti teorici per l'orale e saper risolvere gli esercizi numerici per lo scritto.

---

## 2. TRATTAZIONE TEORICA ED INTUIZIONE (10 Minuti Audio)
### 1. Perché servono le Variabili Artificiali?
Se un vincolo ha forma $\ge$ o $=$, la variabile di scarto ha segno negativo o non esiste, impedendo di estrarre la matrice identità $\mathbf{I}_m$ iniziale. Si aggiungono **Variabili Artificiali** $a_i \ge 0$.

### 2. Il Metodo delle Due Fasi
- **FASE 1**: Costruisci un problema ausiliario: $\min W = \sum_{i=1}^k a_i$.
  - Se $W^* > 0 \implies$ Il problema originale è **Inammissibile**.
  - Se $W^* = 0 \implies$ Si trova una SBA ammissibile per il problema originale. Si eliminano le colonne artificiali e si passa alla Fase 2.
- **FASE 2**: Ripristina la funzione obiettivo originale e applica il simplesso standard.

---

## 3. ESERCIZI GUIDATI PROGRESSIVI (10 Minuti Audio)
### Esercizio 1 (Fase 1 Svolta)
Minimizzare $W = a_1$ s.t. $x_1 + x_2 + a_1 = 5$, $x_1 \ge 0, x_2 \ge 0, a_1 \ge 0$.
Base iniziale $a_1 = 5$. Costo ridotto $a_1$ espresso in termini di $x$: $a_1 = 5 - x_1 - x_2$.
- $\max -W = -5 + x_1 + x_2$.
- Entra $x_1$, esce $a_1$. $W^* = 0$. Soluzione ammissibile trovata!

---

## 4. DOMANDE FREQUENTI E TRABOCCHETTI ALL'ORALE (5 Minuti Audio)
* **Domanda del Professore**: "Qual è l'errore più comune che uno studente fa su questo argomento all'esame?"
* **Risposta d'Esame**: "Glossare sui presupposti di ammissibilità (es. scordare i vincoli di non-negatività o scambiare un vincolo di uguaglianza per disuguaglianza) o fare errori di calcolo matriciale nei cambi di base."
