<!--
author:   Marco Hamann

email:    marco.hamann@htw-dresden.de

version:  0.0.1

language: de

comment:  Dieser Kurs richtet sich an Studierende der Hochschule für Technik und Wirtschaft Dresden im Studiengang Fahrzeugtechnik im 2. Semester.

script:   https://cdn.rawgit.com/davidedc/Algebrite/master/dist/algebrite.bundle-for-browser.js
@Algebrite.eval: <script> Algebrite.run(`@input`)</script>
-->


# Mathematik 2 (I995)

Dieser Kurs richtet sich an Studierende der Hochschule für Technik und Wirtschaft Dresden im Studiengang Fahrzeugtechnik im 2. Semester.

Sie können diesen Kurs auf [LiaScript](https://liascript.github.io/course/?https://github.com/marco-hamann/Mathe2/blob/main/README.md) oder [Opal](https://bildungsportal.sachsen.de/opal/auth/RepositoryEntry/16640933900) aufrufen. Das Repository zu diesem Kurs finden Sie unter

https://github.com/marco-hamann/Mathe2


## Integralrechnung

Thema dieses Kapitels ist die Vertiefung der Integralrechnung für reelle Funktionen einer reellen Veränderlichen.

Schwerpunkte sind u. a. die numerische Integration sowie Anwendungen der Integralrechnung in der Berechnung von Flächen- und Volumeninhalten, von Kurvenlängen, von Massenschwerpunkten etc.

__Zentrale Fragen__ sind dabei die folgenden:

* Zusammenhang zwischen Integrierbarkeit einer Funktion und Infimum bzw. Supremum der Ober- bzw. Untersummen aller Zerlegungen des Integrationsintervalls
* Verfahren wie Trapezformel und Simpsonsche Formel zur numerischen Integration (d. i. der näherungsweisen Berechnung von bestimmten Integralen)
* Anwendung bestimmter Integrale zur Berechnung von Flächeninhalten, Volumen von Rotationskörpern, Massenschwerpunkten und Kurvenlängen


### Numerische Integration

Gegeben ist eine Funktion $f:[a,b]\to\mathbb{R}$, die nach oben und unten beschränkt ist, d. h. es gilt
$$
  m\leq f(x)\leq M
$$  
für alle $x\in[a,b]$ und Konstanten $m$ und $M$.

Hier ist $m\geq0$ vorausgesetzt, damit ist $f(x)\geq0$ für alle $x\in[a,b]$. Das bestimmte Integral ist dann als Flächeninhalt interpretierbar.
$$
  A=\int_{a}^b{f(x)}\,\mathrm{d}x
$$
Ziel ist, einen Näherungswert für den Flächeninhalt zu ermitteln.

Abschätzung des gesuchten Flächeninhaltes $A$
=============================================

1. Zerlegung $Z$ des Integrationsintervalls $[a,b]$ in Teilintervalle $[x_{k-1},x_k]$, $k\in\{1,2,\ldots,m\}$ mit $$ a=x_0<x_1<x_2<\ldots<x_{k-1}<x_k<\ldots<x_m=b $$
2. In $[x_{k-1},x_k]$ wird $f(x)$ durch einen festen Wert $f_k$ ersetzt. Dann ist $$ \sum_{k=1}^m{f_k\cdot\Delta x_k},\quad\Delta x_k=x_k-x_{k-1} $$ ein Näherungswert für den gesuchten Flächeninhalt A, worin $\Delta x_k$ die Intervallbreite bezeichnet.
3. Der Wert $f_k$ genügt wegen der Beschränktheit von $f$ der Bedingung $$ m_k=\inf_{x\in[x_{k-1},x_k]}{f(x)}\;\leq\; f_k\;\leq\; \sup_{x\in[x_{k-1},x_k]}{f(x)}=M_k $$ Die __Untersumme__ $s_Z$ und die __Obersumme__ $S_Z$ einer gegebenen Zerlegung $Z$ sind Schranken für den Flächeninhalt $A$. Es gilt: $$ s_Z=\sum_{k=1}^m{m_k\cdot\Delta_k}\;\leq\; A\;\leq\; \sum_{k=1}^m{M_k\cdot\Delta_k}=S_Z $$
4. Wird die Zerlegung $Z$ verfeinert, d. h. werden zusätzliche Stellen $x_j^\star\in[a,b]$, $j\in J$, hinzugefügt, entsteht eine verfeinerte Zerlegung $Z^\star$. Hierbei gilt: $$ s_Z\leq s_{Z^\star}\leq A \leq S_{Z^\star}\leq S_Z $$ d. h. die untere Schranke für $A$ wächst, wohingegen die obere Schranke für $A$ kleiner wird.[^1]
5. Existieren das Supremum der Untersummen und das Infimum der Obersummen aller Zerlegungen $Z$ $$ \sup_{\text{alle }Z}{s_Z}=\underline{A}\,,\quad \inf_{\text{alle }Z}{S_Z}=\overline{A} $$ so folgt $\underline{A}\leq A\leq\overline{A}$.

> Die Existenz des bestimmten Integrals $\int_a^b{f(x)}\mathrm{d}x$ kann gekoppelt werden an die Gleichheit $\underline{A}=\overline{A}$.

~~Bemerkung.~~ Aus der Stetigkeit von $f$ auf $[a,b]$ folgt die Integrierbarkeit auf diesem Intervall.

Die Verwendung von Ober- bzw. Untersummen zur Berechnung eines bestimmten Integrals ist auch erklärt in

!?[youtube](https://www.youtube.com/watch?v=2bW8Zr7oTlY)<!-- style="width: 60%"-->

die Verwendung der Obersumme zur Zerlegungszahl $n$ bzw. für den Grenzübergang $n\to\infty$ an einem Beispiel in

!?[youtube](https://www.youtube.com/watch?v=wyG4IJmmAmY)<!-- style="width: 60%"-->

!?[youtube](https://www.youtube.com/watch?v=MBsHRSxuDKM)<!-- style="width: 60%"-->

Einige numerische Berechnungsmethoden
=====================================

Rechteckregel
-------------

Das Integrationsintervall $[a,b]$ wird in $n$ Teilintervalle gleicher Länge $$ h=\frac{b-a}{n}\quad \left(n\in\mathbb{N}\,, n\geq1\right) $$ zerlegt. Für die Zerlegung $$ Z:\,a=x_0<x_1<\ldots<x_n=b\,,\quad x_k=a+k\cdot h $$ kann beispielsweise $$ A=\int_{a}^b{f(x)}\mathrm{d}x \approx \sum_{k=1}^n{y_k\cdot h}\,,\quad y_k=f(x_k) $$ gesetzt werden, d. h. das als Flächeninhalt unter dem Graph der Funktion interpretierbare bestimmte Integral wird mittels achsenparalleler __Rechteckflächen__ genähert, deren "Höhe" durch den Funktionswert an der rechten Intervallgrenze bestimmt ist.

Die vorstehende Formel liefert eine näherungsweise Berechnung des bestimmten Integrals unter Benutzung der Funktionswerte $y_k=f(x_k)$ der Zerlegung $Z$ und der Intervallbreite $h$.

~~Bemerkung.~~ Die Festlegung der Höhe der Rechtecke in der Rechteckregel durch den Funktionswert $y_k=f(x_k)$ ist willkürlich und kann durch den Funktionswert an einer beliebigen Stelle $x_k^\star\in[x_{k-1},x_k]$ ersetzt werden, beispielsweise $$ f(x_{k-1})\quad\text{bzw.}\quad f\left(\frac{1}{2}\cdot(x_k+x_{k-1})\right) $$ für den Funktionswert der linken Intervallgrenze beziehungsweise der Intervallmitte.


Trapezregel
-----------

Mit dem Ansatz der Rechteckregel wird das arithmetische Mittel der Inhalte $$ y_k\cdot h\quad\text{und}\quad y_{k-1}\cdot h $$ der Rechteckflächen mit den Funktionswerten $y_k$ an rechter und $y_{k-1}$ an linker Grenze des Intervalls $[x_{k-1},x_k]$ als Höhen gebildet. Dies entspricht dem Flächeninhalt $$ \frac{1}{2}\cdot\left(y_{k-1}+y_k\right)\cdot h $$ eines __Trapez__ über dem Intervall $[x_{k-1},x_k]$.

Das bestimmte Integral kann somit genähert werden durch $$ A=\int_a^b{f(x)}\mathbb{d}x\,\approx\,\frac{h}{2}\cdot\sum_{k=1}^n{\left(y_{k-1}+y_k\right)}=\frac{h}{2}\cdot\left(y_0+y_n+2\cdot\sum_{k=1}^{n-1}{y_k}\right) $$

Die vorstehende Formel liefert eine näherungsweise Berechnung des bestimmten Integrals unter Benutzung der Funktionswerte $y_k=f(x_k)$ der Zerlegung $Z$ und der Intervallbreite $h$.


Simpson-Regel
-------------

Zu einer besseren Näherung des bestimmten Integrals kommt man, wenn jeweils drei zur Zerlegung $Z$ gehörende, benachbarte Punkte auf dem Funktionsgraph $$ (x_k,f(x_k))\,,\quad (x_{k+1},f(x_{k+1}))\,,\quad (x_{k+2},f(x_{k+2})) $$ durch eine quadratische Funktion (Parabel) interpoliert werden. Für eine Näherung des bestimmten Integrals ist das Integrationsintervall $[a,b]$ hierfür in eine gerade Anzahl $m=2\cdot n$, $n\in\mathbb{N}\setminus\{0\}$, von Teilintervallen der Breite $$ h=\frac{b-a}{2\cdot n} $$ zu zerlegen.

Das bestimmte Integral wird hierdurch genähert mittels $$ A=\int_a^b{f(x)}\mathbb{d}x\,\approx\,\frac{h}{3}\cdot\left(y_0+y_n+4\cdot\sum_{j=1}^{n}{y_{2\cdot j-1}}+2\cdot\sum_{k=1}^{n-1}{y_{2\cdot k}}\right) $$
(Nachweis, siehe Abschnitt [Simpson-Regel](#Simpson-Regel))

Wie bei den vorstehenden Methoden liefert diese Formel eine näherungsweise Berechnung des bestimmten Integrals unter Benutzung der Funktionswerte $y_k=f(x_k)$ der Zerlegung $Z$ und der Intervallbreite $h$.


~~Bemerkung.~~ Die Näherungsformeln der Trapez- und Simpson-Regel gelten unabhängig ihrer geometrischen Interpretation für jede auf dem Intervall $[a,b]$ stetige Funktion $f$. Beide Näherungen konvergieren für $n\to\infty$ gegen den Wert des bestimmten Integrals.

---

[^1] Für zwei beliebige Zerlegungen $Z$ und $Z'$ und für die gemeinsame Verfeinerung $Z^\star$ gilt stets $$ s_Z\leq s_{Z^\star}\leq A\leq S_{Z^\star}\leq S_{Z'} $$


### Trapezregel

Die Berechnung eines Näherungswertes für das bestimmte Integral $$ \int_a^b{f(x)\,\mathrm{d}x} $$ über die Funktion $f$ mit $$ x\mapsto y=f(x)\,,\quad [a,b]\subseteq D_f\,,\quad f(x)\geq0\;\;\forall x\in[a,b] $$ mit Hilfe der Trapezformel erfolgt durch nachstehende Rechenschritte.

Rechenverfahren Trapezregel
----------------------------

1. Lege die Anzahl $n$ $(n\geq 1)$ der Teilintervalle gleicher Länge fest, in die das Integrationsintervall zerlegt werden soll. Berechne die __Länge__ eines Teilintervalls $$ h=\frac{b-a}{n} $$
2. Zerlege das Integrationsintervall $[a,b]$ in die Teilintervalle $$ [a,b]=[x_0,x_1]\cup[x_1,x_2]\cup\ldots\cup[x_{n-1},x_n] $$ worin sich die __Stützstellen__ berechnen mittels $$ x_i=a+h\cdot i\,,\quad i\in\{0,1,2,\ldots,n\} $$ Insbesondere sind $x_0=a$ und $x_n=b$.
3. Berechne die $n+1$ __Stützwerte__ $y_i=f(x_i)$, d. s. die Funktionswerte an den Stützstellen $x_i$.
4. Berechne einen Näherungswert für das bestimmte Integral mittels $$ \int_{a}^b{f(x)}\mathrm{d}x\approx \frac{h}{2}\cdot(y_0+y_1) + \frac{h}{2}\cdot(y_1+y_2) + \ldots \frac{h}{2}\cdot(y_{n-1}+y_n) $$ Es ergibt sich schließlich
> Trapezformel $$ \int_{a}^b{f(x)}\mathrm{d}x\approx\frac{h}{2}\cdot\left(y_0+y_n+2\cdot\sum_{k=1}^{n-1}{y_k}\right)$$

Eine Erklärung der Trapezregel zur näherungsweisen Berechnung des bestimmten Integrals ist erklärt in

!?[youtube](https://www.youtube.com/watch?v=6hqHufW0dD4)<!-- style="width: 60%"-->

~~Bemerkung.~~ Die vorstehende Formel ist ein Spezialfall der _Gaußschen Trapezformel_, mit der sich der Flächeninhalt $A$ eines einfachen Polygons berechnen lässt. $$ 2\cdot A=\sum_{i=1}^n{\left(y_i+y_{i+1}\right)\cdot\left(x_i-x_{i+1}\right)} $$ Die Koordinaten $x_i$ und $y_i$ mit $i\in\{1,2,\ldots,n\}$ bezeichnen darin die Koordinaten der Eckpunkte des Polygons, des Weiteren sind in der Formel $x_{n+1}=x_1$ und $y_{n+1}=y_1$ zu setzen. Siehe auch [wikipedia](https://de.wikipedia.org/wiki/Gaußsche_Trapezformel).

~~Beispiel.~~ Gegeben ist die Funktion $f:\mathbb{R}\to\mathbb{R}$ mit $$ x\mapsto y=f(x)=\exp{\left(x^2\right)} $$ sowie das Intervall $[a,b]=[0,1]$. Zu berechnen ist ein Näherungswert des bestimmten Integrals $$ \int_{0}^1{\exp{\left(x^2\right)}}\,\mathrm{d}x $$ für eine Zerlegung des Integrationsintervalls in $n=3$ Teilintervalle gleicher Länge.

1. Mit $n=3$ ergibt sich die Länge $$ h=\frac{1}{3} $$ der Teilintervalle.
2. Das Integrationsintervall wird zerlegt in $$ [0,1]=\left[0,\frac{1}{3}\right]\cup\left[\frac{1}{3},\frac{2}{3}\right]\cup\left[\frac{2}{3},1\right] $$ d. h. mit den Stützstellen $$ x_0=0\,,\quad x_1=\frac{1}{3}\,,\quad x_2=\frac{2}{3}\quad\text{und}\quad x_3=1 $$
3. Die Stützwerte berechnen sich zu $y_i=f(x_i)=\exp{\left((x_i)^2\right)}$ mit $$ y_0=1\,,\quad y_1\approx 1.1175\,,\quad y_2\approx 1.5596\quad\text{und}\quad y_3=\exp{1}\approx 2.7183 $$
4. Das bestimmte Integral besitzt den Näherungswert $$ \int_{0}^1{\exp{\left(x^2\right)}}\,\mathrm{d}x\approx \frac{h}{2}\cdot\left(y_0+y_3+2\cdot(y_1+y_2)\right)\approx 1.5121 $$

Wird hingegen eine Zerlegung von $[0,1]$ in $n=4$ Teilintervalle gleicher Länge vorgenommen, so ergibt sich mithilfe der Trapezregel ein Näherungswert $$\int_{0}^1{\exp{\left(x^2\right)}}\,\mathrm{d}x\approx 1.4907 $$

```javascript
n=4
h=1/n
f=exp(x^2)
float(h/2*(exp(0)+exp(1)+2*sum(subst(i*h,x,f),i,1,n-1)))
```
@Algebrite.eval

Halbiert man die Länge der Teilintervalle, d. h. verdoppelt man die Anzahl $n$ der Intervalle, so kann auf die vorangegangene Rechnung zurückgegriffen werden.


Verfahrensfehler Trapezregel
-----------------------------

Der mittels Trapezregel berechnete der Näherungswert $T_n(f)$ für das bestimmte Integral lässt sich darstellen $$ \int_a^b{f(x)}\,\mathrm{d}x = T_n(f)+\delta_n(f) $$ worin $\delta_n(f)$ den gemachten __Verfahrensfehler__ bezeichnet. $\delta_n(f)$ ist um so kleiner, je kleiner die Länge $h$ der Teilintervalle ist.

>Ist $f$ zweimal differenzierbar, so kann der Verfahrensfehler abgeschätzt werden mittels $$ |\delta_n(f)|\leq\frac{b-a}{12}\cdot h^2\cdot\max_{a\leq x\leq b}{|f^{\prime\prime}(x)|} $$

Hieraus lässt sich schließen, dass sich bei Halbierung der Länge der Teilintervalle die obere Schranke für $|\delta_n(f)|$ mit dem Faktor $\frac{1}{4}$ verkleinert.


### Simpson-Regel

Zunächst ist die in der Simpson-Regel verwendete Approximation zu betrachten.

>~~Satz.~~ Gelten für Punkte $(x_0,y_0)$, $(x_1,y_1)$ und $(x_2,y_2)$ die Beziehungen $$ x_0\not= x_2\quad\wedge\quad x_1=\frac{1}{2}\cdot(x_0+x_2) $$ so berechnet sich das bestimmte Integral der die Punkte interpolierenden quadratischen Funktion $$ \int_{x_0}^{x_2}{(a\cdot x^2+b\cdot x+c)}\,\mathrm{d}x=\frac{h}{3}\cdot(y_0+4\cdot y_1+y_2) $$ worin $h=x_2-x_1=x_1-x_0$ bedeutet.

~~Beweisidee.~~ Die Koeffizienten $a$, $b$ und $c$ im Integranden sind durch die Koordinaten $(x_i,y_i)$ der zu interpolierenden Punkte eindeutig festgelegt. Für den Nachweis der Gleichheit von linker und rechter Seite reicht es jedoch aus:
* das bestimmte Integral auf der linken Seite mittels Hauptsatz der Differential- und Integralrechnung zu berechnen $$ \int_{x_0}^{x_2}{(a\cdot x^2+b\cdot x+c)}\,\mathrm{d}x=\frac{a}{3}\cdot \left(x_2^3-x_0^3\right)+\frac{b}{2}\cdot \left(x_2^2-x_0^2\right)+c\cdot\left(x_2-x_0\right) $$
* in der linken Seite $y_i=a\cdot x_i^2+b\cdot x_i+c$ mit $i\in\{0,1,2\}$ zu setzen sowie $x_1=\frac{1}{2}\cdot(x_0+x_2)$ zu verwenden
um die Gleichheit nachzuweisen. Die konkrete Gestalt der Koeffizienten wird hierfür nicht benötigt. $\square$

Rechenverfahren Simpson-Regel
----------------------------

Die Berechnung eines Näherungswertes für das bestimmte Integral $$ \int_a^b{f(x)\,\mathrm{d}x} $$ über die Funktion $f$ mit $$ x\mapsto y=f(x)\,,\quad [a,b]\subseteq D_f\,,\quad f(x)\geq0\;\;\forall x\in[a,b] $$ mit Hilfe der Simpson-Regel erfolgt analog zum vorigen Abschnitt durch nachstehende Rechenschritte.

1. Lege die Anzahl $m=2\cdot n$ $(n\geq 1)$[^1] der Teilintervalle gleicher Länge fest, in die das Integrationsintervall zerlegt werden soll. Berechne die __Länge__ eines Teilintervalls $$ h=\frac{b-a}{m}=\frac{b-a}{2\cdot n} $$
2. Zerlege das Integrationsintervall $[a,b]$ in die Teilintervalle $$ [a,b]=[x_0,x_1]\cup[x_1,x_2]\cup\ldots\cup[x_{2\cdot n-1},x_{2\cdot n}] $$ worin sich die __Stützstellen__ berechnen mittels $$ x_i=a+h\cdot i\,,\quad i\in\{0,1,2,\ldots,n\} $$ Insbesondere sind $x_0=a$ und $x_n=b$.
3. Berechne die $n+1$ __Stützwerte__ $y_i=f(x_i)$, d. s. die Funktionswerte an den Stützstellen $x_i$.
4. Berechne einen Näherungswert für das bestimmte Integral mittels $$ \int_{a}^b{f(x)}\mathrm{d}x\approx \frac{h}{3}\cdot(y_0+4\cdot y_1+y_2) + \frac{h}{3}\cdot(y_2+4\cdot y_3+y_4) + \ldots \frac{h}{3}\cdot(y_{2\cdot n-2}+4\cdot y_{2\cdot n-1}+y_{2\cdot n}) $$ Es ergibt sich schließlich

> Simpsonformel $$ \int_a^b{f(x)}\mathbb{d}x\,\approx\,\frac{h}{3}\cdot\left(y_0+y_n+4\cdot\sum_{j=1}^{n}{y_{2\cdot j-1}}+2\cdot\sum_{k=1}^{n-1}{y_{2\cdot k}}\right) $$

Eine Erklärung der Simpson-Regel zur näherungsweisen Berechnung des bestimmten Integrals ist erklärt in

!?[youtube](https://www.youtube.com/watch?v=N0kFSTDvDcw)<!-- style="width: 60%"-->

~~Beispiel.~~ Weitgehend analog zum Beispiel in Abschnitt [Trapezregel](#Trapezregel) ist ein Näherungswert des bestimmten Integrals $$ \int_{0}^1{\exp{\left(x^2\right)}}\,\mathrm{d}x $$ für eine Zerlegung des Integrationsintervalls in $n=4$ (gerade Anzahl!) Teilintervalle gleicher Länge mithilfe der Simpson-Regel zu berechnen.

```javascript
n=2
m=2*n
h=1/m
f=exp(x^2)
float(h/3*(exp(0)+exp(1)+4*sum(subst((2*i-1)*h,x,f),i,1,n)+2*sum(subst((2*k)*h,x,f),k,1,n-1)))
```
@Algebrite.eval

Verfahrensfehler Simpson-Regel
------------------------------

Der mittels Simpson-Rregel berechnete der Näherungswert $S_n(f)$ für das bestimmte Integral lässt sich darstellen $$ \int_a^b{f(x)}\,\mathrm{d}x = S_n(f)+\delta_n(f) $$ worin $\delta_n(f)$ den gemachten __Verfahrensfehler__ bezeichnet. $\delta_n(f)$ ist um so kleiner, je kleiner die Länge $h$ der Teilintervalle ist.

>Ist $f$ viermal differenzierbar, so kann der Verfahrensfehler abgeschätzt werden mittels $$ |\delta_n(f)|\leq\frac{b-a}{180}\cdot h^4\cdot\max_{a\leq x\leq b}{|f^{(4)}(x)|} $$

Hieraus lässt sich schließen, dass sich bei Halbierung der Länge der Teilintervalle die obere Schranke für $|\delta_n(f)|$ mit dem Faktor $\frac{1}{16}$ verkleinert.

[^1]: Die Anzahl der Teilintervall muss hier aufgrund der Interpolation der Stützpunkte $(x_i,y_i)\in G_f$ mittels Parabeln als gerade natürliche Zahl vorausgesetzt werden.


### Anwendungen

Längen und Flächeninhalte
=========================

 Zwischen Funktionsgraph und $x$-Achse eingeschlossenen Fläche
--------------------------------------------------------------

Ziel dieses Abschnitts ist die Berechnung von Flächeninhalten , die vom Graph einer reellen Funktion $f$ einer reellen Variablen und Geraden der Form $x=a$ mit $a\in\mathbb{R}$ begrenzt werden. Die Funktionen werden über dem betrachteten Intervall stetig vorausgesetzt.

Es werden die folgenden Fälle unterschieden.

1. Es gilt $$ f(x)\geq 0\;\;\forall x\in[a,b] $$ Durch den Funktionsgraph $G_f$ und die Geraden zu den Gleichungen $x=a$, $x=b$ mit $a<b$ sowie $y=0$ wird eine Fläche begrenzt. Der Inhalt $A$ der Fläche berechnet sich durch das bestimmte Integral $$ A=\int_a^b{f(x)}\,\mathrm{d}x\geq 0 $$ vergleiche Abschnitt [Numerische Integration](#Numerische-Integration).

2. Im Unterschied wird $$ f(x)\leq 0 \;\;\forall x\in[a,b] $$ angenommen. Die durch Funktionsgraph $G_f$ und Geraden zu $x=a$, $x=b$ mit $a<b$ sowie zu $y=0$ begrenzte Fläche besitzt den Inhalt $$ A=\int_a^b{((-1)\cdot f(x))}\,\mathrm{d}x\geq 0 $$

3. Subsummierend wird $$ f(x)\geq 0 \;\;\vee\;\; f(x)\leq 0\quad\forall x\in [a,b] $$ angenommen. O. B. d. A. gelte für ein $c\in[a,b]$ mit $$\begin{array}{rcl} f(x)\geq 0 & \text{für} & x\in[a,c) \\ f(x)=0 & \text{für} & x=c \\ f(x)\leq 0 & \text{für} & x\in(c,b] \end{array} $$ so berechnet sich der Inhalt der beiderseits der $x$-Achse gelegenen, durch $G_f$ begrenzten, Fläche mittels $$ A=A_1+A_2=\int_a^c{f(x)}\,\mathrm{d}x+\int_c^b{((-1)\cdot f(x))}\,\mathrm{d}x $$ Für die Berechnung der durch $G_f$ begrenzten Fläche ist also gegebenenfalls das Integrationsintervall $[a,b]$ in Teilintervalle zu zerlegen, in denen entweder Fall 1 oder Fall 2 gilt. Hierfür ist die Berechnung der Nullstellen von $f$ hilfreich.

> Allgemeine Formel $$ A=\int_a^b{|f(x)|}\,\mathrm{d}x \quad\text{mit}\quad |f(x)|=\left\{\begin{array}{rcl} f(x) & \text{falls} & f(x)\geq 0 \\ (-1)\cdot f(x) & \text{falls} & f(x)<0 \end{array}\right. $$ für $x\in[a,b]$.

~~Beispiel.~~ Gegeben ist die Funktion $f:\mathbb{R}\to\mathbb{R}$ mit $$ f(x)=(x-1)^2-1 $$ Gesucht ist der durch $G_f$ im Intervall $[-1,3]$ mit der $x$-Achse begrenzte Flächeninhalt.

1. Berechnung der Nullstellen von $f$ im angegebenen Intervall $$ f(x)=x\cdot(x-2)=0\quad\leftrightarrow\quad x=0\;\vee\;x=2 $$
2. Zerlegung des Intervalls in Teilintervalle $$ [-1,3]=[-1,0]\cup[0,2]\cup[2,3] $$ Es gelten offensichtlich $$ f(x)\geq 0\quad\text{für}\quad x\in\left([-1,0]\cup[2,3]\right) $$ und $$ f(x)< 0\quad\text{für}\quad x\in(0,2) $$
3. Berechnung des Inhalts der durch $G_f$ und der $x$-Achse begrenzten Fläche $$ A=\int_{-1}^3{|f(x)|}\,\mathrm{d}x = \int_{-1}^0{\left((x-1)^2-1\right)}\,\mathrm{d}x + \int_{0}^2{\left(1-(x-1)^2\right)}\,\mathrm{d}x + \int_{2}^3{\left((x-1)^2-1\right)}\,\mathrm{d}x $$ Mit dem unbestimmten Integral $$ \int{\left((x-1)^2-1\right)}\,\mathrm{d}x=\frac{1}{3}\cdot(x-1)^3-x+C=\frac{1}{3}\cdot x^3-x^2+K $$ und $K=C-\frac{1}{3}\in\mathbb{R}$ ergibt sich der Flächeninhalt von $$ A=\frac{4}{3}+\frac{4}{3}+\frac{4}{3}=4 $$ Flächeneinheiten.

```javascript
f=(x-1)^2-1
roots(f=0)
factor(f)
integral(f,x)
defint(f,x,-1,0)+defint(-f,x,0,2)+defint(f,x,2,3)
defint(f,x,-1,3)
```
@Algebrite.eval

Im nachstehenden Video wird das Verfahren zur Inhaltsberechnung einer durch $G_f$ und der $x$-Achse begrenzten Fläche mit Hilfe bestimmter Integrale erklärt.

!?[youtube](https://www.youtube.com/watch?v=2zVgFO-z-nY)<!-- style="width: 60%"-->


Von zwei Funktionsgraphen begrenzte Fläche
------------------------------------------

Zur Berechnung des Inhalts $A$ einer Fläche, die in einem gegebenen Intervall $[a,b]$ durch die Graphen zweier Funktionen $f$ und $g$ begrenzt wird, sind zu unterscheiden:

1. Es wird angenommen $$ f(x)\geq g(x) \quad\forall x\in[a,b] $$ Damit bildet im Intervall $[a,b]$ der Funktionsgraph $G_f$ die obere und $G_g$ die untere Randkurve der begrenzten Fläche. Da sich der Inhalt nicht ändert, wenn alle begrenzenden Kurven um denselben Wert $a>0$ in Richtung der $y$-Achse verschoben werden, lässt sich $A$ durch eine Flächendifferenz berechnen $$ A=\int_a^b{f(x)}\,\mathrm{d}x-\int_a^b{g(x)}\,\mathrm{d}x=\int_a^b{(f(x)-g(x))}\,\mathrm{d}x $$ Vergleiche Eigenschaften des bestimmten Integrals.
2. Analog kann angenommen werden $$ f(x)\leq g(x) \quad\forall x\in[a,b] $$ Hier bildet im Intervall $[a,b]$ der Funktionsgraph $G_g$ die obere und $G_f$ die untere Randkurve der begrenzten Fläche. Der Inhalt $A$ kann berechnet werden mittels $$ A=\int_a^b{g(x)}\,\mathrm{d}x-\int_a^b{f(x)}\,\mathrm{d}x=(-1)\cdot\int_a^b{(f(x)-g(x))}\,\mathrm{d}x $$
3. Subsummierend können im Integrationsintervall $[a,b]$ obere und untere Randkurve wechseln. Für die Berechnung  des Inhaltes der begrenzten Fläche ist dieses so in Teilintervalle zu zerlegen, dass in jedem Teilintervall einer der beiden zuvor beschriebenen Fälle gilt. Hierfür ist die Berechnung der gemeinsamen Punkte von $G_f$ und $G_g$ hilfreich.[^1]

> Allgemeine Formel $$ A=\int_a^b{|f(x)-g(x)|}\,\mathrm{d}x $$ mit $$ |f(x)-g(x)|=\left\{\begin{array}{rcl} f(x)-g(x) & \text{falls} & (f(x)-g(x))\geq 0 \\ g(x)-f(x) & \text{falls} & (f(x)-g(x))<0 \end{array}\right. $$ für $x\in[a,b]$.

~~Beispiel.~~ Gegeben sind die Funktionen $f:\mathbb{R}\to\mathbb{R}$ und $g:\mathbb{R}\to\mathbb{R}$ mit $$ f(x)=x\,,\quad g(x)=(x-1)^2-1 $$ Gesucht ist der durch $G_f$ und $G_g$ im Intervall $[-1,4]$ begrenzte Flächeninhalt.

1. Berechnung der Argumente der gemeinsamen Punkte von $G_f$ und $G_g$ im angegebenen Intervall $$ f(x)=g(x)\quad\leftrightarrow\quad x\cdot(x-3)=0 \quad\leftrightarrow\quad x=0\;\vee\;x=3 $$
2. Zerlegung des Intervalls in Teilintervalle $$ [-1,4]=[-1,0]\cup[0,3]\cup[3,4] $$ Es gelten offensichtlich $$ f(x)< g(x)\quad\text{für}\quad x\in\left([-1,0)\cup(3,4]\right) $$ und $$ f(x)\geq g(x)\quad\text{für}\quad x\in[0,3] $$
3. Berechnung des Inhalts der durch $G_f$ und $G_g$ begrenzten Fläche $$ A=\int_{-1}^3{|f(x)-g(x)|}\,\mathrm{d}x = \int_{-1}^0{\left(x^2-3\cdot x\right)}\,\mathrm{d}x + \int_{0}^3{\left(3\cdot x-x^2\right)}\,\mathrm{d}x + \int_{3}^4{\left(x^2-3\cdot x\right)}\,\mathrm{d}x $$ Mit dem unbestimmten Integral $$ \int{\left(x^2-3\cdot x\right)}\,\mathrm{d}x=\frac{1}{3}\cdot x^3-3\cdot x^2+C $$ und $C\in\mathbb{R}$ ergibt sich der Flächeninhalt von $$ A=\frac{11}{6}+\frac{27}{6}+\frac{11}{6}=\frac{49}{6} $$ Flächeneinheiten.

```javascript
f=x
g=(x-1)^2-1
roots(f=g)
factor(f-g)
f-g
integral(f-g,x)
defint(g-f,x,-1,0)+defint(f-g,x,0,3)+defint(g-f,x,3,4)
defint(g-f,x,-1,4)
```
@Algebrite.eval


[^1]: Es ist ausreichend, die Argumente der gemeinsamen Punkte von $G_f$ und $G_g$ zu bestimmen.
