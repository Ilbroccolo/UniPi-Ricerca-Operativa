# LA BIBBIA DI RICERCA OPERATIVA
## Trascrizione Pura Integrale Parlata al 100% (Lezioni 01--05)
**Autore:** Joseph Zucchelli  
**Docente Titolare:** Prof. Luca Mencarelli  
**Università di Pisa** — *Corso di Laurea in Informatica / Fisica (A.A. 2026/2027)*

---

> ### Guida alla Lettura Visiva per Fisici ed Informatici
> Questo volume raccoglie la **trascrizione pura integrale senza alcuna forma di sintesi o taglio** di tutte le prime 5 lezioni del Prof. Luca Mencarelli. Ogni singola spiegazione, aneddoto, monologo parlato, botta e risposta con gli studenti e passaggio algebrico alla lavagna è mantenuto al 100% ed integrato con lo stile grafico **"La Bibbia"**, corredato da icone geometriche e card di annotazione delle formule.

### Libreria Iconografica Base (Aziende, Persone, Oggetti)

| Icona Azienda / Impianto | Icona Cliente / Operatore | Icona Prodotto / Risorsa |
| :---: | :---: | :---: |
| 🏢 **Azienda / Stabilimento** | 👤 **Cliente / Operatore** | 📦 **Prodotto / Risorsa** |

---

### Anatomia Visiva delle Formule di RO (Annotazione dei Pedici e dei Vincoli)

#### Indicizzazione delle Variabili Decisionali
$$x_{ij} \quad \text{dove } i = \text{indice di riga (origine)}, \, j = \text{indice di colonna (destinazione)}$$

#### Vincolo di Conservazione dell'Offerta
$$\sum_{j=1}^{n} x_{ij} = a_i \quad \text{(Quantità totale spedita dall'origine $i$ = Offerta disponibile in $i$)}$$

#### Funzione Obiettivo di Costo Totale
$$\min Z = \sum_{i=1}^{m} \sum_{j=1}^{n} c_{ij} x_{ij} \quad \text{(Costo totale = somma su tutte le coppie origine-destinazione)}$$

---

## 1. Lezione 01: Modellazione di Programmazione Lineare e Intera

### Discorso Introduttivo del Professore: L'Arte della Modellazione

Buongiorno a tutti. Prima di iniziare con i nuovi problemi di oggi, vorrei riprendere un attimo la discussione che abbiamo iniziato ieri durante la pausa. Diversi di voi sono venuti a chiedermi chiarimenti sul senso pratico di quello che stiamo facendo in queste primissime lezioni. La perplessità mossa da alcuni era: *«Professore, ma noi adesso stiamo prendendo problemi descritti interamente a parole, tratti dal mondo reale, e li stiamo traducendo in problemi matematici... ma non li stiamo risolvendo! A cosa serve formulare un modello se poi non calcoliamo il valore numerico della soluzione?»*.

La risposta è fondamentale per capire l'impostazione di tutto questo corso: per adesso ci stiamo limitando a tradurre un'applicazione pratica in un problema di ottimizzazione (Programmazione Lineare o Programmazione Lineare Intera) perché la fase di **formulazione del modello** è in assoluto la parte più difficile, critica e delicata dell'intero processo.

Non fraintendetemi: durante il semestre impareremo tutti gli algoritmi matematici per risolvere questi problemi (l'Algoritmo del Simplesso, la Dualità, il Branch and Bound, i Piani di Taglio e gli algoritmi su Rete). Tuttavia, una volta che il modello matematico astratto è scritto bene, per risolverlo nella realtà aziendale o industriale si usano software e solutori automatici (come CPLEX, Gurobi, COIN-OR o Python/PuLP). Il software però non sa nulla del vostro problema reale: legge soltanto la matrice delle equazioni che gli date in pasto. Se voi sbagliate a scrivere anche un solo vincolo, il solutore vi restituirà la risposta esatta... a un problema del tutto sbagliato!

Vi racconto un aneddoto concreto. Qualche anno fa ho fatto da controrelatore a una tesi di laurea specialistica in ingegneria. Lo studente aveva svolto un lavoro enorme: oltre 150 pagine di tesi piene di analisi dati sofisticate, data mining, machine learning e pulizia dei dataset per un'azienda di logistica. Alla fine della tesi, per decidere l'assegnazione dei mezzi, aveva scritto un modello di Programmazione Lineare. Purtroppo, nell'impostare il vincolo principale di capacità, aveva commesso un errore di modellazione banale, concettualmente equivalente a scrivere in matematica che $1/3 + 1/5$ fa $1$. Quel singolo errore nel vincolo rendeva l'intero modello privo di senso, invalidando tutte le 150 pagine di analisi dati precedenti. È stato doloroso dover far notare che un lavoro di mesi era da buttare solo perché la parte di modellazione ottimale era stata trattata con superficialità.

Ecco perché io non parto, come fanno alcuni colleghi in altre università, scrivendo subito in astratto $\min c^T x$ con $A x \ge b$ e spiegando direttamente l'algebra del simplesso. Preferisco che impariate prima ad analizzare un problema reale, a capire quali sono le decisioni da prendere, quali le risorse limitate e come esprimere con il rigore del linguaggio matematico i vincoli operativi.

Oggi e nella prossima lezione continueremo quindi a costruire modelli per diverse famiglie di problemi reali, imparando le tecniche fondamentali per gestire costi fissi, vincoli logici, miscelazioni e scelte discrete.

---

### Esercizio 1: Pianificazione della Produzione del Tonno in Scatola

Affrontiamo come primo problema una classica applicazione di pianificazione della produzione con costi fissi di attivazione dei macchinari.

#### Testo e Dettaglio del Problema
Un'azienda alimentare produce tonno in scatola e può confezionare tre differenti tipologie di prodotto:
a) **Tonno all'Olio d'Oliva**  
b) **Tonno al Naturale**  
c) **Tonno Aromatizzato (al Peperoncino)**  

