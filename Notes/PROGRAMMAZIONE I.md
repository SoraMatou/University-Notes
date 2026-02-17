gli esercizi ed i progetti si trovano su

[https://github.com/AskraZ/APPUNTI-UNICT-INF](https://github.com/AskraZ/APPUNTI-UNICT-INF)
Libro: [Linguaggio C](https://mega.nz/folder/qhBy0IzY#TqPKZbmW05D6HCURQkTsiA/file/zhhVwBbB)

# TIPI
#### CARATTERI
- **==char==** --> char contiene caratteri, spazi e punteggiatura (recepiti     in linguaggio numerico ma codificati da ASCII).
#### INTERI
- **==int==** --> int contiene numeri interi standard, la sua dimensione è definita dall'hardware ma è almeno 16 bit (variante ==unsigned int== permette di avere un intervallo il doppio più grande, ma solo positivo)
- ==short== --> short è uguale ad int, ma secondo lo standard sarà sempre minore o uguale per dimensione di int.
- ==long== --> long usa almeno 32 bit, garantendo un intervallo più grande di int.
- ==long long== --> long long usa almeno 64 bit, garantendo una dimensione enorme, già poco utile (==unsigned long long== arriva a poter contenere valori come: "18,446,744,073,709,551,615").
#### NUMERI DECIMALI
 - ==float== --> float  serve a rappresentare numeri in virgola mobile, richiede almeno 32 bit ma conserva fino a 6 cifre decimali.
- ==double== --> double richiede almeno 64 bit ma può arrivare fino a 15 cifre decimali.

## COSTRUTTI DI BASE

il comando while genera un ciclo che finisce quando la sua condizione (o le sue condizioni) sono soddisfatte.

```c
// programma che prende due variabili e ne aumenta una finché non sarà uguale
// all'altra variabile
int main(){
int a = 3;
int b = 0;
while (a>3){
++b;
printf("b è aumentato di uno");
}
return 0;
}
```

si possono inserire anche due condizioni dentro un ciclo while:

```c

int main(){
int a = 5;
int b = 0;
int c = 2;
while (a>b || a>c){ // a>b "O" a>c, se avessimo voluto entrambe soddisfatte "&&"
++b;
++c;
} // il ciclo uscirà dall'esecuzione quando c=5 e b=3

}
```


il ciclo for può essere definito come un ciclo definito, infatti a differenza del ciclo while sappiamo quando finirà.

```c
int main(){
int eta;
int maggiorenne = 18;

for (eta=0; eta<maggiorenne; ++eta){
printf("%s%d%s","il ragazzo ha" eta "anni");
}

}
```

con if definiamo una condizione per cui qualcosa può avvenire:

```c
int main(){
int eta = 18;
int etarichiesta = 18;

if (eta>=etarichiesta){
	printf("puoi entrare");
	}
else{

printf("non hai la giusta età per entrare");
}
}
```

```c
int main(){
int eta = 18;
int etarichiesta = 18;
int prezzoentrata = 5;
int portafoglio = 2;

if (eta>=eta richiesta){
	printf("sei maggiorenne, potresti entrare");
	if (prezzoentrata>portafoglio){
	printf("mi dispiace, non hai abbastanza soldi");
	}
	else {
	printf("puoi entrare")
	portafoglio += -5;
	}
}
else{
printf("devi crescere un po'");
}
return 0;
}
```

lo switch ti da la possibilità di configurare delle azioni in base ai “CASI”:

```c
int main(){

int input = 0;
printf("inserisci un numero da 1 a 3: ");
scanf("%d", &input);

switch (input){
case 1:
puts("hai inserito 1");
break;
case 2:
puts("hai inserito 2");
break;
case 3:
puts("hai inserito 3");
break;
}
return 0;
}
```

**non si possono usare i char nello switch**

## FUNZIONI

una funziona può essere definita all’esterno del main per migliorare la leggibilità e la riproducibilità del software:

```c
int square();
int main(){

int numero;
printf("inserisci il numero da elevare al quadrato: ")
scanf("%d", &numero);
int numeroalquadrato= square();
printf("%s%d", "il tuo numero al quadrato è: ", numeroalquadrato);
return 0;
}

int square(){

numeroalquadrato = numero * numero;
return numeroalquadrato;
}
```

le variabili definite all’interno di una funzione sono disponibili solo all’interno di essa.

# Array
un array è un gruppo di elementi immagazzinati in modo contiguo nella memoria.
![[Arrays-in-C.webp]]
per fare riferimento ad una posizione, indichiamo il nome dell’array con l’indice contenuto tra parentesi quadre:

```c
int array[]={1,2,3,4,5};

array[2]= 4; // cambiamo l'elemento di indice 2 con il valore 4
```

un array di tipo char può memorizzare una stringa di caratteri.

---
```c
#include <stdio.h>
#define SIZE 20
int main(){

int array[SIZE]; // definiamo un array di grandezza SIZE

for (size_t a = 0; a < SIZE; a++){ // ad ogni iterazione, rendiamo 0 array[a]
	array[a] = 0;
}

for (size_t a = 0; a < SIZE; a++){ // rappresentiamo l'intero array
	printf("%d ", array[a]);
}
} 
```

**size_t** si utilizza per scorrere gli array, per far iterare i cicli, dato che a differenza di **int** è universale tra le architetture (si stampano valori size_t con l'indice di conversione "%zu").

---
> l'identificatore di un array è di per sè un puntatore all'indirizzo di memoria dell'indice 0.

---
### Ricerca Lineare
```c
#include <stdio.h>
#define SIZE 10

void linearsearch(int *array, int key, int *ptrkey);

int main(){
	int a[SIZE];
	for (size_t i = 0; i < SIZE; i++) // riempiamo l'array
	{
		a[i]=2+i*(i+3);
	}
	
	for (size_t i = 0; i < SIZE; i++)
	{
		printf("%d ", a[i]);
	}
	
	printf("\nche valore devi trovare?");
	int key;
	scanf("%d", &key);
	int risultato;
	int *ptrkey = &risultato;
	linearsearch(a, key, ptrkey);
	if (*ptrkey==1)
	{
	printf("il valore %d è presente", key);
    }
    else 
    {
	 printf("il valore %d non è presente", key);
    }
} 


void linearsearch(int *array, int key, int *ptrkey)
{
int temp;
for (size_t i = 0; i < SIZE; ++i)
{
	if (array[i]==key){
		*ptrkey = 1;
		break;
}

	*ptrkey = 0;
}
	
}
```

---
#### ARRAY STATICI E AUTOMATICI
gli array statici restano fissi anche dopo la fine della funzione, mentre quelli automatici permangono solo all'interno della funzione e vengono ripristinati alla fine.

## Array bi-dimensionali

a\[i\]\[j\] → elemento di riga i e di colonna j

```c
a[2][2]={1,2}{3,4} 
```

$\begin{vmatrix}1 & 2 \\ 3 & 4\end{vmatrix}$

---
# Puntatori
i puntatori sono delle variabili.

un puntatore contiene un indirizzo di memoria.

```c
int a = 3;
&a // indirizzo memoria di a
int *ptr; // allocazione di memoria per ptr
ptr = null; //definiamo che il puntatore non punta a nulla
ptr = a;
stampa *ptr = 3;
stampa ptr = indirizzo di memoria di a;

```

### ARITMETICA DEI PUNTATORI
- PUNTATORE $\pm$ INTERO 
	se si somma un intero ad un puntatore non si ha la classica somma, ma si aggiunge l'intero in base al tipo di situazione (se è un array di interi e ptr punta a v[0] con indirizzo 2000, se aggiungiamo +1 non andremo a 2001 ma a 2004 ovvero v[1])
 - INCREMENTO O DECREMENTO
	 valgono le stesse proprietà, ptr++ porterà per esempio da v[1] a v[2]
	- ptr++
	- ++ptr
	- ptr--
	- --ptr
- SOTTRARRE I PUNTATORI
	si può sottrarre un puntatore da un altro solo se puntano allo stesso array.
	per esempio, vptr = 3000, v2ptr = 3012, v2ptr - vptr sarà uguale agli elementi presenti tra i due puntatori
# Struct



# FILE 
> qualsiasi file viene aperto come uno stream e finisce con un marcatore EOF (ctrl+d su linux)

> quando viene eseguito un programma si aprono tre stream:
> - standard input
> - standard output 
> - standard error 

> stdin -> stream di Input
> stdout -> stream di output
> stderr -> stream di errore

> fgetc -> recupera un carattere da uno stream specifico 

> fputc -> scrive un carattere su uno stream specifico 

> MODALITÀ DI APERTURA FILE 
> r -> solo lettura 
> w -> crea un file per la scrittura, se esiste ne elimina il contenuto 
> a -> apre un file per scriverne alla fine, senza eliminare il contenuto 

# STRUTTURE DATI 
