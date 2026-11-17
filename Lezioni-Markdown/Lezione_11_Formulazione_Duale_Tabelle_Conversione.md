# LEZIONE 11: FORMULAZIONE DEL PROBLEMA DUALE E TABELLE DI CONVERSIONE

> **Istruzione per NotebookLM Audio Overview**: Genera una lezione audio approfondita con UN SOLO SPEAKER (un singolo docente/tutor chiaro, fluido e diretto). NON usare due persone o dialoghi a due voci. La voce guida deve spiegare in modo lineare ogni teorema e passaggio matematico a voce, usando analogie brevi, calzanti e strettamente coerenti con l'esercizio (senza perdersi in racconti lunghi). Svolgi la teoria e affronta gli esercizi dal livello base fino ai casi limite da esame.

---

## 1. PANORAMICA DELLA LEZIONE E OBIETTIVI (5 Minuti Audio)
* **Argomento Principale**: Costruzione del Duale, Coppia Primale-Duale, Matrice Trasposta nei Vincoli, Interpretazione Economica.
* **Obiettivo Esame**: Padroneggiare i concetti teorici per l'orale e saper risolvere gli esercizi numerici per lo scritto.

---

## 2. TRATTAZIONE TEORICA ED INTUIZIONE (10 Minuti Audio)
### 1. Regole di Costruzione del Duale
Per ogni vincolo nel primale corrisponde una variabile nel duale.
Per ogni variabile nel primale corrisponde un vincolo nel duale.

---

## 3. ESERCIZI GUIDATI PROGRESSIVI (10 Minuti Audio)
### Esercizio 1 (Formulazione Immediata)
Primale: $\max 2x_1 + 4x_2$ s.t. $x_1 + 3x_2 \le 7$, $2x_1 + x_2 = 5$, $x_1 \ge 0, x_2 	ext{ libera}$.
- **Duale**:
  $$\min 7y_1 + 5y_2$$
  $$	ext{s.t. } y_1 + 2y_2 \ge 2$$
  $$3y_1 + y_2 = 4$$
  $$y_1 \ge 0, y_2 	ext{ libera}$$

---

## 4. DOMANDE FREQUENTI E TRABOCCHETTI ALL'ORALE (5 Minuti Audio)
* **Domanda del Professore**: "Qual è l'errore più comune che uno studente fa su questo argomento all'esame?"
* **Risposta d'Esame**: "Glossare sui presupposti di ammissibilità (es. scordare i vincoli di non-negatività o scambiare un vincolo di uguaglianza per disuguaglianza) o fare errori di calcolo matriciale nei cambi di base."
