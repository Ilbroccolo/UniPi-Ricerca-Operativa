# 📊 LEZIONE 01: TRASCRIZIONE DUPLEX (Spiegazione Umana + Lavagna)

> **Docente**: Prof. Luca Mencarelli  
> **Struttura**: Per ogni sezione trovi **1. Come lo spiega a voce il professore** e **2. Cosa scrive tecnicamente alla lavagna**.

---

## 📌 PARTE 1: INTRODUZIONE ALLA MODELLAZIONE E PERCHÉ NON RISOLVIAMO SUBITO

### 🗣️ Come lo spiega il Prof (A Voce)
"Ragazzi, ieri qualcuno di voi mi ha chiesto durante la pausa: *'Ma come mai stiamo solo prendendo problemi scritti a parole e li stiamo traducendo in formule matematiche senza risolverli?'*.

Voglio chiarire una cosa: durante questo corso impareremo tutti gli algoritmi per risolvere questi problemi. Ma la parte più importante in assoluto — quella che vi servirà davvero nel mondo del lavoro — è **saper formulare il problema**.

Ho fatto da controrelatore a una tesi dove lo studente ha fatto 150 pagine di lavoro con Machine Learning, Data Mining e analisi dati pazzesche... ma il modello di ottimizzazione iniziale era completamente sbagliato. Risultato? 150 pagine di lavoro buttate nel cestino solo perché l'equazione di base era sbagliata. 

Per questo non parto subito a darvi le matrici e gli algoritmi come fanno altri colleghi. Prima dobbiamo imparare a prendere un problema reale e tradurlo in matematica senza commettere errori. Se sbagliate a modellare, qualsiasi software o algoritmo vi darà risultati inutili."

---

### 🖍️ Cosa scrive il Prof alla Lavagna

```
======================================================================
  PROCESSO DECISIONALE & MODELLAZIONE MATEMATICA
======================================================================

  [ Problema Reale a Parole ] 
             │
             ▼  (Fase di Modellazione / Traduzione)
  [ Modello Matematico di Ottimizzazione ]
     • Variabili di Decisione: x ∈ ℝⁿ o ℤⁿ
     • Funzione Obiettivo: max/min Z(x)
     • Vincoli Algebrici: A x ≤ b, x ≥ 0
             │
             ▼  (Fase di Risoluzione)
  [ Solutore / Software / Algoritmo ] ➔ Soluzione Ottima x*
======================================================================
```

---

## 🐟 PARTE 2: ESERCIZIO 1 - PIANIFICAZIONE DELLA PRODUZIONE DI TONNO

### 🗣️ Come lo spiega il Prof (A Voce)
"Facciamo un esercizio semplice di pianificazione della produzione. C'è un'azienda che inscatola tonno e può produrre tre tipi diversi: **Tonno all'Olio**, **Tonno al Naturale** e **Tonno Aromatizzato**.

Per produrre ciascun tipo di tonno serve affittare un macchinario specifico. L'affitto costa €200 a settimana per l'olio, €150 per il naturale e €100 per l'aromatizzato. Attenzione: questo macchinario lo affitto e lo pago **solo se decido di produrre quel tipo di tonno**. Se non ne produco nemmeno uno scatolone, non affitto nulla e spendo zero.

Poi abbiamo le risorse: per fare uno scatolone di tonno all'olio servono 3 ore di lavoro e 4 kg di tonno. Per quello al naturale servono 2 ore e 3 kg di tonno. Per quello aromatizzato servono 6 ore e 4 kg di tonno. In totale l'azienda ha a disposizione **150 ore di lavoro** e **100 kg di tonno** a settimana.
Il ricavo di vendita per ogni scatolone è €6 per l'olio, €4 per il naturale e €7 per l'aromatizzato.

Come si procede?
**Passo 1: Quali decisioni dobbiamo prendere?**
Dobbiamo decidere quanti scatoloni produrre di ciascun tipo ($x_{olio}, x_{nat}, x_{aro}$).
Ma basta questo? No! Dobbiamo anche decidere se affittare o no il macchinario. Ci serve una variabile logica ($y_{olio}, y_{nat}, y_{aro}$) che vale 1 se produciamo quel tonno (e quindi affittiamo il macchinario) e 0 se non produciamo niente.