Per ciascuna tipologia di tonno prodotta, l'azienda deve attivare ed affittare un macchinario specifico per la lavorazione e l'inscatolamento. L'affitto dei macchinari comporta un costo fisso settimanale:
- Macchinario Tonno all'Olio: **200 €/settimana**
- Macchinario Tonno al Naturale: **150 €/settimana**
- Macchinario Tonno Aromatizzato: **100 €/settimana**

Ci tengo a precisare che questo costo fisso si sostiene **esclusivamente se si decide di produrre** quella specifica tipologia di tonno (anche in quantità minima). Se la produzione di tonno al naturale è pari a zero scatoloni, il macchinario non viene affittato e il costo sostenuto è $0 \text{ €}$.

Per quanto riguarda i fabbisogni di risorse per ogni singolo scatolone prodotto:
- uno scatolone di **Tonno all'Olio** richiede **3 ore** di lavoro e **4 kg** di materia prima (tonno fresco), e genera un ricavo di **6 €**;
- uno scatolone di **Tonno al Naturale** richiede **2 ore** di lavoro e **3 kg** di tonno fresco, e genera un ricavo di **4 €**;
- uno scatolone di **Tonno Aromatizzato** richiede **6 ore** di lavoro (lavorazione speciale) e **4 kg** di tonno fresco, e genera un ricavo di **7 €**.

Le risorse complessivamente disponibili per la settimana lavorativa sono:
- **Materia prima tonno:** massimo **100 kg**;
- **Ore lavorative complessive:** massimo **150 ore** di manodopera.

L'obiettivo è formulare un modello di Programmazione Lineare Intera per determinare il piano di produzione settimanale che massimizzi il profitto netto complessivo dell'azienda.

#### Guida Trasparente ai Simboli e alla Notazione

