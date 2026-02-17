# INTRODUZIONE
Un'algoritmo è una serie di istruzioni ben definite, codificate in un linguaggio x che mira al risolvere un dato problema.
Con "Architettura del calcolatore" intendiamo l'insieme della unità principali che compongono il calcolatore e come interagiscono tra di esse.
Le funzioni base di un calcolatore possono essere suddivise in:
- Memorizzare dei dati
- Elaborare dei dati
- Trasferire dei dati
- Controllo
## IL PROCESSORE
Il processore è costituito da 2 parti fondamentali:
- **L'unità logico-aritmetica**, che fa i calcoli.
- **L'unità di controllo**, che fa eseguire l'istruzione tramite i cambiamenti di stato.
e due registri definiti (**Special use register**):
Nel processore vi sono alcuni registri specializzati per alcune funzioni: ***il registro PC*** o program counter che contiene al suo interno l’indirizzo della parola di memoria con l’istruzione de eseguire.
Il registro $IR$ o instruction register che contiene l’istruzione corrente e permette alle varie componenti del processore di eseguire quest’istruzione correttamente, quindi la decodifica.
Quindi ciò che avviene è che il PC ”punta” all’indirizzo con la parola di memoria con l’istruzione da eseguire e la trasferisce all’IR che, conterrà l’istruzione in tutti i suoi passi e sovrascrivera la precedente istruzione.
Quest’interfaccia permette insomma di dialogare tra processore e memoria, cio avviene attraverso dei segnali di controllo che permettono di far capire al processore o alla memoria come comportarsi: vi è ad esempio il segnale di lettura inviato dal processore alla memoria che appunto permette di dire alla memoria di mandare un dato o un istruzione da un determinato indirizzo al processore.
Un altro segnale, inviato dalla memoria al processore è quello di scrittura in cui la memoria dice al processore di scrivere quel determinato dato in un registro.
## La Memoria Centrale
La memoria si suddivide in due categorie:
- Volatile
- Non Volatile
La memoria volatile è un tipo di memoria che "perde" i dati quando il calcolatore viene spento, ed anch'essa si suddivide in due componenti:
- RAM (Random access memory), che immagazzina i programmi in esecuzione.
- CACHE, che immagazzina i dati più utilizzati per tenerli pronti al momento di riutilizzarli.
La memoria non volatile è la ROM (Read only Memory), che immagazzina i dati a lungo termine, anche a spegnimento del calcolatore.
## MACCHINA DI VON NEUMANN
La macchina di Von Neumann è un concetto diverso rispetto alla MdT, infatti si focalizza sul concetto "pratico" della risoluzione di un algoritmo, essa infatti è composta da:
- CPU
- MEMORIA
- BUS
- I/O
> A livello teorico, è una terna di {N, IS, P}:
> - N = $\{0,1,2,3...\}$, è l'insieme dei numeri naturali (rappresenta l'alfabeto della macchina).
> - IS = $\{ZERO, INC, SOM, SOT, MOL\}$, è l'istruction set, ovvero l'insieme delle istruzioni generiche della macchina.
> - P =  ${I_0, I_1, I_2, I_3,...,I_p}$, è una sequenza finita e non vuota di istruzioni prese da IS, con valori specifici della variabili, andando a comporre un programma.
## Layer fondamentali
L'architettura è un "contratto tra hardware e software" (se l'architettura è 32bit/64bit, il sistema operativo o le applicazioni devo corrispondere alla versione dell'architettura).
l'implementazione riguarda invece come l'architettura viene realizzata fisicamente.
l'informatica è suddivisa in 3 layer fondamentali:
- APPLICAZIONI
- SISTEMA OPERATIVO
- HARDWARE
L'architettura di von neumann è tutt'oggi il fondamento architetturale.
il bottleneck di von neumann è un effetto causato dalla differenza di banda tra CPU e memoria, come se la latenza della memoria facesse da "tappo" alla cpu.
## IL MICROPROCESSORE
il Microprocressore è stato una rivoluzione, avendo un'intera cpu su un singolo chip di silicio, portando l'informatica in tutti i contesti, tra cui il personal computer.
Ulteriore agevolazione dall'integrazione in un singolo chip, si elimina il BUS e quindi riduciamo drasticamente il rallentamento provocato da esso, evitando il bottleneck.
## EVOLUZIONE ISA (ISTRUCTION SET ARCHITECTURE)
- CISC (Complex istruction set computer)
istruzioni complesse che eseguono operazioni elaborate in un singolo comando.
esempi sono: x86 intel e amd.
- RISC (REDUCED ISTRUCTION SET COMPUTER)
set di istruzioni semplificate ma efficienti.
esempi sono: ARM per i dispositivi mobile, MIPS per sistemi embedded.
- le architetture moderne utilizzano un sistema ibrido tra CISC e RISC
## ARCHITETTURE SUPERSCALARI
Un processore **Superscalare** ha più unità funzionali (ALU multiple). Per sfruttarle al meglio usa l'**Esecuzione Fuori Ordine**:
- Il processore analizza un "finestra" di istruzioni.
- Se un'istruzione è ferma (es. aspetta un dato dalla RAM), la CPU cerca istruzioni successive che siano indipendenti e le esegue subito.
- Il **Reorder Buffer (ROB)** garantisce che, anche se eseguite fuori ordine, i risultati vengano scritti nei registri nell'ordine originale del programma per mantenere la coerenza.
## SUPERPIPELINING
Il Superpipelining rappresenta una tecnica avanzata che consiste nell'aumentare significativamente il numero di stadi che compongono la pipeline del processore. Attraverso questa suddivisione più granulare, ogni singolo stadio della pipeline viene ridotto in termini di complessità e durata, permettendo così di raggiungere frequenze di clock molto più elevate rispetto alle architetture tradizionali.

---
Entrambe le tecnologie, sia i processori superscalari che il superpipelining, contribuiscono in modo sostanziale all'aumento del throughput complessivo del sistema, ovvero la quantità totale di istruzioni che possono essere elaborate nell'unità di tempo.
## Issue Width
L’**issue width** rappresenta il **numero massimo di istruzioni** che un processore *superscalare* può inviare in esecuzione in un singolo ciclo di clock.
Ad esempio, se un processore ha un’issue width di **4**, significa che può potenzialmente eseguire fino a **4 istruzioni nello stesso ciclo**.
> Aumentare la issue width migliora il parallelismo, ma aumenta anche la complessità e il rischio di conflitti tra istruzioni.
# ISTRUZIONI MACCHINA
Quando si programma in Assembly, sarà inevitabile il contatto diretto con l’ISA (INSTRUCTION SET ARCHITECTURE), dato che in linguaggi ad alto livello sarà il compilatore a trasformare il codice in assembly.
> Le operazioni di base che il processore può eseguire con la memoria sono due:
*Read → un dato viene prelevato dalla memoria e portato nei registri del Processore.
Write → un dato viene passato dai registri alla memoria*
---

L’informazione è immagazzinata in memoria sotto forma di un vettore di parole, ognuna di lunghezza che varia da 16 a 64 bit.
Ad ogni parola è associato un indirizzo binario univoco, principalmente si usano numeri nell’intervallo $[0,2^m]$ con $m=$ numero di bit.
### SCHEMI DI INDIRIZZAMENTO BYTE
- Big-Endian: l’indirizzo aumenta al diminuire del peso aritmetico del Byte.
- Little-Endian: L’indirizzo aumenta all’aumentare del peso aritmetico del Byte.
---
Esistono 4 categorie di Istruzioni macchina:
- Trasferimento dei Dati (Load e Store)
- Operazioni Aritmetiche (Add, Sub, Mul)
- Controllo di Esecuzione
- Trasferimenti I/O
### LISTA ISTRUZIONI
- LDR R2, LOC
Legge il contenuto della locazione di memoria LOC e carica i contenuti nel registro R2.
- MOV R2, \#COSTANTE
sposta l'indirizzo di costante in R2
- ADD R4, R2, R3
Somma il contenuto di R2 e R3 e inserisce la somma nel registro R4.
- STR R4, LOC
Copia il contenuto di R4 nella locazione di memoria LOC.
- SUB R4,R2,R3
Sottrae i contenuti dei registri R2 e R3 e inserisce il risultato in R4.
### DIRETTIVE ASSEMBLATORE
- DCD
Definisce una o più parole di memoria, come inizializzare un array.
- FILL
riserva una porzione di memoria specifica ma non la inizializza.
- EQU
associa un valore numerico ad una costante.
- ORIGIN
indica da quale indirizzo di memoria cominciare.
- END
### BIT DI STATO
![Screenshot From 2026-01-15 21-14-49.png](Screenshot_From_2026-01-15_21-14-49.png)
Il processore tiene traccia di alcune informazioni relative all’esito di alcune operazioni, che servono come condizioni per l’istruzione di salto.