**Passo 2: La Funzione Obiettivo.**
Il profitto è: *(Ricavo di vendita per scatola × scatoloni prodotte)* **MENO** *(Costo di affitto dei macchinari utilizzati)*.

**Passo 3: I Vincoli e il legame tra $x$ e $y$.**
I vincoli sulle ore e sui kg sono facili: la somma dei tempi deve essere $\le 150$ e la somma dei kg deve essere $\le 100$.
Ma come colleghiamo la produzione $x$ con l'affitto $y$? Se $x_{olio} > 0$, allora $y_{olio}$ deve valere 1.
Come si scrive in matematica? Si usa una costante $M$ grande a sufficienza e si scrive $x_{olio} \le M \cdot y_{olio}$. 
Se $y_{olio} = 0$, l'equazione diventa $x_{olio} \le 0$, quindi non posso produrre niente! Se $y_{olio} = 1$, diventa $x_{olio} \le M$, e posso produrre fino al massimo fisicamente possibile. Quanto vale $M$? Siccome ho 100 kg di tonno e ce ne vogliono 4 kg a scatola, al massimo posso fare 25 scatoloni. Quindi metto $M = 25$."

---

### 🖍️ Cosa scrive il Prof alla Lavagna

```
======================================================================
1. DATI DEL PROBLEMA
======================================================================
  Prodotti: Olio (O), Naturale (N), Aromatizzato (A)

  • Costo Affitto Macchinario (F):  F_O = 200€,  F_N = 150€,  F_A = 100€
  • Tempo di lavorazione (a):       a_O = 3h,    a_N = 2h,    a_A = 6h     | Disp: 150h
  • Materia prima Tonno (b):        b_O = 4kg,   b_N = 3kg,   b_A = 4kg    | Disp: 100kg
  • Ricavo di vendita (r):          r_O = 6€,    r_N = 4€,    r_A = 7€

======================================================================
2. VARIABILI DI DECISIONE
======================================================================
  • Quantità prodotte (intere non negative):
      x_O, x_N, x_A ∈ ℤ⁺    (numero scatoloni prodotti)

  • Variabili Logiche di Attivazione (binarie):
      y_O, y_N, y_A ∈ {0, 1}
      dove y_j = 1 se produco il tipo j (affitto macchinario), 0 altrimenti.

======================================================================
3. MODELLO MATEMATICO (PLI)
======================================================================
  max Z = (6 x_O + 4 x_N + 7 x_A) - (200 y_O + 150 y_N + 100 y_A)  [Profitto Netto]

  s.t.
    3 x_O + 2 x_N + 6 x_A ≤ 150                                [Ore Lavoro]
    4 x_O + 3 x_N + 4 x_A ≤ 100                                [Kg Tonno]

    x_O ≤ 25 y_O   (con M_O = ⌊100/4⌋ = 25)                    [Carica Fissa Olio]
    x_N ≤ 34 y_N   (con M_N = ⌊100/3⌋ = 33.3 ➔ 34)              [Carica Fissa Naturale]
    x_A ≤ 25 y_A   (con M_A = ⌊100/4⌋ = 25)                    [Carica Fissa Aromi]

    x_O, x_N, x_A ∈ ℤ⁺
    y_O, y_N, y_A ∈ {0, 1}
======================================================================
```

---

## 🏭 PARTE 3: ESERCIZIO 2 - LOCALIZZAZIONE DEPOSITI E RIFORNIMENTO CENTRI

### 开启 🗣️ Come lo spiega il Prof (A Voce)
"Passiamo a un problema di logistica e distribuzione. 