Prima di scrivere qualsiasi equazione alla lavagna, chiariamo una regola generale sulla scelta dei simboli matematici che usiamo nel corso:
- **Variabili di Decisione (Incognite):** indicano le scelte che dobbiamo compiere noi. Usiamo solitamente la lettera $x$ per le quantità fisiche quantitative (quanti kg, quante scatole produrre) e la lettera $y$ (o $w$) per le decisioni logiche o binarie $\{0, 1\}$ (attivare/disattivare, affittare/non affittare).
- **Parametri (Dati Noti):** sono i numeri fissi forniti dal testo del problema, come i prezzi, le disponibilità di magazzino, le capacità o i costi d'affitto ($D, U, F, C, a, b$). Non sono incognite!

#### Definizione delle Variabili di Decisione
Per modellare questo problema occorrono due tipi distinti di variabili:

1. **Variabili quantitative di produzione:**
   - $x_{\text{olio}} \ge 0$: numero di scatoloni di tonno all'olio da produrre in una settimana;
   - $x_{\text{nat}} \ge 0$: numero di scatoloni di tonno al naturale da produrre in una settimana;
   - $x_{\text{arom}} \ge 0$: numero di scatoloni di tonno aromatizzato da produrre in una settimana.

2. **Variabili logiche binarie di attivazione macchinari:**
   - $y_{\text{olio}} \in \{0, 1\}$: pari a 1 se si affitta il macchinario olio, 0 altrimenti;
   - $y_{\text{nat}} \in \{0, 1\}$: pari a 1 se si affitta il macchinario naturale, 0 altrimenti;
   - $y_{\text{arom}} \in \{0, 1\}$: pari a 1 se si affitta il macchinario aromatizzato, 0 altrimenti.

#### Formulazione della Funzione Obiettivo
Il profitto netto settimanale $Z$ è dato dalla differenza tra il ricavo totale ottenuto dalla vendita degli scatoloni e i costi fissi complessivi sostenuti per l'affitto dei macchinari attivati:
$$\max Z = 6 \, x_{\text{olio}} + 4 \, x_{\text{nat}} + 7 \, x_{\text{arom}} - 200 \, y_{\text{olio}} - 150 \, y_{\text{nat}} - 100 \, y_{\text{arom}}$$

#### Formulazione dei Vincoli sulle Risorse Fisiche
Disponiamo di due vincoli classici sulle risorse disponibili:

1. **Vincolo sulle ore totali di manodopera (max 150 ore):**
   $$3 \, x_{\text{olio}} + 2 \, x_{\text{nat}} + 6 \, x_{\text{arom}} \le 150$$

> ❓ **Domanda dello Studente (Sulla contemporaneità delle lavorazioni):**  
> *«Professore, scusi: ma nel vincolo delle 150 ore stiamo assumendo che possiamo produrre tutti e tre i tipi di tonno insieme? Se sommiamo le ore di tutti e tre i macchinari, non rischiamo di sforare le ore disponibili se l'azienda volesse produrli tutti?»*  
>
> 💡 **Risposta del Professore:**  
> *«Ottima domanda! Questo serve proprio a chiarire come funzionano i vincoli. Le variabili $x_{\text{olio}}, x_{\text{nat}}, x_{\text{arom}}$ sono incognite! Non stiamo fissando noi a priori se produrne uno, due o tutti e tre. Il vincolo $3 x_{\text{olio}} + 2 x_{\text{nat}} + 6 x_{\text{arom}} \le 150$ impone semplicemente che **qualsiasi combinazione di produzione** sceglieremo, il consumo totale di ore rispetti il tetto massimo di 150 ore. Sarà l'algoritmo di ottimizzazione a trovare la combinazione quantitativa perfetta che rientra nei limiti e rende massimo il guadagno.»*

2. **Vincolo sulla materia prima tonno fresco (max 100 kg):**
   $$4 \, x_{\text{olio}} + 3 \, x_{\text{nat}} + 4 \, x_{\text{arom}} \le 100$$

#### Formulazione dei Vincoli Logici di Carica Fissa (Big-M Constraints)