| N (Negativo) | 1 se risulta negativo, 0 se positivo o nullo |
| --- | --- |
| Z (Zero) | 1 se risulta nullo, 0 altrimenti |
| C (Riporto) | 1 se trabocco in binario naturale, 0 altrimenti (carry) |
| V (Trabocco) | 1 se trabocco in comp. a due, 0 altrimenti (overflow) |

I bit di stato vengono aggiornati con:
- Adds
- Subs
## SALTI
I salti si fanno tramite l’aggiornamento dei bit di stato e l’utilizzo di uno dei comandi:
- BEQ → Uguale
- BNE → Diverso
- BLT → Più piccolo di
- BGT → Più grande di
- BLE → Più piccolo o uguale
- BGE → Più grande o uguale
## PILA
La pila è una lista di elementi, alla quale si possono inserire elementi solo nella cima.
Stack Pointer (SP) → Registro che punta alla cima della pila [R13].

![stack_representation.jpg](stack_representation.jpg)
È possibile eseguire solo due operazioni:
- PUSH → porre un elemento in cima
```nasm
add SP, SP, #4
stmfd sp!, {r1} 
```
- POP → toglie un elemento dalla cima
```nasm
ldmfd sp!, {r1}
add sp, sp, #4
```

# MEMORIA
La **memoria** di un calcolatore può essere vista come un **contenitore ordinato di celle**, ognuna delle quali può contenere un dato.
Ogni **cella di memoria** ha una **dimensione di 1 byte** (8 bit) e possiede un **indirizzo univoco** che serve per localizzarla e accedere al valore che contiene.
Gli **indirizzi** partono sempre da **zero**, quindi l’indirizzo dell’ultima cella corrisponde al **numero totale di celle meno uno**.
Ad esempio, una memoria composta da 1024 celle avrà indirizzi che vanno da 0 a 1023.

---
L’**ampiezza dello spazio di indirizzamento** dipende dal numero di linee del **bus indirizzi** del sistema.
In generale, se il bus indirizzi ha *n* linee, lo spazio di indirizzamento sarà pari a:
$2^n$
Questo valore indica **quante celle di memoria** è possibile indirizzare.
Ad esempio:
- con 16 linee di indirizzi → $(2^{16} = 65.536)$ locazioni (64 KB);
- con 32 linee → $(2^{32} = 4.294.967.296)$ locazioni (4 GB).
In un sistema operativo moderno, la memoria può essere **riassegnata** a più processi, grazie alle tecniche di **allocazione dinamica** e **memoria virtuale**.

Un esempio pratico è il **file system FAT32**, che non può gestire file superiori a 4 GB, ma può accettare più trasferimenti da dimensioni inferiori (ad esempio, due file da 3 GB ciascuno).

---
Il **contenuto della memoria principale** rimane memorizzato solo **finché il computer è alimentato**.

Quando l’alimentazione viene interrotta, i dati vengono persi: per questo motivo la memoria RAM è detta **volatile**.

---
### BIOS
> All’interno della memoria di sistema è presente una sezione fondamentale: il BIOS (Basic Input/Output System)

Il BIOS contiene due fasi principali:
1. **Bootstrap** – avvia il sistema e immette sul bus le prime istruzioni necessarie per inizializzare i dispositivi di base;
2. **POST (Power-On Self Test)** – esegue i controlli di base e carica il sistema operativo.
Le aree di memoria che contengono il BIOS e altri **firmware** sono realizzate in tecnologia **ROM (Read Only Memory)**, che è **non volatile**: mantiene i dati anche senza alimentazione.
Queste sezioni possono essere riprogrammate solamente tramite il programma di setup del bios o cambiando direttamente il bios.

> Il bios però è stato superato dalla tecnologia UEFI, che fornisce le stesse principali funzioni del bios migliorandole come:

- Supporto dischi GPT (Bios supportava Solo dischi MBR)
GPT $\to$ permette di avere molte partizioni, il limite lo dichiara il sistema operativo (windows limita a 128 partizioni), tra l'altro i dati di avvio e di gestione delle partizioni sono immagazzinate in più posizioni.
MBR $\to$ è un sistema vecchio che permette di avere solo 4 partizioni primarie, dato che ogni partizione occupa 16 byte e la partizione di gestione è grande 64 byte, altro lato negativo è che i dati di avvio e di gestione sono immagazzinati in una sola partizione portando il disco ad un rischio di corruzione maggiore ai dischi GPT.
- Interfaccia grafica migliorata, con integrazione di cursore del mouse
- introduzione di funzionalità come Secure Boot, che accetta solo programmi firmati
---
Esistono due principali tipi di memoria RAM:
- **DRAM (Dynamic RAM)**: più lenta ma economica, utilizzata come memoria principale del sistema.

I moduli DRAM sono installati negli **slot DIMM** della scheda madre.

## Cache e Gerarchie di Memoria
La memoria principale (RAM) è molto più lenta rispetto al processore.
Per ridurre questa latenza, si usano le **cache**, memorie piccole ma velocissime.
Si hanno due proprietà:
- Spaziale    
Se il processore preleva un dato ad indirizzo X, allora sarà probabile che preleverà anche i dati in X + q ( $Q \neq 0$, Q intero e valore piccolo). 
- Temporale  
Se il processore preleva un dato nel tempo $t_1$, è probabile che venga prelevato di nuovo anche in $t_1 + q$ ( $Q \neq 0$, Q intero e valore piccolo).
> Se i dati di cui ha bisogno il processore sono già nella Cache, si parlerà di Cache Hit.

 >Se i dati di cui ha bisogno il processore non si trovano nella Cache, si parlerà di Cache Miss e inevitabile perdita di efficienza. 
  
### Livelli di cache
- **L1:** la più veloce, ma piccola e dedicata a ciascun core.
- **L2:** intermedia per velocità e capacità.
- **L3:** condivisa tra i core, più grande ma più lenta.
Quando un dato non è presente nella cache (**cache miss**), deve essere recuperato dalla RAM, rallentando l’esecuzione.
#### Politiche di Sostituzione
- **LRU (Least Recently Used):** rimuove il dato usato meno recentemente.
- **FIFO (First In, First Out):** elimina il dato più vecchio.
- **Random:** scelta casuale, utile quando si vuole semplicità di implementazione.
---
## Memoria Virtuale

La **memoria virtuale** consente a ogni programma di vedere uno **spazio di memoria continuo e più ampio** rispetto a quello fisico disponibile utilizzando il disco fisso.
Il sistema operativo traduce gli **indirizzi virtuali** in **indirizzi fisici reali** tramite la **MMU (Memory Management Unit)**
> la memoria virtuale è più lenta rispetto alla RAM
### Tecniche di mappatura
- **Paginazione:** la memoria è divisa in blocchi di dimensione fissa (pagine).
- **Segmentazione:** la memoria è suddivisa in segmenti logici di dimensione variabile.
- **Ibridi:** combinano entrambi i metodi.
> Grazie alla memoria virtuale, parte del disco può essere usata come memoria di supporto (swap).
# BUS
Il **bus** è un insieme di fili (chiamati *linee*) che collegano tra loro le varie parti del computer:
- il **processore (CPU)**,
- la **memoria**,
- e i **dispositivi di input/output (I/O)**.
In pratica, è come una **strada a più corsie** su cui viaggiano i dati.