Immaginate un'azienda che produce pasta e ha $n$ centri di distribuzione (negozi o supermercati) da servire ogni mese. Ciascun negozio $i$ richiede una quantità $D_i$ di scatole di pasta.
L'azienda dispone di $m$ possibili depositi centrali. Ogni deposito $j$ ha una capacità massima di $U_j$ scatole al mese.
Se decidiamo di attivare e aprire il deposito $j$, dobbiamo pagare un costo fisso mensile di gestione $F_j$. Se il deposito non serve nessun negozio, lo teniamo chiuso e la gestione costa zero. In più, per ogni scatola inviata dal deposito $j$, paghiamo un costo unitario di trasporto $C_j$.

**Variante A: Il vincolo del Semiassegnamento (1 solo deposito per negozio).**
Nel testo c'è scritto: *'Ogni centro viene rifornito da un unico deposito centrale'*.
Cosa significa? Che per ogni negozio dobbiamo scegliere quale deposito lo serve.
Usiamo la variabile $x_{ij} = 1$ se il negozio $i$ è servito dal deposito $j$, e $0$ altrimenti.
Siccome ogni negozio deve avere UN SOLO deposito, per ogni negozio $i$ la somma di $x_{ij}$ su tutti i depositi $j$ deve fare esattamente 1! Questo si chiama vincolo di **Semiassegnamento**.

E la capacità dei depositi? Se il deposito $j$ è attivo ($y_j = 1$), la somma delle scatole inviate a tutti i negozi serviti deve essere $\le U_j$. Se $y_j = 0$, la capacità diventa 0 e non possiamo inviare nulla.
Quindi scriviamo: $\sum D_i x_{ij} \le U_j y_j$.

---

**Variante B: Cosa cambia se il rifornimento è frazionabile?**
Se togliamo il vincolo che il negozio debba essere servito da un unico deposito e ammettiamo che più depositi possano mandare scatoloni allo stesso negozio, cosa succede?
La variabile $x_{ij}$ non può più essere $0$ o $1$! Diventa una variabile quantitativa $z_{ij} \ge 0$, cioè il **numero effettivo di scatole** che il deposito $j$ manda al negozio $i$.
A questo punto non usiamo più il semiassegnamento, ma il vincolo di **Soddisfacimento della Domanda**: la somma delle scatole inviate da tutti i depositi al negozio $i$ deve fare esattamente la domanda $D_i$, cioè $\sum_j z_{ij} = D_i$.

---

**Variante C: Scegliere la capacità del deposito tra varie taglie.**
Supponiamo infine di non avere una capacità fissa $U_j$, ma di poter scegliere se affittare per il deposito $j$ un locale piccolo, medio o grande (scegliendo tra $K$ possibili taglie di capacità $U_{1j}, U_{2j}, \dots, U_{Kj}$ con costi $F_{kj}$).
Introduciamo la variabile $w_{kj} = 1$ se scegliamo la taglia $k$ per il deposito $j$.
Siccome possiamo scegliere al massimo una sola taglia, imponiamo $\sum_{k=1}^K w_{kj} \le 1$.
E il vincolo di capacità diventa semplicemente: $\sum_i z_{ij} \le \sum_k U_{kj} w_{kj}$."

---

### 🖍️ Cosa scrive il Prof alla Lavagna

