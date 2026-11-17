# LEZIONE 02: PROBLEMI DI ASSEGNAMENTO, DIETA E PIANIFICAZIONE TEMPORALE

> **Istruzione per NotebookLM Audio Overview**: Genera una lezione audio approfondita con UN SOLO SPEAKER (un singolo docente/tutor chiaro, fluido e diretto). NON usare due persone o dialoghi a due voci. La voce guida deve spiegare in modo lineare ogni teorema e passaggio matematico a voce, usando analogie brevi, calzanti e strettamente coerenti con l'esercizio (senza perdersi in racconti lunghi). Svolgi la teoria e affronta gli esercizi dal livello base fino ai casi limite da esame.

---

## 1. PANORAMICA DELLA LEZIONE E OBIETTIVI (5 Minuti Audio)
* **Argomento Principale**: Modelli di Dieta Minimale, Assegnamento Compiti-Macchine, Pianificazione del Personale e Copertura dei Turni.
* **Obiettivo Esame**: Padroneggiare i concetti teorici per l'orale e saper risolvere gli esercizi numerici per lo scritto.

---

## 2. TRATTAZIONE TEORICA ED INTUIZIONE (10 Minuti Audio)
### 1. Il Problema della Dieta Stocastica/Deterministica
Il problema della dieta (formulato da George Stigler nel 1945) cerca la combinazione a minimo costo di cibi che garantisca i nutrienti essenziali (proteine, vitamine, calorie). È il prototipo dei problemi con vincoli di tipo $\ge$.

### 2. Problemi di Assegnamento (Assignment Problem)
Assegnare $n$ lavoratori a $n$ mansioni in modo biunivoco minimizzando il costo totale o massimizzando l'efficienza.
Variabile di decisione binaria: $x_{ij} = 1$ se il lavoratore $i$ fa la mansione $j$, $0$ altrimenti.
- Ogni lavoratore fa esattamente 1 mansione: $\sum_j x_{ij} = 1 \quad orall i$.
- Ogni mansione è fatta da esattamente 1 lavoratore: $\sum_i x_{ij} = 1 \quad orall j$.

### 3. Pianificazione del Personale (Staff Scheduling)
Pianificare i turni di lavoro coprendo il fabbisogno minimo di personale per ogni ora/giorno della settimana con turni di durata fissa (es. turni di 8 ore consecutive).

---

## 3. ESERCIZI GUIDATI PROGRESSIVI (10 Minuti Audio)
### Esercizio 1 (Livello Base - Dieta)
Cibo 1 (Mela): costa 1€, fornisce 100 cal e 2g di fibra.
Cibo 2 (Pane): costa 2€, fornisce 300 cal e 1g di fibra.
Servono almeno 600 cal e 4g di fibra.
- **Formulazione**:
  $$\min Z = x_1 + 2x_2$$
  $$	ext{s.t. } 100x_1 + 300x_2 \ge 600$$
  $$2x_1 + x_2 \ge 4$$
  $$x_1, x_2 \ge 0$$

### Esercizio 2 (Livello Intermedio - Turni di Lavoro)
Un call center necessita di coprire 3 periodi del giorno:
- Mattino (8-12): servono 5 operatori.
- Pomeriggio (12-16): servono 8 operatori.
- Sera (16-20): servono 4 operatori.
Gli operatori fanno turni di 8 ore consecutive (Mattino+Pomeriggio $x_1$, oppure Pomeriggio+Sera $x_2$).
- **Formulazione**:
  $$\min Z = x_1 + x_2$$
  $$	ext{s.t. } x_1 \ge 5 \quad (	ext{Copertura Mattino})$$
  $$x_1 + x_2 \ge 8 \quad (	ext{Copertura Pomeriggio})$$
  $$x_2 \ge 4 \quad (	ext{Copertura Sera})$$
  $$x_1, x_2 \ge 0, 	ext{ intere}$$

### Esercizio 3 (Livello Avanzato - Assegnamento con incompatibilità)
4 lavoratori e 4 macchine. Il lavoratore 2 non può lavorare sulla macchina 3.
- **Come modellarlo all'esame**: Impostare direttamente $x_{23} = 0$ oppure inserire un costo $c_{23} = M = +\infty$ nella funzione obiettivo.

---

## 4. DOMANDE FREQUENTI E TRABOCCHETTI ALL'ORALE (5 Minuti Audio)
* **Domanda del Professore**: "Qual è l'errore più comune che uno studente fa su questo argomento all'esame?"
* **Risposta d'Esame**: "Glossare sui presupposti di ammissibilità (es. scordare i vincoli di non-negatività o scambiare un vincolo di uguaglianza per disuguaglianza) o fare errori di calcolo matriciale nei cambi di base."