Ogni filo del bus trasporta un bit (0 o 1).
Tutti i componenti principali del computer “si affacciano” su questa strada per leggere, scrivere o scambiare informazioni.
Il **modello di von Neumann** prevede che:
- i dati e le istruzioni risiedano in memoria,
- il processore li legga, li elabori e li riscriva,
- e che tutto questo avvenga tramite il **bus**.
Quindi, la maggior parte delle operazioni di un computer sono **trasferimenti di bit** tra CPU, memoria e dispositivi di I/O.
---
il **processore** è il **Master** (cioè quello che comanda),
mentre **memoria** e **I/O** sono gli **Slave** (cioè quelli che eseguono le richieste).
Il bus è il “mezzo di trasporto” che collega tutto.
Ci sono due tipi principali di trasferimenti:
- **Scrittura (Write)**: il processore invia dati alla memoria o ai dispositivi di I/O.
- **Lettura (Read)**: il processore riceve dati dalla memoria o dagli I/O.
Per gestire queste operazioni, il bus è diviso in **tre sottoblocchi** principali:

| Tipo di Bus | Nome | Funzione |
| --- | --- | --- |
| Bus degli indirizzi | **Address Bus (ABus)** | Specifica *dove* leggere o scrivere in memoria. |
| Bus dei dati | **Data Bus (DBus)** | Trasporta *i dati veri e propri*. |
| Bus di controllo | **Control Bus (CBus)** | Indica *cosa fare* e *quando* (es. leggere, scrivere, fine operazione). |

Il **Control Bus** contiene linee che dicono:
- se l’operazione è **tra memoria e CPU** oppure **tra I/O e CPU**;
- se è una **lettura (R/W = 1)** o **scrittura (R/W = 0)**;
- se il trasferimento è **finito (Wait = 1)** o **in corso (Wait = 0)**.
Il bus ha anche un **clock** (una specie di metronomo) che regola il tempo dei trasferimenti.
Tutto avviene in modo **sincronizzato**: prima si indica l’indirizzo, poi il tipo di operazione, poi si inviano o ricevono i dati.
Il segnale *Wait* serve perché la **memoria è più lenta** della CPU → questo crea il famoso **collo di bottiglia di von Neumann**: la CPU deve aspettare la memoria.
Ogni bus ha un certo numero di linee (fili).
- L’**Address Bus** determina **quanta memoria può essere indirizzata**.
Esempio: con 16 linee si possono indirizzare $(2^{16} = 65.536)$ locazioni (cioè 64 KB).
- Il **Data Bus** indica **quanti bit si possono trasferire per volta** (cioè il “grado di parallelismo”).
Esempio: un DBus a 32 linee trasferisce 32 bit (4 byte) alla volta.

Sulla **scheda madre** del computer il bus di sistema è realizzato dal **Chipset**, cioè un insieme di circuiti che collegano tutto.
Si divide in due parti:
- **NorthBridge** → collega la CPU con la memoria e la scheda video.
- **SouthBridge** → collega la CPU con le periferiche (tastiera, USB, disco, ecc.).
Nel tempo i bus sono diventati sempre più veloci:

| Standard | Larghezza | Frequenza | Note |
| --- | --- | --- | --- |
| **ISA** | 8 bit | 8,33 MHz | Bus storico, lento |
| **EISA** | 16 bit | 8,33 MHz | Migliorato ma ancora lento |
| **PCI** | 32 bit | 33 MHz | Bus standard per anni |
| **PCI-X** | 32–64 bit | 66 MHz | Fino a 1 GB/s |
| **AGP** | dedicato alla scheda video |  |  |
| **PCI Express (PCIe)** | bus moderno e veloce | sostituisce AGP e PCI |  |

Il numero di linee del bus **non sempre coincide** con la dimensione dell’architettura (32 o 64 bit), ma spesso è simile.

| Architettura | Address Bus | Memoria indirizzabile | Data Bus | Dati per trasferimento |
| --- | --- | --- | --- | --- |
| **32 bit** | 32 linee | $2^{32} = 4 GB$ | 32 linee | 4 byte |
| **64 bit** | 64 linee | $2^{64} \approx 16 \  exabyte$ | 64 linee | 8 byte |

Non sempre serve avere tutte le linee teoriche.
Per esempio, un processore **a 64 bit** può avere **solo 48 linee di indirizzi**, sufficienti per gestire 256 TB di memoria fisica.
Le scelte su quanti fili usare dipendono da:

- **efficienza**,
- **costi**,
- e **requisiti del sistema**.
# I/O

La sezione **Input/Output (I/O)** di un computer serve per:
- **acquisire** dati e programmi dall’esterno (input);
- **rappresentare** i risultati delle elaborazioni (output).
Le forme di rappresentazione sono molteplici: sullo schermo, tramite la stampante, o come dati memorizzati su dispositivi di massa (hard disk, DVD, pendrive, ecc.).
### REGISTRI DI I/O
Dal punto di vista concettuale, la sezione di I/O si può immaginare come una **memoria con celle**, ma con uno **spazio di indirizzamento separato e più piccolo** rispetto alla memoria principale.
Ogni dispositivo di I/O (come tastiera, monitor o stampante) possiede:

- un proprio **intervallo di indirizzi** riservato, chiamato **registri di I/O** o **porte di I/O**;
- questi indirizzi servono al processore per comunicare con quella specifica periferica.
---
### MEMORY-MAPPED I/O
Alcuni dispositivi richiedono un grande spazio di I/O e utilizzano **indirizzi di memoria normali** invece degli indirizzi di I/O.
In questo caso si parla di **dispositivi mappati in memoria (Memory-Mapped I/O)**.
Questa tecnica permette di trattare la periferica come se fosse una parte della memoria principale, semplificando le operazioni di lettura e scrittura.

---
Per gestire in modo efficiente la comunicazione tra CPU e periferiche, esistono **linee di sincronizzazione dedicate**, chiamate **linee di interruzione** o **interrupt**.

Sul **Control Bus (CBus)** sono presenti due segnali principali:

- **INTR**: richiesta di interruzione da parte di una periferica;
- **INTA**: risposta del processore che accetta e gestisce l’interruzione.

Quando arriva un interrupt, il processore sospende temporaneamente ciò che sta facendo per eseguire una **procedura specifica** chiamata **ISR (Interrupt Service Routine)**.
Questo meccanismo è essenziale per i dispositivi che funzionano in modo **asincrono**, cioè che possono richiedere attenzione in qualsiasi momento (come il mouse o la tastiera).

I processi infatti possono essere Sincroni e Asincroni:
- Sincroni -> i processi vengono messi in coda con un ordine
- Asincroni -> i processi non hanno un ordine ma possono arrivare in qualsiasi momento (tipo lo spostamento del mouse).
---
Il **DMA (Direct Memory Access)** è fondamentale perché libera la CPU dal compito di spostare i dati. Esistono tre strategie di utilizzo del bus da parte del DMA:
1. **Burst Mode:** Il DMA prende il controllo totale del bus e trasferisce tutto il blocco di dati. La CPU rimane ferma finché il DMA non finisce.
2. **Cycle Stealing:** Il DMA "ruba" un ciclo di bus ogni tanto alla CPU. La CPU rallenta leggermente ma non si ferma mai del tutto.
3. **Transparent Mode:** Il DMA usa il bus solo quando la CPU sta facendo operazioni interne (es. EXECUTE) e non ha bisogno del bus. È la più efficiente ma la più complessa da realizzare.
---
Ogni periferica dispone di una circuiteria chiamata **scheda controller**, che ha il compito di:
- collegarsi al bus di sistema;
- gestire i propri indirizzi di I/O;
- sincronizzare i trasferimenti tramite il Control Bus;
- gestire eventuali linee di interrupt o DMA.
Le periferiche interne (come scheda video, rete, tastiera) hanno la scheda controller **integrata nel Chipset** della scheda madre.
Esistono anche **controller dedicati** per gestire in modo centralizzato le interruzioni e il DMA: l’**Interrupt Controller** e il **DMA Controller**.