Ora arriviamo al punto centrale del problema: come leghiamo la produzione $x$ all'attivazione del macchinario $y$?
Vogliamo esprimere la seguente implicazione logica:
$$\text{Se produciamo una quantità positiva } x_i > 0 \implies \text{dobbiamo necessariamente attivare il macchinario } y_i = 1$$

Non possiamo usare formule non-lineari come $y_i = \text{sign}(x_i)$ oppure $y_i = x_i / x_i$, perché la Programmazione Lineare vieta rigorosamente prodotti, divisioni o funzioni discontinue tra variabili.

La tecnica corretta consiste nell'utilizzare i vincoli di **Carica Fissa** o **Vincoli Big-M**:
$$x_i \le M_i \cdot y_i$$
dove $M_i$ è un valore numerico (costante nota) rappresentante un **limite superiore valido** (*upper bound*) sulla massima quantità fisicamente producibile del prodotto $i$.

Analizziamo come funziona questo vincolo dal punto di vista logico:
- **Se $y_i = 0$ (macchinario disattivato):** Il vincolo diventa $x_i \le M_i \cdot 0 \implies x_i \le 0$. Siccome la variabile $x_i$ è non negativa ($x_i \ge 0$), l'unica soluzione ammissibile è $x_i = 0$. Il vincolo impedisce fisicamente qualsiasi produzione se il macchinario non è affittato.
- **Se $y_i = 1$ (macchinario attivo):** Il vincolo diventa $x_i \le M_i \cdot 1 \implies x_i \le M_i$. Siccome $M_i$ è stato scelto pari al massimo limite fisico di produzione, questo vincolo diventa "ridondante" (inattivo), lasciando la variabile $x_i$ libera di assumere qualsiasi valore compreso tra 0 e $M_i$.

#### Calcolo Rigoroso di Big-M ($M_i$)
1. **Per il Tonno all'Olio ($M_{\text{olio}}$):**  
   - Manodopera: $3 x_{\text{olio}} \le 150 \implies x \le 50$;  
   - Tonno fresco: $4 x_{\text{olio}} \le 100 \implies x \le 25$.  
   $$M_{\text{olio}} = \min(50, 25) = 25$$

2. **Per il Tonno al Naturale ($M_{\text{nat}}$):**  
   - Manodopera: $2 x_{\text{nat}} \le 150 \implies x \le 75$;  
   - Tonno fresco: $3 x_{\text{nat}} \le 100 \implies x \le 33.33 \implies 33$.  
   $$M_{\text{nat}} = \min(75, 33) = 33$$

3. **Per il Tonno Aromatizzato ($M_{\text{arom}}$):**  
   - Manodopera: $6 x_{\text{arom}} \le 150 \implies x \le 25$;  
   - Tonno fresco: $4 x_{\text{arom}} \le 100 \implies x \le 25$.  
   $$M_{\text{arom}} = \min(25, 25) = 25$$

> 📝 **Modello PLI Finale del Problema del Tonno:**  
> $$\begin{array}{rll}
> \max Z = & 6 x_{\text{olio}} + 4 x_{\text{nat}} + 7 x_{\text{arom}} - 200 y_{\text{olio}} - 150 y_{\text{nat}} - 100 y_{\text{arom}} & \\
> \text{s.t.} & 3 x_{\text{olio}} + 2 x_{\text{nat}} + 6 x_{\text{arom}} \le 150 & \text{(Vincolo Manodopera)} \\
> & 4 x_{\text{olio}} + 3 x_{\text{nat}} + 4 x_{\text{arom}} \le 100 & \text{(Vincolo Tonno Fresco)} \\
> & x_{\text{olio}} - 25 y_{\text{olio}} \le 0 & \text{(Carica Fissa Tonno Olio)} \\
> & x_{\text{nat}} - 33 y_{\text{nat}} \le 0 & \text{(Carica Fissa Tonno Naturale)} \\
> & x_{\text{arom}} - 25 y_{\text{arom}} \le 0 & \text{(Carica Fissa Tonno Aromatizzato)} \\
> & x_{\text{olio}}, x_{\text{nat}}, x_{\text{arom}} \ge 0, \quad x \in \mathbb{Z}^+ & \text{(Integrabilità Quantità)} \\
> & y_{\text{olio}}, y_{\text{nat}}, y_{\text{arom}} \in \{0, 1\} & \text{(Binarietà Attivazioni)}
> \end{array}$$

