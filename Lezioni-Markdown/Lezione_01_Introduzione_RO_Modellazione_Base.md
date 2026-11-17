# LEZIONE 01: INTRODUZIONE ALLA RICERCA OPERATIVA E MODELLAZIONE DI BASE

> **Istruzione per NotebookLM Audio Overview**: Genera una lezione audio approfondita con UN SOLO SPEAKER (un singolo docente/tutor chiaro, fluido e diretto). NON usare due persone o dialoghi a due voci. La voce guida deve spiegare in modo lineare ogni teorema e passaggio matematico a voce, usando analogie brevi, calzanti e strettamente coerenti con l'esercizio (senza perdersi in racconti lunghi). Svolgi la teoria e affronta gli esercizi dal livello base fino ai casi limite da esame.

---

## 1. PANORAMICA DELLA LEZIONE E OBIETTIVI (5 Minuti Audio)
* **Argomento Principale**: Origine della RO, Formulazione Matematica, Variabili di Decisione, Funzione Obiettivo, Vincoli Fisici, Problemi di Produzione e Miscelazione.
* **Obiettivo Esame**: Padroneggiare i concetti teorici per l'orale e saper risolvere gli esercizi numerici per lo scritto.

---

## 2. TRATTAZIONE TEORICA ED INTUIZIONE (10 Minuti Audio)
### 1. Storia e Definizione di Ricerca Operativa
La Ricerca Operativa (RO) nasce durante la Seconda Guerra Mondiale per risolvere problemi di allocazione ottimale di risorse scarse in ambito militare e logistico.
In termini matematici, un problema di RO consiste nell'ottimizzare (massimizzare o minimizzare) una funzione obiettivo $Z(x)$ sotto un insieme di vincoli fisici, tecnici ed economici espresso come $x \in S \subseteq \mathbb{R}^n$.

### 2. Struttura dei Modelli Matematici
- **Variabili di Decisione ($x_j$)**: Rappresentano le decisioni che il decisore può controllare (es. kg di lega prodotta, numero di camion spediti).
- **Funzione Obiettivo ($Z$)**: Funzione $f(x_1, \dots, x_n)$ che quantifica la qualità della decisione (profitto da massimizzare o costo da minimizzare).
- **Vincoli**: Relazioni algebriche ($\le, =, \ge$) che limitano le combinazioni ammissibili delle variabili di decisione.

### 3. Problemi Classici di Produzione e Miscelazione (Blending)
Nel problema di produzione semplice, si determina la quantità ottimale di beni da fabbricare disponendo di risorse limitate (materie prime, ore macchina, manodopera).
Nel problema di miscelazione, si combinano materie prime grezze con diverse percentuali di purezza o concentrazione per ottenere un prodotto finale con specifiche minime e massime di composizione.

---

## 3. ESERCIZI GUIDATI PROGRESSIVI (10 Minuti Audio)
### Esercizio 1 (Livello Facile - A Mente)
Un'azienda produce due bevande: Aranciata ($x_1$) e Limonata ($x_2$).
L'Aranciata frutta 3€ al litro, la Limonata 2€ al litro.
Disponiamo di 100 litri d'acqua e 40 kg di zucchero.
Per 1 litro di Aranciata servono 1L acqua e 1kg zucchero.
Per 1 litro di Limonata servono 1L acqua e 0.5kg zucchero.
- **Formulazione**:
  $$\max Z = 3x_1 + 2x_2$$
  $$	ext{s.t. } x_1 + x_2 \le 100 \quad (	ext{Acqua})$$
  $$x_1 + 0.5x_2 \le 40 \quad (	ext{Zucchero})$$
  $$x_1, x_2 \ge 0$$

### Esercizio 2 (Livello Intermedio - Miscelazione)
Dobbiamo produrre una lega di alluminio di 100 kg con almeno il 30% di alluminio puro usando due rottami:
- Rottame A: contiene l'80% di alluminio e costa 5€/kg.
- Rottame B: contiene il 10% di alluminio e costa 2€/kg.
- **Formulazione**:
  Siano $x_A, x_B$ i kg di rottame A e B.
  $$\min Z = 5x_A + 2x_B$$
  $$	ext{s.t. } x_A + x_B = 100 \quad (	ext{Peso totale})$$
  $$0.80 x_A + 0.10 x_B \ge 0.30(100) = 30 \quad (	ext{Alluminio puro})$$
  $$x_A, x_B \ge 0$$

### Esercizio 3 (Livello Esame - Tranello Linearizzazione)
Nel problema di miscelazione, uno studente scrive il vincolo come: $rac{0.80 x_A + 0.10 x_B}{x_A + x_B} \ge 0.30$.
- **Perché è un errore grave all'esame**: Il rapporto tra variabili rende la funzione non-lineare! I solutori di Programmazione Lineare falliscono.
- **Correzione obbligatoria**: Moltiplicare per il denominatore positivo $(x_A + x_B)$ ottenendo vincoli lineari: $0.50 x_A - 0.20 x_B \ge 0$.

---

## 4. DOMANDE FREQUENTI E TRABOCCHETTI ALL'ORALE (5 Minuti Audio)
* **Domanda del Professore**: "Qual è l'errore più comune che uno studente fa su questo argomento all'esame?"
* **Risposta d'Esame**: "Glossare sui presupposti di ammissibilità (es. scordare i vincoli di non-negatività o scambiare un vincolo di uguaglianza per disuguaglianza) o fare errori di calcolo matriciale nei cambi di base."
