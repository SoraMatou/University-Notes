# FORMULARIO
## DETERMINANTE
ad ogni matrice quadrata A si associa un numero reale o complesso chiamato *Determinante*, denotato con $\det(A)$.
- MATRICE $2\times 2$
  $\det \begin{pmatrix}a_{1} & b_{1} \\ a_{2} & b_{2}\end{pmatrix}=a_{1}b_{2}-a_{2}b_{1}$
- MATRICE $3\times 3$
  $\det \begin{pmatrix}a_{1} & b_{1} & c_{1} \\ a_{2} & b_{2} & c_{2} \\ a_{3} & b_{3} & c_{3}\end{pmatrix}$ -> Regola di Sarrus 
![[sarrus 1.webp]]
- MATRICE DI ORDINE $\geq 4$ 
  si utilizza il teorema di laplace
## Complemento Algebrico
sia $A=(a_{ij})$ una matrice quadrata di ordine n.
il complemento algebrico di posizione (i,j) denotato con $A_{ij}$, è:
$$A_{ij}=(-1)^{i+j}\cdot \det(M_{ij})$$ dove $M_{ij}$ è la matrice ottenuto eliminando la i-esima riga e la j-esima colonna di A.

$M_{ij}=\begin{pmatrix}1 & 2 & * & 4 \\ 1 & 2 & * & 4 \\ * & * & a_{ij} & * \\ 1 & 2 & * & 4\end{pmatrix}$
## Teoremi di Laplace
### TEOREMA DI LAPLACE I
sia A una matrice $n \times n$. il determinante si ottiene moltiplicando gli elementi di una riga (o colonna) per i rispettivi complementi algebrici e sommando i prodotti:
> $\det A=a_{1}A_{1}+a_{2}A_{2}+\dots+a_{n}A_{n}$
### TEOREMA DI LAPLACE II
se $R_{i}$ e $R_{j}$ sono due righe (o colonne) distinte con $i\neq j$, allora:
$a_{i1}A_{j1}+\dots+a_{in}A_{jn}=0$ | $a_{1i}A_{1j}+\dots+a_{ni}A_{nj}$
la somma degli elementi per i rispettivi complementi algebrici sarà uguale a 0.
#### SCAMBIO RIGHE/COLONNE 
> se B si ottiene da A scambiando due righe o due colonne:
> $\det B=-\det A$

#### RIGHE UGUALI O NULLE 
> se una riga o una colonna è nulla, oppure due righe sono uguali:
> $\det A=0$

### TRASFORMAZIONI ELEMENTARI 
> $R_{i}\to R_{i}+\lambda R_{j}$ non cambia il determinante 
> $A=\begin{pmatrix}1 & 2 & -1 \\ 4 & 5 & 2 \\ 0 & -1 & 3\end{pmatrix}$ -> $R_{3}\to R_{3}+3R_{1}$
>
   $B=\begin{pmatrix}1 & 2 & -1  \\ 4 & 5 & 2 \\ 3 & 5 & 0\end{pmatrix}$ -> $\det A=\det B$

## MINORI DI UNA MATRICE 
> sia A una matrice $m\times n$.
> 1. una sottomatrice di A è ottenuta selezionando p righe e q colonne di A.
> 2. un minore di ordine $p$ è il determinante di una sottomatrice quadrata di $p$ righe e $p$ colonne
> 3. i minori di ordine 1 sono i coefficienti stessi della matrice.

## TEOREMA DI BINET
> Siano A e B due matrici quadrate dello stesso ordine.
> $\det(A\cdot B)=\det A\cdot \det B$

> il determinante del prodotto di due matrici quadrate è uguale al prodotto dei determinanti.

### MATRICE RIDOTTA PER RIGHE 
> una matrice si dice **ridotta per riga** se, per ogni riga non nulla:
> 1. esiste un elemento non nullo (pivot) sotto il quale tutti gli elementi della stessa colonna sono nulli 
> 2. l'ultima riga può essere nulla

### MATRICE RIDOTTA PER COLONNA 
> una matrice si dice ridotta per colonne, se per ogni colonna non nulla:
> 1. esiste un elemento non nullo (pivot) accanto al quale tutti gli altri elementi della colonna sono nulli.
> 2. la definizione vale per tutte le colonne fino alla penultima; l'ultima colonna può contenere zeri

#### RIDUZIONE PER RIGA 
per ridurre una matrice per righe:
- scegli un elemento non nullo della prima riga, detto pivot.
- esegui trasformazioni elementari sulle righe, in modo da non alterare il determinante né il rango, per annullare gli elementi sotto il pivot:
$$R_\text{da sostituire}\to R_\text{da sostituire}-\frac{elemento \ da\  sostituire}{pivot}R_{pivot}$$
- ripeti per ogni riga successiva.
## RANGO
sia A una matrice $m\times n$.
> PRIMA DEFINIZIONE
> il rango di A, denotato $rk(A)$, è l'ordine massimo di un minore non nullo estraibile da A. 
> tutti i minori di ordine maggiore di $rk(A)$ sono nulli.

> SECONDA DEFINIZIONE 
> il rango di A, denotato $rk(A)$, è il numero di righe (o colonne) non nulle della sua matrice ridotta per righe (o per colonne).

## TEOREMA DI KRONECKER
sia A una matrice $m\times n$ con righe $R_{1},\dots,R_{m}$ e colonne $C_{1},\dots,C_{n}$.
> il rango di A è la dimensione dello spazio generato dalle righe o dalle colonne:
> $rk(A)=dim\mathcal{L}(R_{1},\dots,R_{m})=dim\mathcal{L}(C_{1},\dots,C_{n})$