---
Con l’introduzione del **bus PCI**, che collega CPU, memoria e I/O attraverso il **SouthBridge**, si è semplificata la gestione degli indirizzi e dei canali DMA.
Prima del PCI, le schede controller dovevano essere **configurate manualmente** (tramite ponticelli o interruttori) per assegnare indirizzi, linee di interrupt e canali DMA, evitando conflitti con altre schede.
Il PCI ha introdotto la tecnologia **Plug & Play**, grazie alla quale:
- il BIOS, il sistema operativo e il firmware della scheda controller stabiliscono automaticamente gli indirizzi e le linee di comunicazione;
- l’utente non deve più configurare manualmente i dispositivi;
- è possibile collegare dispositivi “a caldo” (senza spegnere il computer).
---
Le **periferiche esterne** si collegano al bus del sistema tramite **connettori standard**.
Esempi:
- **Slot PCI o PCIe**: per collegare schede aggiuntive (come una seconda scheda di rete o una scheda audio dedicata);
- **Connessioni IDE/EIDE (ATA-ATA2)**: usate in passato per hard disk e DVD, oggi quasi del tutto sostituite da interfacce più moderne.
---
Gli standard moderni per il collegamento dei dispositivi di I/O sono:
- **USB (Universal Serial Bus)**: consente il collegamento e l’installazione “a caldo” (Hot Swap), supporta alte velocità (480 Mbit/s per USB 2.0) e fornisce alimentazione ai dispositivi;
- **FireWire (IEEE 1394)**: simile all’USB, con velocità di 400 Mbit/s e possibilità di connessioni multiple in cascata;
- **Ethernet (802.x)**: standard per la rete locale.
Gli standard più vecchi come **RS232**, **porte parallele Centronics** e **PS/2** sono stati progressivamente abbandonati o convertiti in connessioni USB.
---
La sezione di **Input/Output** è fondamentale perché consente al calcolatore di interagire con il mondo esterno.
Nel tempo, le tecniche e i bus di comunicazione si sono evoluti per:
- aumentare la velocità dei trasferimenti;
- ridurre il carico sul processore;
- semplificare la configurazione delle periferiche;
- rendere più pratico l’uso dei dispositivi grazie a standard universali come USB e PCI Express.
# PROCESSORE
Un **processore (CPU – Central Processing Unit)** è un **circuito integrato** in grado di eseguire operazioni logiche, aritmetiche e di controllo sui dati.
È composto da varie **unità funzionali**, ciascuna con un ruolo specifico.
### COMPONENTI PRINCIPALI
- **Registri:** piccole memorie interne alla CPU, molto veloci, che contengono temporaneamente dati e indirizzi.
Servono per trasferire i dati all’interno del processore, in particolare verso l’**ALU** (Arithmetic Logic Unit) per l’elaborazione.
- **ALU (Arithmetic Logic Unit):** esegue operazioni **aritmetiche** (addizione, sottrazione, moltiplicazione, divisione) e **logiche** (AND, OR, NOT, XOR).
- **Unità di controllo (Control Unit):** gestisce il flusso delle istruzioni, decodifica gli **opcode**, coordina le operazioni tra registri, ALU e memoria.
- **Program Counter (PC):** registro speciale che contiene l’indirizzo dell’**istruzione successiva** da eseguire. Dopo ogni istruzione, viene **incrementato automaticamente** della lunghezza dell’istruzione appena completata.
---
### DATA PATH
Il **data path** rappresenta il percorso che i dati compiono all’interno del processore:
$\text{Registri} \rightarrow \text{Registri di input} \rightarrow \text{ALU} \rightarrow \text{Registro di output}\rightarrow registri$

Questo ciclo consente il trasferimento e l’elaborazione continua delle informazioni.

---
## CICLO DI ISTRUZIONE DEL PROCESSORE
Il processore opera secondo una **sequenza ciclica di fasi**, nota come **FETCH – DECODE – EXECUTE – STORE**:

1. **FETCH (Prelievo):**
L’unità di controllo pone sul **bus degli indirizzi (Address Bus)** il valore contenuto nel **Program Counter**, per leggere dalla memoria l’istruzione da eseguire.
L’**op.code (Operation Code)** dell’istruzione viene caricato nel registro istruzioni (Instruction Register).
2. **DECODE (Decodifica):**
L’unità di controllo **interpreta l’Op.code**, determinando **quali operandi servono** e **quale operazione** eseguire.
In questa fase vengono caricati gli **operandi** dai registri o dalla memoria (**Operand Fetch**).
3. **EXECUTE (Esecuzione):**
L’ALU o un’unità funzionale specializzata **esegue l’operazione richiesta** sull’input.
La velocità di questa fase dipende dal **clock della CPU**, che regola la frequenza di esecuzione dei microprogrammi.
4. **STORE (Memorizzazione):**
I risultati dell’operazione vengono **memorizzati** nei registri o **scritti in memoria** (tramite il **bus dei dati**) oppure inviati ai dispositivi di I/O.
---
## TIPOLOGIE DI ARCHITETTURA
Ogni istruzione viene decodificata tramite un Operation Code che viene seguito dagli operandi.
### CISC (Complex Instruction Set Computer)
- Ogni istruzione può eseguire **operazioni complesse** (ad esempio accesso in memoria + calcolo + memorizzazione).
- Le istruzioni sono **numerose e variabili in lunghezza**, quindi la fase di **decodifica è complessa**.
- Niente Pipeline, solo prefetch
- Richiede un **data path a più cicli** per completare l’esecuzione di un’istruzione.
- È più **compatibile e portabile** a livello software: lo stesso codice Assembly può essere usato su CPU successive.
- Esempi: **Intel x86, AMD64**.
### RISC (Reduced Instruction Set Computer)
- Utilizza un **insieme ridotto e uniforme di istruzioni**, generalmente di **lunghezza fissa (es. 32 bit)**.
- Ogni istruzione viene **eseguita in un solo ciclo di clock**, con un **data path a singolo passo**.
- L’esecuzione è più **rapida e prevedibile**.
- Per eseguire un’operazione complessa serve una **sequenza di più istruzioni semplici**.
- Esempi: **ARM, MIPS, RISC-V, SPARC**.
**Differenze principali:**

| Caratteristica | CISC | RISC |
| --- | --- | --- |
| Numero di istruzioni | Alto | Basso |
| Lunghezza istruzione | Variabile | Fissa |
| Fasi per istruzione | Più cicli | Un solo ciclo |
| Decodifica | Complessa | Semplice |
| Velocità media | Inferiore | Maggiore |
| Esempi | x86, 68000 | ARM, RISC-V |

### CRISC
La tendenza attuale nell’industria dei microprocessori è l’implementazione di architetture ibride **CRISC, che combinano i punti di forza di entrambi.**
- LIVELLO ESTERNO CISC: Mantiene la compatibilità con ISA complesse come x86.
- LIVELLO INTERNO RISC: Le istruzioni CISC vengono tradotte in micro-operazioni RISC.
- Le istruzioni semplici e comuni vengono eseguite direttamente in modalità RISC.
### GESTIONE INTERRUZIONI
Il ciclo del processore termina consultando il segnale **INTR per verificare se il controller della periferica ha richiesto un’interruzione.**
Un’interruzione rappresenta la sospensione dell’esecuzione del programma per servire il codice associato all’interruzione.
## BOTTLENECK
### SISD/CISC

