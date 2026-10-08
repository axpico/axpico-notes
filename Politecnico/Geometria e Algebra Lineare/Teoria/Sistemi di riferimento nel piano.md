---
tags:
  - geometria-algebra-lineare
  - geometria-analitica
  - sistemi-di-riferimento
  - spazio-euclideo
---
## Sistemi di riferimento nel piano (spazi euclidei)

> Introduzione: si passa dall'algebra lineare astratta alla **geometria analitica**, cioè al modo di descrivere con numeri (coordinate) i punti del piano e dello spazio. Argomento appena iniziato a lezione.

### Idea

Il piano euclideo $\mathcal E$ è un insieme di **punti**, che non sono numeri. Per fare calcoli serve una **corrispondenza biunivoca** (biiettiva) tra punti e coppie di numeri: un **sistema di riferimento**. Così un problema geometrico diventa un problema algebrico, e viceversa (vedi [[Politecnico/Geometria e Algebra Lineare/Teoria/Vettori geometrici liberi.md|Vettori geometrici liberi]]).

### Definizione

Un sistema di riferimento (cartesiano) del piano si assegna dando una **terna di punti non allineati** $(O,A,B)$ (cioè non appartenenti alla stessa retta):

- $O$ = **origine**;
- $\vec{u}=\overrightarrow{OA}$, $\vec v=\overrightarrow{OB}$ = **vettori di base**, linearmente indipendenti (non paralleli, perché $O,A,B$ non allineati);
- le rette $OA$ e $OB$ sono gli **assi coordinati**.

Equivalentemente: $(O,A,B)\sim(O,\vec u,\vec v)$, origine più base ordinata dei vettori liberi del piano.

> Se $\vec u\perp\vec v$ e $|\vec u|=|\vec v|=1$ il riferimento è **ortonormale** (cartesiano standard); non è però richiesto in generale: gli assi possono essere obliqui.

### Coordinate di un punto

Per ogni punto $P$ si considera il **vettore posizione** $\vec r_P=\overrightarrow{OP}$. Poiché $\{\vec u,\vec v\}$ è una base dei vettori del piano (dimensione 2), esistono **unici** $x,y\in\mathbb R$ tali che
$$\overrightarrow{OP}=x\,\vec u+y\,\vec v.$$
$(x,y)$ sono le **coordinate** di $P$ nel riferimento $(O,\vec u,\vec v)$. Geometricamente: si traccia da $P$ la parallela a $OB$ e a $OA$; le intersezioni con gli assi danno i multipli $x\vec u$ e $y\vec v$ (regola del parallelogramma).

**Perché esistenza e unicità:** due vettori non paralleli generano il piano e sono linearmente indipendenti; l'unicità della scrittura segue dall'indipendenza lineare (se $x\vec u+y\vec v=x'\vec u+y'\vec v$ allora $(x-x')\vec u+(y-y')\vec v=\vec 0$ e quindi $x=x',\ y=y'$).


**Esempio (riferimento obliquo).** $O=(0,0)$, $\vec u=(2,0)$, $\vec v=(1,1)$ e $P$ con $\overrightarrow{OP}=2\vec u+3\vec v=(7,3)$, cioè coordinate $(2,3)$ nel riferimento $(O,\vec u,\vec v)$.

```desmos-graph
left=-2; right=10; top=6; bottom=-2; width=700; height=467;
---
y=0
y=x
(2,0)|label:u
(1,1)|label:v
(4,0)|label:2u
(3,3)|label:3v
(7,3)|label:P (coord. 2,3)
y=3\{3\le x\le7\}
y=x-4\{4\le x\le7\}
```

*Parallelogramma: $P=2\vec u+3\vec v$. I due lati tracciati da $2\vec u$ e $3\vec v$ fino a $P$ sono paralleli agli assi $OA$ (asse $x$) e $OB$ (retta $y=x$).*

### Conseguenza: parallelismo

Se un vettore è un multiplo di $\vec u$ (o di $\vec v$) allora è **parallelo** a $\vec u$ (o a $\vec v$): in coordinate è del tipo $(x,0)$ (o $(0,y)$).

### Esito

La corrispondenza $P\mapsto(x,y)$ è una biiezione $\mathcal E\to\mathbb R^2$ che dipende dalla scelta di $(O,\vec u,\vec v)$: **riferimenti diversi danno coordinate diverse dello stesso punto** (si tornerà sul cambiamento di riferimento con il teorema di rappresentazione e le matrici di cambio base).

## Collegamenti

- [[Politecnico/Geometria e Algebra Lineare/Teoria/Vettori geometrici liberi.md|Vettori geometrici liberi]]
- [[Politecnico/Geometria e Algebra Lineare/Teoria/Spazi vettoriali e sottospazi.md|Spazi vettoriali e sottospazi]]
- [[Politecnico/Geometria e Algebra Lineare/Teoria/Applicazioni lineari, nucleo e immagine.md|Applicazioni lineari, nucleo e immagine]]