```
======================================================================
ESERCIZIO 2: DEPOSITI E CENTRI DI DISTRIBUZIONE
======================================================================
DATI:
  • i = 1...n  (Centri / Negozio),  Richiesta mensile = D_i
  • j = 1...m  (Depositi),           Capacità massima = U_j
  • F_j = Costo fisso mensile gestione deposito j (se attivo)
  • C_j = Costo unitario trasporto per scatola dal deposito j

----------------------------------------------------------------------
VARIANTE A: RIFORNIMENTO UNICO (SEMIASSEGNAMENTO)
----------------------------------------------------------------------
VARIABILI:
  y_j ∈ {0, 1}    (1 se deposito j è attivo, 0 altrimenti)
  x_ij ∈ {0, 1}   (1 se negozio i è rifornito interamente da deposito j)

MODELLO:
  min Z = ∑_{j=1}^m F_j y_j  +  ∑_{j=1}^m C_j ( ∑_{i=1}^n D_i x_ij )

  s.t.
    ∑_{j=1}^m x_ij = 1         ∀ i = 1...n    [Semiassegnamento: 1 solo deposito per negozio]
    ∑_{i=1}^n D_i x_ij ≤ U_j y_j  ∀ j = 1...m  [Capacità & Attivazione Deposito]

    x_ij ∈ {0, 1},  y_j ∈ {0, 1}

----------------------------------------------------------------------
VARIANTE B: RIFORNIMENTO FRAZIONABILE (QUANTITATIVO)
----------------------------------------------------------------------
VARIABILI:
  y_j ∈ {0, 1}    (1 se deposito j è attivo, 0 altrimenti)
  z_ij ∈ ℤ⁺       (numero effettivo di scatole inviate da j a i)

MODELLO:
  min Z = ∑_{j=1}^m F_j y_j  +  ∑_{j=1}^m ∑_{i=1}^n C_j z_ij

  s.t.
    ∑_{j=1}^m z_ij = D_i       ∀ i = 1...n    [Soddisfacimento Domanda del Negozio]
    ∑_{i=1}^n z_ij ≤ U_j y_j   ∀ j = 1...m    [Capacità & Attivazione Deposito]

    z_ij ≥ 0 (Interi),  y_j ∈ {0, 1}

----------------------------------------------------------------------
VARIANTE C: SCELTA TAGLIA CAPACITÀ DEPOSITO
----------------------------------------------------------------------
VARIABILI:
  w_kj ∈ {0, 1}   (1 se per il deposito j scelgo la taglia k ∈ {1...K})

MODELLO (Modifica Vincoli e Costi):
  min Z = ∑_{j=1}^m ∑_{k=1}^K F_kj w_kj  +  ∑_{j=1}^m ∑_{i=1}^n C_j z_ij

  s.t.
    ∑_{k=1}^K w_kj ≤ 1        ∀ j = 1...m    [Scelta al più di una sola taglia]
    ∑_{i=1}^n z_ij ≤ ∑_{k=1}^K U_kj w_kj  ∀ j = 1...m  [Capacità Flessibile & Attivazione]
======================================================================
```

---

## 🎓 PRINCIPIO TEORICO APPLICATO: MODELLARE VALORI DISCRETI FINITI

### 🗣️ Come lo spiega il Prof (A Voce)
"Guardate che quello che abbiamo fatto per scegliere la capacità del deposito è una tecnica generale utilissima!
Immaginate di avere una variabile $x$ (ad esempio il diametro di una tubazione) che non può prendere un valore qualsiasi, ma deve essere per forza uno tra un insieme discreto di valori possibili $V_1, V_2, \dots, V_K$.

I software di ottimizzazione non accettano direttamente l'istruzione 'scegli un valore tra questi 5 dati'. 
Come si risolve? 
Si introducono $K$ variabili logiche $y_1, y_2, \dots, y_K \in \{0, 1\}$. 
Si scrive un vincolo di semiassegnamento per dire che al massimo una sola $y_k$ può valere 1 ($\sum y_k = 1$).
E poi si sostituisce la variabile $x$ in tutte le equazioni del problema con l'espressione lineare $x = \sum_{k=1}^K V_k y_k$.
In questo modo manteniamo il problema perfettamente lineare e costringiamo la variabile a prendere esattamente uno dei valori ammessi!"

---

### 🖍️ Cosa scrive il Prof alla Lavagna

```
======================================================================
TECNICA GENERALE: VARIABILI A VALORI DISCRETI ARBITRARI
======================================================================
PROBLEMA:
  Una variabile x deve assumere un valore nell'insieme finito {V_1, V_2, ..., V_K}.

FORMULAZIONE LINEARE:
  1. Introduco K variabili binarie:
       y_1, y_2, ..., y_K ∈ {0, 1}

  2. Vincolo di Scelta Unica (Semiassegnamento):
       ∑_{k=1}^K y_k = 1    (oppure ≤ 1)

  3. Sostituzione della variabile x in tutte le formule del modello:
       x = ∑_{k=1}^K V_k y_k
======================================================================
```
