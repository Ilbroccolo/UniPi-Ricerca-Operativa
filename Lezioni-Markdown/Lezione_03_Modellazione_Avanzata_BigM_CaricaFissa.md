# LEZIONE 03: MODELLAZIONE AVANZATA - SOGLIA MINIMA, CARICA FISSA E BIG-M

> **Istruzione per NotebookLM Audio Overview**: Genera una lezione audio approfondita con UN SOLO SPEAKER (un singolo docente/tutor chiaro, fluido e diretto). NON usare due persone o dialoghi a due voci. La voce guida deve spiegare in modo lineare ogni teorema e passaggio matematico a voce, usando analogie brevi, calzanti e strettamente coerenti con l'esercizio (senza perdersi in racconti lunghi). Svolgi la teoria e affronta gli esercizi dal livello base fino ai casi limite da esame.

---

## 1. PANORAMICA DELLA LEZIONE E OBIETTIVI (5 Minuti Audio)
* **Argomento Principale**: Variabili Binarie d'Attivazione, Modellazione di Costi Fissi (Fixed Charge), Soglie Minime di Produzione e Calcolo Ottimale del valore Big-M.
* **Obiettivo Esame**: Padroneggiare i concetti teorici per l'orale e saper risolvere gli esercizi numerici per lo scritto.

---

## 2. TRATTAZIONE TEORICA ED INTUIZIONE (10 Minuti Audio)
### 1. Variabili di Attivazione e Stato Binario
In molte applicazioni industriali, produrre una quantità positiva $x_j > 0$ richiede l'accensione di un impianto o il pagamento di un costo fisso. Si associa ad $x_j$ una variabile binaria d'attivazione $y_j \in \{0, 1\}$.

### 2. Formitatura del Vincolo Big-M
$$x_j \le M_j y_j$$
- Se $y_j = 0 \implies x_j \le 0 \implies x_j = 0$ (Produzione spenta).
- Se $y_j = 1 \implies x_j \le M_j$ (Produzione attiva fino a $M_j$).

### 3. Scelta del Valore di Big-M
**Regola d'Oro d'Esame**: Nelle prove scritte e orali NON usare mai $M = 1.000.000$ arbitrario! Trova la capacità massima teorica $M_j$ imponendo il vincolo più stringente sul problema.

---

## 3. ESERCIZI GUIDATI PROGRESSIVI (10 Minuti Audio)
### Esercizio 1 (Livello Facile - Carica Fissa)
Attivare una linea costa 50€. Ogni pezzo costa 2€ e si vende a 10€ (profitto netto 8€).
- **Formulazione**:
  $$\max Z = 8x - 50y$$
  $$	ext{s.t. } x \le M y, \quad y \in \{0, 1\}, x \ge 0$$

### Esercizio 2 (Livello Intermedio - Soglia Minima + Massima)
Se si produce la sostanza chimica $x_1$, bisogna produrne tra 100 kg (minimo tecnico) e 500 kg (capacità serbatoio).
- **Formulazione**:
  $$100 y_1 \le x_1 \le 500 y_1$$
  $$y_1 \in \{0, 1\}, \quad x_1 \ge 0$$

### Esercizio 3 (Livello Avanzato - Calcolo di M da Vincoli Esistenti)
Dati i vincoli: $2x_1 + 5x_2 \le 100$ e $x_1 \le M y_1$. Calcolare il valore minimo valido di $M$.
- **Calcolo**: Poiché $x_1 \ge 0$ e $x_2 \ge 0$, il massimo valore possibile per $x_1$ si ha quando $x_2 = 0 \implies 2x_1 \le 100 \implies x_1 \le 50$.
- **Risposta d'Esame**: $M = 50$ è il valore minimo e corretto.

---

## 4. DOMANDE FREQUENTI E TRABOCCHETTI ALL'ORALE (5 Minuti Audio)
* **Domanda del Professore**: "Qual è l'errore più comune che uno studente fa su questo argomento all'esame?"
* **Risposta d'Esame**: "Glossare sui presupposti di ammissibilità (es. scordare i vincoli di non-negatività o scambiare un vincolo di uguaglianza per disuguaglianza) o fare errori di calcolo matriciale nei cambi di base."