- LIMITE SISD
Il principio Single Istruction, Single data implica che una singola istruzione operi su un singolo dato nell’unità di tempo.
questo approccio rappresenta un limite fondamentale per le esigenze computazionali odierne.
Molte applicazioni, dal rendering grafico all’IA richiedono di elaborare grosse quantità di dati simultaneamente, e con questo approccio sprecheremo potenza computazionale.
- LIMITE CISC
Il “Memory Wall” accade perché l’accesso alla memoria rallenta molto l’esecuzione, dato che si deve passare dal BUS.
Quindi, avendo già una fase di Decode particolarmente pesante, questo ritardo di accesso grava ancora sull’efficienza.
### **Sistema di Cache**
Per evitare il *bottleneck* dovuto alla lentezza della memoria principale rispetto alla CPU, si utilizza un sistema di **cache**.
Quando la CPU legge un indirizzo dalla memoria, gli indirizzi successivi vengono memorizzati nella cache.
Questo avviene tramite un **bus dedicato**, molto più veloce rispetto al bus della memoria principale (più lunga è la linea del bus, minore è la velocità di trasmissione).
Il funzionamento può essere riassunto così:
1. La CPU cerca il dato **prima nella cache**.
2. Se il dato **non è presente** (*cache miss*), viene letto dalla memoria principale.
3. Il dato viene quindi **copiato nella cache**, eventualmente **rimpiazzando** la linea meno utilizzata (*Least Recently Used – LRU*).
### Livelli di cache:
- **Cache L1** → all’interno della CPU (la più veloce, ma più piccola)
- **Cache L2** → collegata alla CPU (più grande, ma leggermente più lenta)
- **Cache L3** → condivisa, collegata alla scheda madre (ancora più grande, ma meno veloce)
---
### **Prefetch**
Fin dalle prime CPU, si è introdotto il **prefetch**:
la CPU preleva e memorizza in anticipo alcuni byte (ad esempio 6 o 8) successivi a quelli richiesti, in modo da **anticipare l’uso futuro dei dati** e **ridurre l’accesso al bus**.
Questo meccanismo aumenta la probabilità che le istruzioni necessarie siano già disponibili nella cache.

---
### **Superscalar Architecture**
Un processore con **più ALU (Arithmetic Logic Unit)** può gestire più pipeline contemporaneamente:
→ questo tipo di architettura si chiama **superscalare**.

---
### **Architetture CISC e ibridi moderni**
I processori **Intel i7** e **i9** appartengono alla famiglia **CISC (Complex Instruction Set Computer)**,
ma internamente sono **ibridi**, poiché utilizzano una microarchitettura **RISC-like** per ottimizzare l’esecuzione delle istruzioni complesse.
# LIVELLO SOFTWARE
### Livelli di Linguaggio
- I programmi sono scritti in **Linguaggio ad Alto Livello** (es. C, C++, ecc.), che è il più espressivo.
- Questo codice viene tradotto in **Linguaggio macchina assemblativo (Assembly)**.
- Il linguaggio assemblativo viene infine tradotto in **Linguaggio macchina binario**.
### Strumenti di Traduzione

| **Strumento** | **Trasformazione** | **Note** |
| --- | --- | --- |
| **Compilatore** | Codice ad Alto Livello → Codice Assemblativo  | Automatizza molti compiti del programmatore assembly. Un compilatore che riorganizza le istruzioni è detto **Ottimizzante**. |
| **Assemblatore** | Codice Assemblativo → Codice Macchina Binario (File Oggetto) | Esegue passi come la generazione della codifica binaria e la gestione delle direttive di allocazione di memoria. |

## Generazione del Programma Oggetto
La generazione di un file eseguibile completo (Programma Oggetto) richiede la collaborazione di più strumenti.
### Flusso di Lavoro
**Compilatore**: Trasforma i file sorgenti ad alto livello in file sorgenti assembly.
**Assemblatore**: Trasforma i file sorgenti assembly in **File Oggetto**.
**Linker (Collegatore)**: Collega assieme vari file oggetto e file di libreria in un unico **Programma Oggetto**.
> **Il Ruolo del Linker e delle Librerie**
- Quando un file sorgente chiama sottoprogrammi dichiarati altrove, l'assemblatore genera un file oggetto incompleto (con riferimenti a nomi esterni).
- Il Linker risolve questi riferimenti combinando più file oggetto separati.
- Le Librerie sono file che raggruppano file oggetto riutilizzabili e contengono le informazioni necessarie al Linker per risolvere i riferimenti a nomi esterni. Sono create dall'utility Archiver.
### Assemblatore a Due Passate
Si usa un metodo a 2 passate per gestire i simboli (es. etichette dei salti in avanti) che vengono usati prima di essere dichiarati.
**Passo 1**: Scorre il codice sorgente e raccoglie tutti i simboli e i rispettivi valori numerici nella **tabella dei simboli.**
**Passo 2**: Scorre nuovamente il codice sorgente, sostituisce i simboli con i valori in tabella e genera il codice oggetto finale.
## Esecuzione e Debug del Programma
### Loader (Caricatore)
Il Loader è il programma che carica il programma oggetto dalla memoria secondaria (disco) alla **memoria centrale** per l'esecuzione.
- Legge informazioni (lunghezza e locazione di caricamento) dall'header del file oggetto.
- Carica il programma in memoria.
- Salta alla prima istruzione del programma da eseguire.
### Debugger
Il Debugger è un programma che consente di eseguire e interrompere il programma oggetto per controllare lo stato della memoria e dei registri e individuare errori di programmazione (bug).

| **Modalità** | **Descrizione** | **Meccanismo** |
| --- | --- | --- |
| **Trace Mode** | Il programma viene eseguito **passo-passo**, interrompendosi dopo ogni istruzione. | Si genera un'eccezione al termine di ogni istruzione; il Debugger è la routine di servizio dell'interruzione. |
| **Breakpoint** | L'esecuzione si interrompe in punti di osservazione specifici definiti dal programmatore. | Il Debugger sostituisce temporaneamente le istruzioni nei punti di osservazione con speciali interruzioni software (**Trap**). |

## Il Sistema Operativo (SO)
Il **Sistema Operativo** gestisce il coordinamento generale di tutte le attività del calcolatore.
**Funzioni**: Esecuzione concorrente di programmi, gestione degli I/O, gestione dell'accesso alla memoria, gestione dell'interfaccia utente, etc.
**Struttura**: Formato da un insieme di routine essenziali che risiedono nella memoria centrale e programmi di utilità che risiedono su disco.
**Sistemi Multitasking**: Sistemi operativi capaci di eseguire più programmi contemporaneamente (virtualmente).
- **Gestione Concorrente (Time Slicing)**: Il SO divide l'esecuzione dei programmi in **quanti di tempo** ($\tau$). Un contatore lancia un'interruzione a intervalli regolari, attivando la routine **SCHEDULER** per scegliere il prossimo programma da eseguire.
**Stati dei Programmi**: **RUNNING**, **RUNNABLE** e **BLOCKED**.

---
# PIPELINE
La pipeline è una catena di montaggio formata da 5 stadi che permette un’esecuzione delle istruzioni più efficiente.
Gli stadi della pipeline sono:
1. FETCH (Prelievo)
2. DECODE (DECODIFICA)
3. EXECUTION (ESECUZIONE)
4. MEMORY (MEMORIA)
5. STORE (SCRITTURA)
> LA PIPELINE VIENE APPLICATA AI PROCESSORI RISC E CRISC MA NON CISC

![instruction_execution_in_5_stage_pipeline.webp](instruction_execution_in_5_stage_pipeline.webp)
- Nel caso migliore si hanno 5 istruzioni eseguite in parallelo
---
Per gestire l’esecuzione in pipeline di più istruzioni si ha bisogno di mantenere informazioni tra uno stadio e l’altro.
Queste informazioni vengono mantenute nei buffer interstadi:
- I rispettivi registri interstadio (RA, RB, PC_TEMP, …)
- Il registro IR
- Segnali di controllo per i vari stadi
---
## PROBLEMI DEL PIPELINING
Non è sempre possibile avere una situazione ideale in cui si eseguono 5 istruzioni in parallelo.
I possibili tipi di conflitto sono:
- Data Hazard
- Ritardi nell’accesso alla memoria
- Control Hazard
- Limiti di Risorse
### DATA HAZARD
Una dipendenza di dato avviene quando un istruzione contiene un registro sorgente che non è stato ancora aggiornato dalle istruzioni precedenti.
Ci sono tre tipi di Data Hazard: 
1. RAW (READ AFTER WRITE) = Un istruzione utilizza un registro che ancora dev’essere modificato dall’istruzione precedente.
2. WAR (WRITE AFTER READ) = Istruzione 1 deve leggere R1 ma Istruzione 2 sovrascrive R1 prima di $I_1$, facendogli leggere il valore sbagliato.
3. WAW (WRITE AFTER WRITE) = Istruzione 1 scrive su R1 dopo che Istruzione 2 ha scritto su R1, rendendo il valore di R1 obsoleto.
---
Le istruzioni NOP sono delle istruzioni nulle che creano un ciclo di inattività chiamato Bolla.
I compilatori ottimizzanti possono inserire delle NOP se lo ritengono utile.

