---
tags: [geometria-algebra-lineare, esame, non-svolti]
---
# GAL — Prova in itinere, 11-11-2025 (docente P. Gumenyuk, 60 min per Parti A e B)

## Parte A — Test
1. Dati $a,b,c\in\mathbb R$, il sistema $\begin{cases}x+z=a\\x-y+z=b\\4x-2y+3z=c\end{cases}$ ha soluzione
 (A) $\begin{pmatrix}x\\y\\z\end{pmatrix}=\begin{pmatrix}-1&-2&1\\1&-1&0\\2&2&-1\end{pmatrix}\begin{pmatrix}a\\b\\c\end{pmatrix}$; (B) $\begin{pmatrix}x\\y\\z\end{pmatrix}=\begin{pmatrix}1&0&1\\1&-1&1\\4&-2&3\end{pmatrix}\begin{pmatrix}a\\b\\c\end{pmatrix}$; (C) $\begin{pmatrix}x\\y\\z\end{pmatrix}=\begin{pmatrix}1&1&4\\0&-1&-3\\1&1&3\end{pmatrix}\begin{pmatrix}a\\b\\c\end{pmatrix}$; (D) la soluzione non esiste per ogni $a,b,c$.
2. Date $A\in M_{\mathbb R}(2,3)$ e $B\in M_{\mathbb R}(4,3)$, quale delle seguenti matrici è definita? (A) $B^TA$; (B) $A^TB^T$; (C) $AB^T$; (D) $B^TA^T$.
3. $\mathbb R[x]_{\le2}$ polinomi $c_0+c_1x+c_2x^2$. $L:M_{\mathbb R}(2,2)\to\mathbb R[x]_{\le2}$, $L\begin{pmatrix}a&b\\c&d\end{pmatrix}=(a+d)-(b+c)x$. La matrice rappresentativa di $L$ rispetto alla base $\left\{\begin{pmatrix}1&0\\0&0\end{pmatrix},\begin{pmatrix}0&1\\0&0\end{pmatrix},\begin{pmatrix}0&0\\1&0\end{pmatrix},\begin{pmatrix}0&0\\0&1\end{pmatrix}\right\}$ di $M_{\mathbb R}(2,2)$ e alla base $\{1+x^2,\ x,\ 1-x^2\}$ di $\mathbb R[x]_{\le2}$ è
 (A) $\begin{pmatrix}1/2&0&1/2\\0&-1&0\\0&-1&0\\1/2&0&1/2\end{pmatrix}$; (B) $\begin{pmatrix}1&-1\\-1&1\end{pmatrix}$; (C) $\begin{pmatrix}1/2&0&1/2&0\\0&-1&0&-1\\1/2&0&1/2&0\end{pmatrix}$; (D) $\begin{pmatrix}1/2&0&0&1/2\\0&-1&-1&0\\1/2&0&0&1/2\end{pmatrix}$.
4. $\mathbb R[x]_{\le3}$ polinomi di grado $\le3$. Data una mappa lineare $T:M_{\mathbb R}(2,3)\to\mathbb R[x]_{\le3}$ allora sicuramente (A) $T$ non è iniettiva; (B) $T$ è iniettiva; (C) $T$ non è suriettiva; (D) $T$ è suriettiva.

## Parte B — Esercizio
$\mathbb R[t]_{\le2}$ polinomi di grado $\le2$. Sia $L:\mathbb R^3\to\mathbb R[t]_{\le2}$ definita da $L\begin{pmatrix}a\\b\\c\end{pmatrix}=(a+c)+bt+(a+c)t^2$.

a) Trovare una base dell'immagine e la dimensione del nucleo di $L$.

b) Data $F:\mathbb R^3\to\mathbb R[t]_{\le2}$, $F\begin{pmatrix}a\\b\\c\end{pmatrix}=b+(a+c)t+ct^2$, trovare una base del sottospazio $H=\left\{\begin{pmatrix}a\\b\\c\end{pmatrix}\in\mathbb R^3:L\begin{pmatrix}a\\b\\c\end{pmatrix}=F\begin{pmatrix}a\\b\\c\end{pmatrix}\right\}$.

c) Dato $K=\mathrm{span}\left\{\begin{pmatrix}2\\2\\3\end{pmatrix},\begin{pmatrix}2\\0\\1\end{pmatrix}\right\}$, determinare una base di $H\cap K$.

d) Verificare che l'insieme $\ell_1=\left\{\begin{pmatrix}a\\b\\c\end{pmatrix}\in\mathbb R^3:L\begin{pmatrix}a\\b\\c\end{pmatrix}=1+t^2\right\}$ è una retta in $\mathbb R^3$. Determinare la posizione reciproca tra $\ell_1$ e la retta $\ell_2$ di equazione parametrica $\mathbf r=\begin{pmatrix}0\\0\\2\end{pmatrix}+t\begin{pmatrix}1\\0\\0\end{pmatrix}$, $t\in\mathbb R$.