---

### Esercizio 2: Problema di Miscelazione e Regola di Linearizzazione

Un impianto chimico deve produrre una sostanza liquida mescolando due componenti di base $A$ e $B$:
- Litro $A$: costa 5 €, contiene 80% sostanza attiva e 10% impurità.
- Litro $B$: costa 3 €, contiene 10% sostanza attiva e 40% impurità.
- Produzione totale: esattamente 1000 litri. Sostanza attiva minima: 30%.

#### Linearizzazione Frazionaria
$$\frac{0.80 x_A + 0.10 x_B}{x_A + x_B} \ge 0.30 \iff 0.80 x_A + 0.10 x_B \ge 0.30 (x_A + x_B) \iff 0.50 x_A - 0.20 x_B \ge 0$$

---

### Esercizio 3: Facility Location e Selezione Discreta degli Impianti

- $y_j \in \{0,1\}$: attivazione deposito $j$ ($F_j$ costo fisso).
- $x_{ij} \in \{0,1\}$: assegnamento unico cliente $i$ a deposito $j$ ($C_{ij} D_i$ costo di trasporto).

$$\begin{array}{rll}
\min Z = & \sum_{j=1}^m F_j \, y_j + \sum_{i=1}^n \sum_{j=1}^m C_{ij} \, D_i \, x_{ij} & \\
\text{s.t.} & \sum_{j=1}^m x_{ij} = 1 & \forall i = 1, \dots, n \quad \text{(Semiassegnamento)} \\
& \sum_{i=1}^n D_i \, x_{ij} \le U_j \, y_j & \forall j = 1, \dots, m \quad \text{(Capacità Deposito)} \\
& y_j, x_{ij} \in \{0, 1\} & \forall i, j
\end{array}$$

---

## 2. Lezione 02: Modellazione Logistica Avanzata, Flussi su Reti e Traversamento Grafi

### Avvisi Istituzionali ed Organizzazione del Compitino

Buongiorno a tutti. Prima di iniziare con i modelli su rete di oggi, vi do un'importante comunicazione organizzativa che pubblicherò in giornata anche sul canale ufficiale del corso.

Ho fissato per **Mercoledì 30 Ottobre alle ore 16:00** (in uno slot in cui non avete altre lezioni a calendario) una **sessione straordinaria di esercitazione e ricevimento congiunto** in vista della prima prova in itinere (il compitino), che si terrà con ogni probabilità all'inizio di Novembre. La mattina del 30 svolgeremo regolarmente lezione per concludere la prima parte di programma, poi al pomeriggio ci ritroveremo in aula per svolgere insieme le tracce d'esame degli anni passati, risolvere tutti i vostri dubbi e fissare i concetti chiave prima del compitino.

### Esercizio 1: Assegnamento Quartieri ai Presidi Sanitari con Vincolo di Equilibrio

Assegnare $n$ quartieri (abitanti $A_i$) ad $m$ presidi sanitari minimizzando i costi $C_{ij}$, garantendo che il presidio meno popolato serva almeno la metà degli abitanti del presidio più popolato ($\min_j D_j / \max_j D_j \ge 1/2$).