---
#### INOLTRO DEGLI OPERANDI
Per risolvere il problema si può ricorrere all’Operand forwarding.
Se $I_2$ ha bisogno del risultato di $R1$, ma ancora sta venendo processato dalla pipeline, si fa reindirizzare direttamente nella ALU per l’istruzione $I_2$ saltando memory e writeback.

![ms-teams_QbhE9ZSDXI.png](ms-teams_QbhE9ZSDXI.png)
### RITARDI NELLA MEMORIA
Quando si ha un cache miss si deve accedere alle memoria, avendo così un ritardo dovuto al passaggio dal bus.
In questo caso tutte le istruzioni vanno ritardate del tempo in cui si accede alla memoria.
### CONTROL HAZARD
Durante un’istruzione di salto incodizionato, l’indirizzo di destinazione viene caricato nel PC durante il passo 3 per calcolare l’indirizzo di memoria.
![ms-teams_DMqmDODEpr.png](ms-teams_DMqmDODEpr.png)
Le 2 istruzioni successive al salto verranno scartate e quindi la pipeline verrà ricaricata per intero.
Si può ridurre la penalità di salto di un ciclo di clock tramite delle modifiche:
- Aggiungere un sommatore nella fase di decode, che permette di calcolare l’offset
- Aggiungere sempre in Decode un sommatore usando come ingressi direttamente le uscite del banco dei registri
#### SALTO DIFFERITO
Nel caso del salto differito, le istruzioni antecedenti al salto non vengono scartate ma eseguite comunque, il compilatore capirà se sono valide o meno ed in caso aggiungerà delle nop.
#### PREDIZIONE DEI SALTI
Abbiamo due modalità di predizione:
- STATICA
è la modalità più semplice, si dà per probabile che un salto all’indietro verrà preso, per i salti in avanti si dà per scontato che non verrà preso.
- DINAMICA
la predizione dinamica va suddivisa in 2 modi:
==**MACCHINA 2 STATI**==
ci sono due stati: PS (PROBABILMENTE SALTA), PNS (PROBABILMENTE NON SALTA).
Per esempio, entriamo in un ciclo for che si ripete 10 volte, il bit di stato sarà PS fino all’utima iterazione dove diventa PNS.
**==MACCHINA 4 STATI==**
Ci sono quattro stati: MPS(MOLTO PROB. SALTA), PS (PROB. SALTA), PNS (PROB. NON SALTA), MPNS (MOLTO PROB: NON SALTA).
Per esempio, dentro un loop avremo il bit = MPS, all’uscita non sarà PNS o MPNS ma sarà PS cosicché non avremo un miss se rientriamo in loop.

---
Se si deve eseguire la predizione nello stadio di Fetch si ha bisogno di una memoria piccola e veloce chiamata **buffer di destinazione di salto.**
Durante il Runtime la tabella viene aggiornata per ogni salto, infatti ad ogni salto si cercherà l’indirizzo in tabella e si useranno quelle informazioni per aggiornare PC.

---
### STRUCTURAL HAZARD
La pipeline può andare in stallo quando una risorsa hardware è richiesta da più istruzioni contemporaneamente.
Esempio: abbiamo 4 istruzioni, quando $I_1$ è in stato di memory (accede alla memoria), $I_4$ sarà in fetch e accederà alla memoria.
> SOLUZIONE: Avere cache separate per istruzioni e dati
### ESECUZIONE FUORI ORDINE
L'esecuzione fuori ordine cerca di sfruttare al massimo le varie unità di elaborazione nei processori superscalari, dato che vanno ad eseguire le istruzioni in modo da eseguirle nel minor tempo possibile in disordine.
- Le istruzioni vengono eseguite in disordine ma non vengono subito messe in runtime, vengono impilate in una lista ordinata e vengono poi eseguite in runtime solo in ordine
- L'ordine delle istruzioni originale viene mantenuto in un buffer chiamato Reorder Buffer
# STRUTTURA BASE PROCESSORE
Il processore è un circuito integrato che ha il ruolo di “cervello” nel calcolatore.
È capace di eseguire le istruzioni elementari necessarie per eseguire i programmi.
COMPONENTI:
- ALU
- CIRCUITI DI CONTROLLO
- BANCO DEI REGISTRI
- PROGRAM COUNTER E INSTRUCTION REGISTER
- GENERATORE DI INDIRIZZI
- INTERFACCIA PROCESSORE-MEMORIA
### BANCO DEI REGISTRI
è un blocco di memoria particolarmente veloce che consiste in vari registri collegati da un circuito per l’accesso in scrittura e lettura.
### ALU
Esegue le operazioni aritmetiche e logiche di base (+, -, AND, OR, XOR)
![Screenshot From 2026-01-16 15-54-24.png](Screenshot_From_2026-01-16_15-54-24.png)
Ha due porte di input InA e InB che rappresentano gli operandi in ingresso.
Ha un uscita che rappresenta il risultato dell’operazione.
Si usa un Mux (Multiplexer) che sceglie se mandare in InB un valore dai registri o un valore immediato come una costante.
### GENERATORE DI INDIRIZZI
È un circuito usato per generare l’indirizzo della prossima istruzione da inserire nel PC.

![Screenshot From 2026-01-16 15-58-58.png](Screenshot_From_2026-01-16_15-58-58.png)
Il sommatore riceve il valore di PC in InA e il valore da aumentare tramite due Mux, MuxPC decide se dare il program counter basico o un Indirizzo da un registro, MuxINC decide se aumentare di 4 bit o se aumentare in base alla presenza di un salto.
PC-TEMP immagazzina il PC per inserirlo nel link register durante una chiamata a sotto-programma

---
Per eseguire un’istruzione il processore deve eseguire 3 passi:
1. Prelievo dell’istruzione dalla memoria puntata da PC: IR ← \[PC]
2. Incremento di PC di 4 Bit: PC ← \[PC] + 4
3. Esecuzione dell’istruzione
I primi due passi vengono detti fase di fetch.
il terzo passo viene detto fase di esecuzione.
### DATA PATH

![Screenshot From 2026-01-16 18-12-20.png](Screenshot_From_2026-01-16_18-12-20.png)

![Screenshot From 2026-01-16 17-28-49.png](Screenshot_From_2026-01-16_17-28-49.png)

---
Non è assicurato che i dati di cui abbiamo bisogno siano già caricati nella Cache, quindi se si ha un cache miss, l’esecuzione dovrà bloccarsi finché l’operazione di memoria non sarà eseguita.

Ad ogni operazione di memoria eseguita viene generato un segnale MFC (Memory function completed), il circuito di controllo quindi, non da il permesso di riprendere l’esecuzione finché MFC == 1.
### CONTROLLO CABLATO
Un approccio per gestire i segnali di controllo consiste nel **Controllo Cablato.**
- Esiste un contatore che tiene traccia degli stadi del data path
- Un decodificatore di Istruzioni che genera un vettore lungo m (m = numero istruzioni) mettendo a 1 solo il bit corrispondente all’istruzione letta su IR
- Il generatore dei segnali di controllo produce i segnali di controllo sulla base dell’istruzione in esecuzione, dello stadio attuale, dei segnali di condizione e di segnali esterni quali le interruzioni.

![Screenshot From 2026-01-16 18-26-59.png](Screenshot_From_2026-01-16_18-26-59.png)
Gli stadi in cui si accede alla memoria possono durare diversi cicli di clock, quindi negli stadi di accesso alla memoria si deve bloccare il contatore dei passi finché il segnale *contatore_abilita non sarà == 1.*
### ORGANIZZAZIONE CISC
Le istruzioni CISC possono occupare più di una parola di memoria, quindi non si può applicare un approccio a stadi come nei RISC.

![Screenshot From 2026-01-16 20-18-03.png](Screenshot_From_2026-01-16_20-18-03.png)
Ogni componente a differenza dell’approccio a stadi è collegato a tutti i componenti tramite un Bus.
Per evitare sovraffollamento del bus, ad ogni componente è associata una porta a 3 stati:

