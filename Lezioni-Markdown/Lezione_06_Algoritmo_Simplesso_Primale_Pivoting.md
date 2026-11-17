# LEZIONE 06: ALGORITMO DEL SIMPLESSO PRIMALE E TABELLA MATRICIALE

> **Istruzione per NotebookLM Audio Overview**: Genera una lezione audio approfondita con UN SOLO SPEAKER (un singolo docente/tutor chiaro, fluido e diretto). NON usare due persone o dialoghi a due voci. La voce guida deve spiegare in modo lineare ogni teorema e passaggio matematico a voce, usando analogie brevi, calzanti e strettamente coerenti con l'esercizio (senza perdersi in racconti lunghi). Svolgi la teoria e affronta gli esercizi dal livello base fino ai casi limite da esame.

---

## 1. PANORAMICA DELLA LEZIONE E OBIETTIVI (5 Minuti Audio)
* **Argomento Principale**: Algoritmo del Simplesso Primale, Costi Ridotti, Scelta della Variabile Entrante/Uscente, Pivoting Matriciale.
* **Obiettivo Esame**: Padroneggiare i concetti teorici per l'orale e saper risolvere gli esercizi numerici per lo scritto.

---

## 2. TRATTAZIONE TEORICA ED INTUIZIONE (10 Minuti Audio)
### 1. Concetto Chiave del Simplesso
L'algoritmo del Simplesso esplora i vertici (SBA) del poliedro muovendosi da una SBA a una SBA adiacente con valore di funzione obiettivo non inferiore, fino a raggiungere l'ottimo.

### 2. Struttura della Tabella del Simplesso
| Base | $x_B$ | $x_N$ | R.H.S. ($b$) |
| :--- | :--- | :--- | :--- |
| **$-Z$** | $0$ | $ar{c}_N^T = c_N^T - c_B^T \mathbf{B}^{-1}\mathbf{N}$ | $-c_B^T \mathbf{B}^{-1}b$ |
| **$x_B$** | $\mathbf{I}$ | $\mathbf{ar{A}}_N = \mathbf{B}^{-1}\mathbf{N}$ | $\mathbf{ar{b}} = \mathbf{B}^{-1}b$ |

### 3. Criteri di Passo
- **Ottimalità**: Se tutti i costi ridotti $ar{c}_j \le 0$ (in Max), la soluzione corrente è OTTIMA.
- **Entrata in Base**: Scegli $x_h$ con $ar{c}_h > 0$.
- **Uscita dalla Base (Test del Rapporto Minimo)**:
  $$\lambda = \min_{i : ar{a}_{ih} > 0} \left\{ rac{ar{b}_i}{ar{a}_{ih}} 
ight\}$$

---

## 3. ESERCIZI GUIDATI PROGRESSIVI (10 Minuti Audio)
### Esercizio 1 (Pivoting Matriciale Svolto)
Dato il problema: $\max Z = 4x_1 + 3x_2$
$x_1 + 2x_2 + s_1 = 6$
$2x_1 + x_2 + s_2 = 8$
- **Passo 1**: Base iniziale $(s_1, s_2)^T = (6, 8)^T$. $Z=0$. Costi ridotti: $ar{c}_1 = 4, ar{c}_2 = 3$.
- **Passo 2**: Entra $x_1$ (costo ridotto 4).
  - Rapporto riga 1: $6/1 = 6$.
  - Rapporto riga 2: $8/2 = 4 \implies$ Esci $s_2$.
- **Passo 3 (Pivoting)**: Perno su elemento $(2,1) = 2$.
  - Nuova riga 2: $x_1 + 0.5 x_2 + 0.5 s_2 = 4$.
  - Nuova riga 1: $s_1 + 1.5 x_2 - 0.5 s_2 = 2$.
  - Nuova $Z = 16$.
- **Passo 4**: Nuovi costi ridotti: $ar{c}_2 = 1, ar{c}_{s2} = -2$.
  - Entra $x_2$. Esci $s_1$ (rapporto $2/1.5 = 4/3$).
- **Ottimo**: $x_1 = 10/3, x_2 = 4/3, Z^* = 54/3 = 18$.

---

## 4. DOMANDE FREQUENTI E TRABOCCHETTI ALL'ORALE (5 Minuti Audio)
* **Domanda del Professore**: "Qual è l'errore più comune che uno studente fa su questo argomento all'esame?"
* **Risposta d'Esame**: "Glossare sui presupposti di ammissibilità (es. scordare i vincoli di non-negatività o scambiare un vincolo di uguaglianza per disuguaglianza) o fare errori di calcolo matriciale nei cambi di base."