> 📝 **Modello PLI dell'Assegnamento Sanitari:**  
> $$\begin{array}{rll}
> \min Z_{\text{costo}} = & \sum_{i=1}^n \sum_{j=1}^m C_{ij} \, x_{ij} & \\
> \text{s.t.} & \sum_{j=1}^m x_{ij} = 1 & \forall i = 1, \dots, n \quad \text{(Semiassegnamento)} \\
> & W \le \sum_{i=1}^n A_i \, x_{ij} \le Z & \forall j = 1, \dots, m \quad \text{(Soglie Min/Max per presidio $j$)} \\
> & 2 W \ge Z & \text{(Vincolo di Equilibrio $W/Z \ge 1/2$)} \\
> & x_{ij} \in \{0, 1\}, \quad Z, W \ge 0 & \forall i, j
> \end{array}$$

---

### Esercizio 2: Rete del Gas e Flusso di Costo Minimo

Rete a 5 nodi: nodi 2 (+3), 3 (+2), 4 (+1), 5 (+2) sono sorgenti di estrazione gas; nodo 1 (Raffineria) è il pozzo finale che assorbe 8 unità di gas.

```mermaid
graph LR
    3((3 [+2])) -->|c32| 2((2 [+3]))
    3((3 [+2])) -->|c34| 4((4 [+1]))
    2((2 [+3])) -->|c21| 1[[1 Raffineria +8]]
    4((4 [+1])) -->|c41| 1[[1 Raffineria +8]]
    4((4 [+1])) -->|c45| 5((5 [+2]))
    5((5 [+2])) -->|c51| 1[[1 Raffineria +8]]

    style 1 fill:#99ff99,stroke:#333
```

#### Vincolo di Conservazione del Flusso al Nodo $i$:
$$\sum_{j: (j,i) \in E} x_{ji} - \sum_{j: (i,j) \in E} x_{ij} = b_i \quad \forall i \in V$$

---

## 3. Lezione 03: Algoritmi per Cammini Minimi, Dijkstra e Bellman-Ford

### Spiegazione Parlata del Principio Generico SPT

Allora ragazzi, riprendiamo esattamente da dove ci eravamo fermati la scorsa lezione: il problema dell'**Albero dei Cammini Minimi (Shortest Path Tree - SPT)** orientato da un nodo radice $R=1$ verso tutti gli altri nodi del grafo.

Ricordiamo le celebri **Condizioni di Bellman**: dato un vettore di distanze etichettate $d$, l'albero corrente rappresenta un albero dei cammini minimi se e solo se per ogni arco $(u,v) \in E$ vale l'ineguaglianza:
$$d_u + c_{uv} \ge d_v$$
Se durante l'esecuzione dell'algoritmo troviamo un arco $(u,v)$ per cui l'ineguaglianza è violata ($d_u + c_{uv} < d_v$), significa che abbiamo scoperto una scorciatoia per raggiungere il nodo $v$ passando prima per $u$. Eseguiamo dunque l'operazione fondamentale di **rilassamento (Relaxation)**:
1. Aggiorniamo la distanza del nodo destinazione: $d_v \gets d_u + c_{uv}$;
2. Aggiorniamo il puntatore al nodo padre: $p(v) \gets u$;
3. Inseriamo $v$ nella coda $Q$ dei nodi da ri-esaminare.

#### Inizializzazione con Big-M:
$$d_R = 0, \quad d_j = M = (n-1) c_{\text{max}} + 1 \quad \forall j \neq R$$