![Screenshot From 2026-01-16 20-22-30.png](9bf90b1c-f349-40f1-b8b4-5f1edc653def.png)
Se  $R_{in}$ vale 0, ad ogni ciclo di clock il risultato sarà riportato indietro al multiplexer fino a che varrà 1, indicando che il bus è disponibile.
### INTERCONNESSIONE A TRE BUS
Una soluzione comune è quella di usare 3 Bus per la connessione.

![Screenshot From 2026-01-16 20-36-05.png](Screenshot_From_2026-01-16_20-36-05.png)
BUS A e BUS B → per i sorgenti delle operazioni
BUS C → per i risultati
## CONTROLLO MICROPROGRAMMATO
il controllo microprogrammato è una tecnica molto più semplice del controllo cablato ma anche molto lenta.
nel controllo microprogrammato i segnali di controlli relativi ad una istruzione vengono pre-caricati nella cpu in delle “parole di controllo” che contengono i segnali di controllo relativi ad una istruzione.
- Per esempio ‘ADD’ potrebbe avere i segnali di controllo necessari 010111, quindi la parola di controllo relativa sarà 010111.
# ALGEBRA BOOLEANA
L’algebra booleana è un sistema algebrico in cui ogni variabile può assumere solo 2 valori:  $0 \ e \ 1$.
Le operazioni di base sono:
- SOMMA LOGICA (OR)
- PRODOTTO LOGICO (AND)
- COMPLEMENTAZIONE (NOT)
## SOMMA LOGICA (OR)
- La somma logica o OR è una funzione che vale 1 solo se almeno uno dei suo ingressi binari vale 1

![Screenshot From 2026-01-16 22-17-57.png](Screenshot_From_2026-01-16_22-17-57.png)

- Si denota tramite gli operatori $+ \ e \ \vee$
la forma algebrica della somma:
$f(x_1,x_2)=x_1+x_2\equiv x_1 \vee x_2$

> PROPRIETÀ

COMMUTATIVA → $x_1+ x_2 \equiv x_2 + x_1$
ASSOCIATIVA → $x_1+(x_2+ x_3)\equiv(x_1+ x_2)+ x_3$
ESTENSIONE → $f=x_1+ x_2+ \ \dots\ + x_n$
ELEMENTO NEUTRO → $0+ x=x$
## PRODOTTO LOGICO (AND)

- Il prodotto logico o AND è una funzione che vale 1 solo se entrambi gli ingressi binari valgono 1.

![Screenshot From 2026-01-16 22-21-46.png](Screenshot_From_2026-01-16_22-21-46.png)

- Si denota con gli operatori $\cdot \ e\ \wedge$
La forma algebrica è:
$f(x_1,x_2)=x_1\cdot x_2\equiv x_1 \wedge x_2$

> PROPRIETÀ

COMMUTATIVA → $x_1\cdot x_2 \equiv x_2 \cdot x_1$
ASSOCIATIVA → $x_1\cdot(x_2\cdot x_3)\equiv(x_1\cdot x_2)\cdot x_3$
ESTENSIONE → $f=x_1\cdot x_2\cdot \ \dots\ \cdot x_n$
ELEMENTO NEUTRO → $1\cdot x=x$
## COMPLEMENTAZIONE (NOT)

- La funzione NOT inverte il valore della variabile in ingresso.
![Screenshot From 2026-01-16 22-29-24.png](Screenshot_From_2026-01-16_22-29-24.png)
- Si denota tramite gli operatori $\neg \ e \ \overline{x}$
> $\overline{\overline{x}}=x$
## DIFFERENZA SIMMETRICA (XOR)
- La funzione che vale 1 se e solo se gli 1 nei suoi ingressi sono in numero dispari.
![Screenshot From 2026-01-19 12-31-16.png](Screenshot_From_2026-01-19_12-31-16.png)
- Si rappresenta con “$\oplus$”
$f=x_1\oplus x_2 = \overline{x_1}x_2+x_1\overline{x_2}$
---
**PROPRIETÀ DUALI**
$x+y\cdot z= (x+y)\cdot(x+z)$ ↔ $x\cdot(y+z)=(x\cdot y)+(x\cdot z)$
$x+x=x$ ↔ $x\cdot x=x$
$x+\overline{x}=1$ ↔ $x\cdot\overline{x}=0$
$1+x=1$ ↔ $0\cdot x=0$
### TEOREMI DI DE MORGAN
- ADDIZIONE
$$
\overline{x_1+x_2+x_3+\dots+x_n}=\overline{x_1}+\overline{x_2}+\dots+\overline{x_n}
$$
- PRODOTTO
$$
\overline{x_1\cdot x_2\cdot x_3\cdot \dots\  \cdot x_n}=\overline{x_1}\cdot\overline{x_2}\cdot\dots\ \cdot\overline{x_n}
$$
## FUNZIONI LOGICHE
- Funzione logica: funzione con una o più variabili binarie di ingresso ed una variabile binaria di uscita.
Una funzione logica può essere espressa con una tabella di verità:

![Screenshot From 2026-01-16 22-44-43.png](Screenshot_From_2026-01-16_22-44-43.png)
Esiste una sola tabella di verità per funzione logica.
Una tabella di verità ha $2^n$ righe e $n+1$ colonne, dove $n$ è il numero di variabili di ingresso.

---
Due espressioni logiche sono equivalenti se rappresentano la stessa funzione.
Per dimostrare l’equivalenza di due espressioni logiche si possono confrontare le tabelle di verità.

![Screenshot From 2026-01-16 22-48-43.png](Screenshot_From_2026-01-16_22-48-43.png)

---
Per decidere quale operazione eseguire prima in un’espressione bisogna seguire gli ordini di precedenza degli operatori:
1. NEGAZIONE (NOT)
2. PRODOTTO (AND)
3. SOMMA (OR)
Se si deve forzare la precedenza di uno sull’altro si usano le parentesi.
### MINTERMINI (SOP)
Mintermine → funzione a n variabili che vale 1 solo per una specifica configurazione delle variabili
Possiamo costruire quindi l’espressione di una tabella di verità facendo la somma logica dei mintermini.

![Screenshot From 2026-01-16 22-59-23.png](Screenshot_From_2026-01-16_22-59-23.png)
che in questo caso sarà 
$$
f_1=(\overline{x_1x_2x_3})+(\overline{x_1x_2}x_3)+(\overline{x_1}x_2x_3)+(x_1x_2x_3)
$$
è unica e chiamata **PRIMA FORMA CANONICA**
### MAXTERMINI (POS)
Maxtermine → funzione a n variabili che vale 0 solo per una specifica configurazione delle variabili
Possiamo costruire quindi l’espressione di una tabella di verità facendo il prodotto logico dei maxtermini.x
Usando la tabella di prima:

$$
f_1=(x_1+\overline{x_2}+x_3)(\overline{x_1}+x_2+x_3)(\overline{x_1}+x_2+\overline{x_3})(\overline{x_1+x_2}+x_3)
$$
è una forma unica ed è detta SECONDA FORMA CANONICA
### FORMA MINIMA
Un espressione si dice in forma minima qunado non esiste nessun altra espressione equivalente con un costo inferiore.
- Per espressioni SOP e POS usiamo il criterio di costo dei LETTERALI: il costo di un espressione è dato dal numero di comparse di variabili.
$$
(x_1+x_2)(x_1+\overline{x_2})(\overline{x_1}+x_2) \to COSTO \ 6\\x_1x_2\to COSTO\ 2
$$
---
**TRASFORMAZIONE SOP → FORMA MINIMA**
- PROPRIETÀ DISTRIBUTIVA → associare le coppie di mintermini che posseggono una sola variabile in forma discordante

$$
\overline{x_1x_2x_3}+\overline{x_1x_2}x_3=\overline{x_1x_2}(x_3+\overline{x_3})
    $$  
- LEGGE DI COMPLEMENTO → Somma di variabili complementari diventa 1

$$
\overline{x_1x_2}(x_3+\overline{x_3})=\overline{x_1x_2}\cdot 1
$$

- IDEMPOTENZA (se possibile, in questo caso no)

$$
\overline{x_1\cdot x_1}=
\overline{x}
$$

## METODO DI KARNAUGH
Per trasformare un espressione in forma minima, si possono usare le mappe di karnaugh.
![Screenshot From 2026-01-17 01-38-47.png](Screenshot_From_2026-01-17_01-38-47.png)
in questo caso i gruppi sono A(000,001) e B(011,111).
- A → $x_3$ non contribuisce → $\overline{x_1x_2}$
- B → $x_1$ non contribuisce → $x_2x_3$ (x2 vale 1 e x3 vale 1 quindi nessuna forma negata)
forma minima → $\overline{x_1x_2}+x_2x_3$
### CONDIZIONE DI INDIFFERENZA
Quando abbiamo una X nella k-map si può scegliere arbitrariamente il valore, dato che sono “don’t care conditions”.

![ms-teams_InX60KFu4o.png](ms-teams_InX60KFu4o.png)
## CIRCUITI LOGICI
- Le operazioni logiche (AND, OR, NOT, XOR) possono essere realizzate da semplici circuiti elettronici.
- Questi circuiti base vengono chiamati **Porte**.

![ms-teams_kbSzuZFOY7.png](ms-teams_kbSzuZFOY7.png)
Collegando entrate e uscite delle porte si creano le reti combinatorie.
Una rete combinatoria ha n ingressi binari e m uscite binarie, con $n, m \geq 1$.

---
> PORTA A PIU' INGRESSI

Grazie alla proprietà associativa, AND e OR possono essere estese a più di 2 ingressi.
![ms-teams_0xEQ1buPG9.png](ms-teams_0xEQ1buPG9.png)
### RETI COMBINATORIE
è possibile rappresentare un’espressione logica come rete combinatoria con:
- Una porta per ogni operatore logico
- collegando le porte tra loro ad albero seguendo i livelli di priorità nell’espressione
> Le espressioni SOP e POS corrispondono a reti a due livelli

![ms-teams_GPgYcxG1px.png](ms-teams_GPgYcxG1px.png)
> GODONO DELLE PROPRIETA’ COMMUTATIVA MA NON ASSOCIATIVA

![ms-teams_ckeuRDfE5E.png](ms-teams_ckeuRDfE5E.png)
# CIRCUITI ARITMETICI
### ADDIZIONATORE AD 1 BIT
Per sommare numeri binari ad 1 bit:

![ms-teams_TL61DRFFj8.png](ms-teams_TL61DRFFj8.png)
Il riporto in uscita dell’operazione viene assegnato come riporto in entrata.
Un Addizionatore tra due bit può essere espresso da due funzioni logiche a tre ingressi.
$s_i=x_i\oplus y_i \oplus c_i$ 
$c_{i+1}=x_ic_i+y_ic_i+x_iy_i$
###### ESEMPI DI ADDIZIONATORI
>FATTIBILI TRAMITE IL SISTEMA FULL ADDER
>$11001 + 11 = 11100$ $(25 + 3 = 28)$
>$00110101 + 11010 = 01001111$ 
### ADDIZIONATORE COMPLETO (FULL ADDER)
- Unendo assieme in un singolo circuito le reti logiche per le funzioni di somma e riporto in uscita, si ottiene l’addizionatore completo.
- L’addizionatore completo prende in ingresso i due bit da sommare e il riporto in entrata e rende in uscita somma e riporto in uscita.

![Screenshot From 2026-01-19 12-39-14.png](Screenshot_From_2026-01-19_12-39-14.png)

### ADDIZIONATORE A PROPAGAZIONE DI RIPORTO
- Collegando una catena di n addizionatori completi in modo da propagare il riporto si ottiene un circuito in grado di sommare numeri binari di n bit.
- tale circuito è chiamato addizionatore a propagazione di riporto (ripple carry adder).

![Screenshot From 2026-01-19 12-42-59.png](Screenshot_From_2026-01-19_12-42-59.png)
#### SOTTRAZIONE IN UN ADDIZIONATORE
La sottrazione negli addizionatori viene vista come una semplice somma, ma si fa il complemento a due del sottraendo.
Il circuito capisce di dover complementare il sottraendo in base al valore di $OpType_O$, se è uguale a 1 verrà complementato.
0011 + 0010 = 0101 (5) $\to$ comp. a due di 2 $\to$ 1110
0011 + 1110 = 0001
### TRABOCCO
- l’addizione di due numeri in complemento a due corrisponde alla somma di due numeri binari naturali senza contare il riporto in uscita
$trabocco =c_n\oplus c_{n-1}$
### RITARDI RIPPLE CARRY ADDER
La somma è effetuata da una rete logica molto semplice (una porta xor a 3 ingressi) che assumiamo generi 1 ritardo di porta, mentre il calcolo del riporto ha bisogno di passare sia per le 3 porte and che per la porta or, assumendo quindi 2 ritardi di porta, quindi:
>Il Riporto viene generato dopo $2^n$ ritardi di porta
>L'ultimo bit risultato viene generato dopo $2^n-1$ ritardi di porta

### ANTICIPO DEL RIPORTO
Per anticipare il riporto si usano due funzioni:
- FUNZIONE DI GENERAZIONE$$G_i=x_iy_i$$
Si attiva quando entrambi gli ingressi sono 1 $\to$ crea un riporto senza controllare che ce ne sia già uno.
- FUNZIONE DI PROPAGAZIONE$$P_i=x_i+y_i$$
Si attiva quando almeno uno degli ingressi è 1, lasciando passare o ''perire'' i riporti.

![[Gemini_Generated_Image_f0v6r1f0v6r1f0v6.png]]
### IEEE 754
- PRECISIONE SINGOLA (32 BIT)
	segno = 1 bit, esponente = 8 bit, mantissa = 23 bit.
- PRECISIONE DOPPIA (64 BIT)
	segno = 1 bit, esponente = 11 bit, mantissa = 52 bit.
# CIRCUITI INTEGRATI
Nei circuiti elettronici, per rappresentare i valori 0 e 1 della variabili binarie, normalmente si usano valori di **tensione elettrica** (voltaggio).
- Per discretizzare il valore della tensione (grandezza continua), si usa la **soglia di separazione**.
- Tutti i valori di tensione superiori alla **Tensione di soglia** rappresentano il valore 1 mentre quelli inferiori il valore 0.
- Per evitare incertezza data dal rumore del circuito, tutti i valori prossimi alla tensione di soglia non vengono presi in considerazione (**Banda vietata**)

![Screenshot From 2026-01-23 14-45-52.png](Screenshot_From_2026-01-23_14-45-52.png)
### TRANSISTORI
I transistori sono delle componenti elettroniche che possono svolgere la funzione di interruttori.
A seconda della tensione ricevuta in ingresso possono trovarsi in stato di conduzione o interdizione.
La tecnologia più usata è il transistore a metallo-ossido-semiconduttore (MOS)
> Valori tipici:
$V_{cc}= 5V$, $V_{soglia}=2.5V$
$V_{cc}=3.3V$, $V_{soglia}=1.5V$
### MOS
I transistori MOS hanno 3 collegamenti: Base (porta), Pozzo e Sorgente.
- A seconda della tensione in ingresso nella base il transistore collegherà o meno la Sorgente al Pozzo.
- Se il transistore è in stato di conduzione la tensione nel pozzo diventerà uguale alla tensione nella Sorgente.
---
Esistono due tipi di transistori MOS:
1. NMOS
- Tensione di base alta = conduzione
- Tensione di base bassa = interdizione
- Sorgente collegata alla massa
2. PMOS
- Tensione di base alta = interdizione
- Tensione di base bassa = Conduzione
- Sorgente collegata all’alimentazione
### PORTA TRI-STATE
Una porta a tre stati ha due e tre possibili uscite:
![ms-teams_0tfhGyD6ed.png](ms-teams_0tfhGyD6ed.png)
Tutto dipende da $e$ dato che se sarà = 0 l’uscita sarà sempre Z (alta impedenza), se = 1 sarà il valore del ingresso di segnale.