| Iterazione | Nodo $u$ Estratto | Stella $\delta^+(u)$ | Test Bellman | Etichette $(d_1,d_2,d_3,d_4)$ | Predecessori $p$ | Lista $Q$ |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| 0 (Init) | — | — | — | $(0, 10, 10, 10)$ | $(\text{Nil}, 1, 1, 1)$ | $\{1\}$ |
| 1 | $u = 1$ | $(1,2), (1,3)$ | $0+3 < 10 \checkmark, 0+1 < 10 \checkmark$ | $(0, 3, 1, 10)$ | $(\text{Nil}, 1, 1, 1)$ | $\{2, 3\}$ |
| 2 | $u = 2$ | $(2,4)$ | $3+3 = 6 < 10 \checkmark$ | $(0, 3, 1, 6)$ | $(\text{Nil}, 1, 1, 2)$ | $\{3, 4\}$ |
| 3 | $u = 3$ | $(3,2)$ | $1+1 = 2 < 3 \checkmark$ | $(0, 2, 1, 6)$ | $(\text{Nil}, 3, 1, 2)$ | $\{4, 2\}$ |
| 4 | $u = 4$ | $(4,3)$ | $6+2 = 8 \ge 1 \text{ (No)}$ | $(0, 2, 1, 6)$ | $(\text{Nil}, 3, 1, 2)$ | $\{2\}$ |
| 5 | $u = 2$ | $(2,4)$ | $2+3 = 5 < 6 \checkmark$ | $(0, 2, 1, 5)$ | $(\text{Nil}, 3, 1, 2)$ | $\{4\}$ |
| 6 | $u = 4$ | $(4,3)$ | $5+2 = 7 \ge 1 \text{ (No)}$ | $(0, 2, 1, 5)$ | $(\text{Nil}, 3, 1, 2)$ | $\emptyset$ (Stop) |

---

## 4. Lezione 04: Cammini Minimi su DAG $O(m)$ ed Introduzione agli MST

### Algoritmo $O(m)$ su Grafi Aciclici (DAG)

In un DAG numerato topologicamente ($i < j \quad \forall (i,j) \in E$), l'etichetta $d_i$ diventa **definitiva** non appena il ciclo `for` scansiona il nodo $i$.

> ❓ **Domanda dello Studente (Sulla somma di una costante ai costi):**  
> *«Professore, ma se ci sono costi negativi, non potremmo semplicemente aggiungere una costante $K > 0$ a tutti gli archi del grafo in modo da renderli tutti positivi e poi applicare Dijkstra?»*  
>
> 💡 **Risposta del Professore:**  
> *«Attenzione! Questo è uno dei trabocchetti più insidiosi d'esame. Nei cammini minimi, due cammini diversi tra la radice $R$ ed un nodo $v$ possono contenere un **numero differente di archi** (ad esempio un cammino da 2 archi ed un cammino alternativo da 5 archi). Se sommiamo $K > 0$ a ogni singolo arco, il costo del primo cammino aumenta di $2K$, mentre il costo del secondo aumenta di $5K$! Avete alterato la proporzione relativa tra i cammini, penalizzando pesantemente quelli con più archi. Di conseguenza, il cammino minimo nel grafo modificato può non corrispondere affatto al cammino minimo nel grafo originale!»*

---

## 5. Lezione 05: Caratterizzazioni di Ottimalità per MST ed Analisi Parametrica

> ### Teorema (Ottimalità per Cicli $e \notin E_T$)
> Un albero di copertura $T$ è ottimo (MST) **se e solo se** per ciascun arco fuori albero $e = (i,j) \notin E_T$, il peso di $e$ è **maggiore o uguale** del peso di qualunque altro arco appartenente al ciclo fondamentale $C(T, e)$ formato aggiungendo $e$ a $T$:
> $$c_e \ge c_{uv} \quad \forall (u,v) \in C(T, e) \quad \text{($c_e$ è il peso massimo del ciclo)}$$

> ### Teorema (Ottimalità per Tagli $e \in E_T$)
> Un albero di copertura $T$ è ottimo (MST) **se e solo se** per ciascun arco dell'albero $e = (i,j) \in E_T$, il suo peso è **minore o uguale** del peso di qualunque altro arco appartenente al taglio fondamentale $\delta(S)$ generato rimuovendo $e$ da $T$:
> $$c_e \le c_{uv} \quad \forall (u,v) \in \delta(S) \quad \text{($c_e$ è il peso minimo del taglio)}$$

### Analisi Parametrica dei Costi $(\gamma, \beta)$
- **Regione Ammissibile di Ottimalità:** $\gamma \le 20 \land \beta \le 20$.
- **Condizione per l'UNICITÀ dell'Albero Ottimo:** $\gamma < 20 \land \beta < 20$.
