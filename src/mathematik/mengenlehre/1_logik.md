# Logik
Die Mathematik ist wie eine eigene Sprache.
Wer sich mathematische Texte angeschaut hat, der wird sich vielleicht gewundert haben, was das alles für Symbole sind.
Die Symbole der Mengenlehre und auch der Logik werden dazu verwendet, um mathematische Sätze, Definitionen und Beweise kurz zu formulieren.
Doch nur Symbole an sich haben erst einmal wenig Bedeutung.
Erst durch die Regeln der Logik selbst haben die Symbole eine Bedeutung.
Die Symbole und Schreibweisen selbst nennt man *Syntax*.
Syntax regelt das gültige Zusammensetzen von Zeichen.
Die *Semantik* wiederum gibt nun den syntaktisch korrekten Formeln eine Bedeutung, also wie sie zu interpretieren sind.
Syntax und die Semantik hängen in der Logik durchaus eng zusammen, da sie nach ähnlichen Regeln definiert sind, doch sollte man diese nicht verwechseln.
In der Mathematik sind die Beweise allerdings informal und eher eine Skizze eines formalen logischen Beweises,
weshalb die strikte Trennung zwischen Syntax und Semantik nicht immer transparent erscheint.

## Aussagenlogik (PL 0)
Die *Aussagenlogik* oder auch *Prädikatenlogik 0. Stufe* (*PL0*) beschäftigt sich mit *Aussagen*.

```admonish note title="Aussagen 1"
*Aussagen* sind Sachverhalte in sprachlicher Form, die in der objektiven Realität vorliegen oder denkbar sind.
```

Diese Definition wirkt etwas sperrig.
Eine andere Definition wäre:

```admonish note title="Aussagen 2"
Eine *Aussage* ist ein sprachliches Gebilde, dem eindeutig ein
*Wahrheitswert* (*wahr* oder *falsch*) zugeordnet werden kann.
```

Diese Definition verknüpft allerdings schon ein bisschen die Syntax (sprachliches Gebilde) mit Semantik (Wahrheitswert).
Sowohl die Syntax, als auch die Semantik werden nachfolgend gesondert eingeführt.
Nur wenden wir uns dann nicht mehr dem Begriff Aussage selbst zu, sondern nutzen Variablen.

#### Beispiele
Folgendes sind Beispiele für Aussagen:
- "Berlin ist die Hauptstadt von Deutschland."
- "Kein Auto ist Minzgrün"
- $3 + 4 = 0$
- $3 - 7 > -5$

Jede dieser Aussagen ist ein sprachliches Gebilde.
Die ersten Beiden sind deutsche Sätze. 
Deutsch ist eine *natürliche Sprache*.
Die anderen Beiden nutzen eine *formale Sprache*. 
Solche Formeln und andere Schreibweisen mit Symbolen können eine formale Sprache bilden.
Formale Sprachen werden im Teil [Informatik](../../informatik/informatik.md) näher behandelt.

### Syntax
Aussagenlogische *Formeln* beinhalten verschiedene Symbole und werden rekursiv definiert:

```admonish note title="Aussagenlogische Formeln"
Sei $O = \{ \neg, \wedge, \vee, \rightarrow, \leftrightarrow, (, ) \}$ die Menge der *logischen Operatoren* (*Junktoren*)
und $\Sigma$ eine Menge von Symbolen, die *Aussagevariablen* genannt werden.
Neben den Aussagenvariablen existieren noch die "Grundaussagen-Symbole" $\{ w, f \}$.
Um Verwechslungen zu vermeiden, sollen alle drei Mengen keine gemeinsamen Elemente enthalten.

Formeln sind nun rekursiv definiert:
- $w$ und $f$ sind (atomare) Formeln
- Alle Aussagenvariablen aus $\Sigma$ sind (atomare) Formeln
- Sind $A$ und $B$ Formeln, dann sind auch $\neg A,\ (A),\ A \wedge B,\ A \vee B,\ A \rightarrow B,\ A \leftrightarrow B$ Formeln.
```

Das letzte ist der oben erwähnte rekursive Teil der Definition.
Jede gültige Zusammensetzung der Symbole nach diesen Regeln ist wieder eine Formel.
Es erscheinen also keine Junktoren, außer die Klammern, nebeneinander, sondern es liegen am Ende immer eine Aussagenvariable oder ein "Grundaussagen-Symbol" dazwischen.

Durch das Ersetzen der Aussagenvariablen durch konkrete Aussagen erhält man eine konkrete (zusammengesetzte) Aussage.
Zusammengesetzte Aussagen nennt man auch *Aussagenverbindungen*, wenn man den zusammengesetzten Charakter hervorheben möchte,
ansonsten sind es eben auch nur Aussagen oder Formeln.
Es sind auch andere Symbole in Verwendung, je nach Person oder je nach Wissenschaft oder Fachgebiet.

Die Junktoren haben einen Namen und eine Sprechweise:

```admonish note title="Name und Sprechweise der Junktoren"
$$
\begin{align*}
    w &: \text{"wahr"}\\
    f &: \text{"falsch"}\\
    \neg A &: \text{"nicht A" (Negation)}\\
    A \wedge B &: \text{"A und B" (Konjunktion)}\\
    A \vee B &: \text{"A oder B" (Disjunktion)}\\
    A \rightarrow B &: \text{"wenn A, dann B" ((materiale) Implikation)}\\
    A \leftrightarrow B &: \text{"A genau dann, wenn B" (Äquivalenz)}
\end{align*}
$$
```

Bisher war es nur Syntax, d.h. rein syntaktische Gebilde ohne Bedeutung.
Einfach eine korrekte Aneinanderreihung von Symbolen.
Auch $w$ und $f$ sind erstmal nur Symbole, die allerdings wenig überraschend mit der den Worten entsprechenden Semantik belegt werden.

### Semantik
In der Aussagenlogik gilt das *Zweiwertigkeitsprinzip*:

```admonish note title="Zweiwertigkeitsprinzip"
Alle Aussagen sind entweder *wahr* ($w$ oder $1$) oder *falsch* ($f$ oder $0$)

> Tertium non datur (dt.: Ein Drittes gibt es nicht)
> 
> — Satz vom ausgeschlossenem Dritten
```

Nehmen wir eine Formel $A \vee B$ und möchten diese untersuchen, ob sie wahr oder falsch ist, so können wir dies nicht ohne weiteres tun.
Ersetzen wir die Aussagenvariablen $A$ und $B$ durch konkrete Aussagen, so können wir immerhin diesen Aussagen einen Wahrheitswert zuordnen.
Aber nach welchen Regeln soll das $\wedge$, also das *und*, behandelt werden?

Dafür müssen wir diesen syntaktischen Symbolen nun eine Bedeutung mittels einer Wahrheitstabelle eine Semantik geben.

```admonish note title="Semantik der Junktoren"
$$
\begin{array}{c|c||c|c|c|c|c|c}
    A & B & \neg A & A \wedge B & A \vee B & A \rightarrow B & A \leftrightarrow B\\
    \hline\hline
    f & f & w & f & f & w & w\\
    f & w & w & f & w & w & f\\
    w & f & f & f & w & f & f\\
    w & w & f & w & w & w & w
\end{array}
$$
```

Um Klammern zu sparen, vereinbaren wir eine Priorität von Junktoren, ähnlich wie "Punkt vor Strich".
Die Priorität der Junktoren in absteigender Reihenfolge: $\neg, \wedge, \vee, \rightarrow, \leftrightarrow$.

Eine Zeile dieser Wahrheitstabelle nennt man auch *Interpretation* oder *Belegung*.

#### Beispiele
Wählen wir folgende Aussagen $A = "3 < 5"$ und $B = "3 + 2 = 1"$.
$A$ ist eine wahre Aussage, während $B$ eine falsche Aussage ist.
Wir bilden nun die neue Aussage $A \wedge B$. 
Ist die neue Aussage wahr oder falsch?
Dazu schauen wir in die Wahrheitstafel bei der Interpretation $w, f$ und sehen, dass $f$ gilt - also ist $A \wedge B$ eine falsche Aussage.

$\neg (3 + 5 = 0)$ ist eine wahre Aussage, denn $3+5$ ist nicht $0$, sondern $8$. 
In diesem Fall könnte man statt $\neg (3 + 5 = 0)$ auch $3 + 5 \ne 0$ schreiben.
Die logische Negation macht das $=$ also zu einem $\ne$.

Die Implikation hängt eng mit der logischen Schlussfolgerung zusammen, durch das sogenannte *Deduktionstheorem*.
Allerdings wird hierauf nicht näher eingegangen, lediglich der Begriff *folgern* wird hier nun verwendet, 
wenngleich nicht ganz korrekt, da wir damit Meta- und Objektebene vermischen.
Doch wie bereits angemerkt, nimmt man es damit nicht immer so genau, wenn man nicht gerade Logik wirklich formal betreibt.
Wenn wir uns die Wahrheitstabelle der Implikation anschauen, dann stellen wir fest, dass wir aus etwas Wahrem
nie was Falsches folgern dürfen, aber aus etwas Falschem stets was Wahres:
- $2^2 = 4 \rightarrow 1+1=1 \qquad\;$ ist falsch
- $1+1=1 \rightarrow 2+2=4 \quad$ ist wahr

#### Weitere Anmerkungen
Bei $\vee$ (gesprochen *oder*) ist anzumerken, dass es sich um ein *Inklusiv-Oder* handelt, d.h. die Gesamtaussage ist genau dann wahr,
wenn mindestens eine Teilaussage wahr ist.
Das Inklusiv-Oder ist wie ein "Milch *oder* Zucker" beim Kaffee zu verstehen - man kann auch beides nehmen.
Im Gegensatz dazu steht das *Exklusiv-Oder* (*Antivalenz* genannt, $\not\leftrightarrow$ geschrieben, 
"entweder $A$ oder $B$" gesprochen), das nur dann wahr wird, wenn genau eine der beiden Teilaussagen wahr ist. 
Die Antivalenz ist auch ein wichtiger Junktor, der hier aber nicht näher eingeführt wird.

Die Implikation bereitet vielen am Anfang Bauchschmerzen, da sie dem umgangssprachlichen "wenn ..., dann ..." auf den ersten Blick nicht vollkommen entspricht.
Hierfür findet man im Web viele weitere Erklärungen und Beispiele, die vielleicht Abhilfe schaffen können.

### Klassifikation von Formeln
```admonish note title="Modell"
Jede Belegung, unter der die Formel wahr wird nennen wir ein *Modell* der Formel.
```

#### Beispiele
$$
\begin{array}{c||c|c||c}
     & A & B & F = (A \wedge B) \rightarrow B\\
    \hline\hline
    1 & f & f & w\\
    2 & f & w & f\\
    3 & w & f & w\\
    4 & w & w & w\\
\end{array}
$$
Die Zeilen 1, 2 und 4 sind Modelle der Formel $F$.

$$
\begin{array}{c||c|c||c}
    & A & B & P = (A \rightarrow B) \leftrightarrow (\neg B \rightarrow \neg A)\\
    \hline\hline
    1 & f & f & w\\
    2 & f & w & w\\
    3 & w & f & w\\
    4 & w & w & w\\
\end{array}
$$
Jede Belegung für $P$ ist ein Modell.
Solche Formeln haben einen bestimmten Namen, der in der nächsten Definition eingeführt wird.

Wir können Formeln nun anhand ihrer Modelle in verschiedene Klassen einteilen:

```admonish note title="Klassifikation von Formeln"
Falls die Formel mindestens ein Modell hat, nennen wir sie *erfüllbar*.

Eine Formel heißt *allgemeingültig*, falls jede Belegung ein Modell ist.
Solche Formeln nennt man auch *Tautologie*.

Dagegen nennen wir sie *unerfüllbar*, wenn kein Modell existiert.
Man nennt so eine Formel auch *Kontradiktion* oder *Widerspruch*.
```

#### Beispiele
Oben haben wir bereits eine Tautologie gesehen. 
Eine weitere wäre:
$$
\begin{array}{c||c}
    A & A \vee \neg A\\
    \hline\hline
    f & w\\
    w & w\\
\end{array}
$$
Diese Tautologie beweist uns gerade den Ausspruch "*Tertium non datur*" ("*Ein Drittes gibt es nicht*", Satz vom ausgeschlossenen Dritten).
"Es gilt oder es gilt nicht" ist also eine immer wahre Aussage, da gibt es nichts dazwischen.

$$
\begin{array}{c||c}
    A & A \wedge \neg A\\
    \hline\hline
    f & f\\
    w & f\\
\end{array}
$$
Das ist eine Kontradiktion, sie ist immer falsch.
Diese Formel nennt man auch *Widerspruch*. 
Es kann $A$ *und* $\neg A$ nie gleichzeitig gelten.
Wenn also bspw. jemand behauptet "Ich wohne in Berlin", er aber gleichzeitig sagt "Ich wohne nicht in Berlin", dann widerspricht er sich ja selbst.

### Semantische Äquivalenz
Wenn wir über verschiedene Formeln reden und bestimmen wollen, ob diese Formeln das gleiche Aussagen, 
dann ist das die Frage nach der *semantischen Äquivalenz*.

```admonish note title="Semantische Äquivalenz"
Zwei Formeln $F$ und $G$ heißen *semantisch äquivalent*, wenn sie die gleichen Modelle haben.
Man schreibt $F \equiv P$.
```

#### Beispiel
$$
\begin{array}{c|c||c|c}
    A & B & A \rightarrow B & \neg B \rightarrow \neg A\\
    \hline\hline
    f & f & w & w\\
    f & w & w & w\\
    w & f & f & f\\
    w & w & w & w\\
\end{array}
$$
Die letzten beiden Spalten stimmen überein, also gilt $A \rightarrow B \equiv \neg B \rightarrow \neg A$.
Diese semantische Äquivalenz nennt man auch *Kontraposition* und ist ein wichtiges mathematisches Beweisverfahren.
In den Beispielen im Abschnitt [Klassifikation von Formeln](#klassifikation-von-formeln) wurden die zwei Formeln
schonmal mit der objektsprachlichen *syntaktischen Äquivalenz* verknüpft und die Wahrheitstabelle offenbarte uns dort eine Tautologie.
Es gibt einen wichtigen Zusammenhang zwischen der objektsprachlichen *syntaktischen Äquivalenz*
und der metasprachlichen *semantischen Äquivalenz*:

```admonish example title="Semantische und syntaktische Äquivalenz"
Zwei Formeln $F$ und $P$ heißen *semantisch äquivalent*, genau dann, wenn $F \leftrightarrow P$ eine Tautologie ist.
```

Es gibt ein paar wichtige semantische Äquivalenzen, die uns auch beim *Rechnen* oder *Umformen* von Formeln helfen.
Die tatsächliche semantische Äquivalenz lässt sich leicht durch Aufstellen einer Wertetabelle ermitteln und ist eine gute Übung.

```admonish example title="Wichtige semantische Äquivalenzen"
1. $$
\begin{align*} 
    \begin{aligned} 
        x \wedge y &\equiv y \wedge x\\
        x \vee y &\equiv y \vee x\\
        x \leftrightarrow y &\equiv y \leftrightarrow x 
    \end{aligned}
    &&\text{Kommutativität}
\end{align*}
$$
2. $$
\begin{align*}
    \begin{aligned} 
        x \wedge (y \wedge z) &\equiv (x \wedge y) \wedge z\\
        x \vee (y \vee z) &\equiv (x \vee y) \vee z\\
        x \leftrightarrow (y \leftrightarrow z)
        &\equiv (x \leftrightarrow y) \leftrightarrow z
    \end{aligned}
    &&\text{Assoziativität}
\end{align*}
$$
3. $$
\begin{align*}
    \begin{aligned}
        x \wedge (y \vee z) &\equiv (x \wedge y) \vee (x \wedge z)\\
        x \vee (y \wedge z) &\equiv (x \vee y) \wedge (x \vee z)
    \end{aligned}
    &&\text{Distributivität}
\end{align*}
$$
4. $$
\begin{align*}
    \begin{aligned}
        x \wedge (x \vee y) &\equiv x\\
        x \vee (x \wedge y) &\equiv x
    \end{aligned}
    &&\text{Absorption}
\end{align*}
$$
5. $$
\begin{align*}
    \begin{aligned}
        x \wedge x &\equiv x\\
        x \vee x &\equiv x
    \end{aligned}
    &&\text{Idempotenz}
\end{align*}
$$
6. $$
\begin{align*}
    \begin{aligned}
        \neg(\neg x) &\equiv x\\
        \neg(x \rightarrow y) &\equiv x \wedge \neg y\\
        \neg(x \leftrightarrow y)
        &\equiv \neg x \leftrightarrow y
        \equiv x \leftrightarrow \neg y
    \end{aligned}
    &&\text{Verneinung}
\end{align*}
$$
7. $$
\begin{align*}
    \begin{aligned}
        \neg(x \wedge y) &\equiv \neg x \vee \neg y\\
        \neg(x \vee y) &\equiv \neg x \wedge \neg y
     \end{aligned}
    &&\text{De Morgan'sche Regeln}
\end{align*}
$$
8. $$
\begin{align*}
    \begin{aligned}
           x \leftrightarrow y &\equiv (x \rightarrow y) \wedge (y \rightarrow x)\\
           x \rightarrow y &\equiv \neg x \vee y\\
           x \wedge y &\equiv \neg(\neg x \vee \neg y)\\
           x \vee y &\equiv \neg(\neg x \wedge \neg y)
    \end{aligned}
    &&\text{Elimination}
\end{align*}
$$
9. $$
\begin{align*}
    \begin{aligned}
        x \rightarrow y \equiv \neg y \rightarrow \neg x
    \end{aligned}
    &&\text{Kontraposition}
\end{align*}
$$
10. $$
\begin{align*}
    \begin{aligned}
       \neg f &\equiv w\\
       \neg w &\equiv f
    \end{aligned}
    &&
\end{align*}
$$
11. $$
\begin{align*}
    \begin{aligned}
       x \wedge \neg x &\equiv f\\
       x \vee \neg x &\equiv w\\
       x \leftrightarrow \neg x &\equiv f
    \end{aligned}
    &&
\end{align*}
$$
12. $$
\begin{align*}
    \begin{aligned}
       w \wedge x &\equiv x\\
       f \wedge x &\equiv f\\
       w \vee x &\equiv w\\
       f \vee x &\equiv x
    \end{aligned}
    &&
\end{align*}
$$
13. $$
\begin{align*}
    \begin{aligned}
       f \rightarrow x &\equiv w\\
       w \rightarrow x &\equiv x\\
       x \rightarrow f &\equiv \neg x\\
       x \rightarrow w &\equiv w
    \end{aligned}
    &&
\end{align*}
$$
14. $$
\begin{align*}
    \begin{aligned}
       f \leftrightarrow x &\equiv \neg x\\
       w \leftrightarrow x &\equiv x
    \end{aligned}
    &&
\end{align*}
$$
```

#### Beispiele
Im folgenden Beispiel wird eine Formel durch obige Äquivalenzen in eine äquivalente Formel umgeformt.
Die verwendete Äquivalenz wird entsprechend der Nummerierung oben angegeben, damit es besser nachvollziehbar ist, was umgeformt wurde.
$$
\begin{alignat*}{2}
    \quad && &(A \rightarrow B) \rightarrow ((B \rightarrow C) \rightarrow (A \rightarrow C))\\
    \overset{\text{8.}}{\equiv}\quad && &\neg (\neg A \vee B) \vee (\neg (\neg B \vee C) \vee (\neg A \vee C))\\
    \overset{\text{7.}}{\equiv}\quad && &(A \wedge \neg B) \vee ((B \wedge \neg C) \vee \neg A \vee C)\\
    \overset{\text{1.}}{\equiv}\quad && &(A \wedge \neg B) \vee \neg A \vee (B \wedge \neg C) \vee C\\
    \overset{\text{3.}}{\equiv}\quad && &((A \vee \neg A) \wedge (\neg B \vee \neg A)) \vee ((B \vee C) \wedge (\neg C \vee C))\\
    \overset{\text{11.}}{\equiv}\quad && &(w \wedge (\neg B \vee \neg A)) \vee ((B \vee C) \wedge w)\\
    \overset{\text{12.}}{\equiv}\quad && &\neg B \vee \neg A \vee B \vee C\\
    \overset{\text{3.}}{\equiv}\quad && &\neg B \vee B \vee \neg A \vee C\\
    \overset{\text{11.}}{\equiv}\quad && &w \vee \neg A \vee C\\
    \overset{\text{11.}}{\equiv}\quad && &w
\end{alignat*}
$$
In diesem Fall konnten wir nur durch umformen, also insbesondere ohne Wahrheitstabelle, zeigen, 
dass es sich um eine Tautologie handelt, da die ursprüngliche Formel semantisch äquivalent zu $w$ ist.
Die Ausgangsformel nennt man auch *Kettenschluss*.

Das Umformen von Gleichungen in der Schule ist übrigens ähnlich.
Vielleicht hat dein Mathelehrer mal das Wort "*Äquivalenzumformung*" dafür verwendet.
Es wird so umgeformt, dass sich der Wahrheitswert der Gleichung nicht ändert.

## Prädikatenlogik (PL 1)
Die Aussagenlogik allein reicht leider nicht aus, um viele Problemstellungen in der Mathematik vernünftig zu formulieren.

```admonish note title="Variable"
Sei $G$ ein Grundbereich von Objekten.
Für eine *Variable* $x$ über $G$ kann ein Objekt aus $G$ eingesetzt werden.
```

```admonish note title="Aussagenform"
Eine *Aussagenform* $H$ über $G$ ist ein schriftsprachliches Gebilde mit mindestens einer Variable.
Durch Einsetzen von Objekten aus $G$ **für alle** Variablen wird $H$ zu einer Aussage.
```

Man schreibt $H(x)$ oder $H(x_1, x_2, \dots, x_n)$ für eine Aussagenform $H$ mit den Variablen $x$ bzw. $x_1, x_2, \dots, x_n$.
Aussagenformen wurden bereits in der [Aussagenlogik](#syntax) oben eingeführt, ohne sie konkret zu benennen:
> Durch das Ersetzen der Aussagenvariablen durch konkrete Aussagen, erhält man eine \[$\dots$\] Aussage.
 
Das Zusammensetzen von Aussagen(-formen) mit den entsprechenden Junktoren ist analog zur Aussagenlogik.

#### Beispiele
Sei $G = \mathbb{N}$ Grundbereich und $A(n) := ``n + 1 = 3''$ Aussagenform.
Durch Ersetzen der Variable $n$ durch ein Objekt aus $G$, hier also einer natürlichen Zahl, wird $A(x)$ zu einer Aussage:
- Für $n = 1$ ist $A(1) := ``1 + 1 = 3''$ eine falsche Aussage.
- Für $n = 2$ ist $A(2) := ``2 + 1 = 3''$ eine wahre Aussage.

Sei $G$ die Menge aller Lebewesen und $Mensch(x) := ``x \text{ ist ein Mensch}''$ eine Aussagenform.
In der Prädikatenlogik nennt man solche Aussagenformen ein *Prädikat*.
$Mensch(AngelaMerkel)$, sprich "Angela Merkel ist ein Mensch", ist eine wahre Aussage,
während $Mensch(Grumpy Cat)$, sprich "Grumpy Cat ist ein Mensch" eine falsche Aussage ist.

Doch in der Prädikatenlogik gibt es noch mehr, was diese ausmacht:

```admonish note title="Quantifizierung"
Quantoren:
- Allquantor: $\forall x$ - sprich: "Für alle $x$ aus $G$"
- Existenzquantor: $\exists x$ - sprich: "Es existiert ein $x$ aus $G$"

Unter *Quantifizierung* einer Aussagenform $H(x)$ versteht man die Überführung von $H(x)$ mittels den Quantoren in die Aussagen:
- Allaussage: $\forall x (H(x))$ - sprich: "Für alle $x$ aus $G$ gilt $H(x)$"
- Existenzaussage: $\exists x (H(x))$ - sprich: "Es existiert ein $x$ aus $G$ für das $H(x)$ gilt"

Variablen, die durch einen Quantor quantifiziert sind, nennt man auch *gebunden*.
Nicht gebundene Variablen heißen *frei*.
```

Eine Aussagenform wurde erst zu einer Aussage, wenn wir die Variablen durch ein konkretes Objekt aus $G$ ersetzt haben.
Durch ein Quantor ist eine Aussagenform direkt eine Aussage:

#### Beispiele
Sei $G = \mathbb{N}$ Grundbereich und $H(x) := ``x + 1 = 3''$ Aussagenform.
Durch Quantifizierung entstehen folgende Aussagen:
- $\forall x (x + 1 = 3)$ -- "Für alle $x$ aus $G$ gilt $x + 1 = 3$" ist eine falsche Aussage.
- $\exists x (x + 1 = 3)$ -- "Es existiert ein $x$ aus $G$ mit $x + 1 = 3$" ist eine wahre Aussage.

Sei $G = \mathbb{N}$ und $H(x) := ``2x \ge x''$.
Durch Quantifizierung entstehen folgende Aussagen:
- $\forall x (2x \ge x)$ -- "Für alle $x$ aus $G$ gilt $2x \ge x$" ist eine wahre Aussage.
- $\exists x (2x \ge x)$ -- "Es existiert ein $x$ aus $G$ mit $2x \ge x$" ist eine wahre Aussage.

Man beachte hierbei, dass es bei einer Existenzaussage heißt "Es existiert **mindestens** ein $x\ \dots$".
Im Beispiel sieht man, dass mehrere $x$ die letzte Aussage erfüllen.
Möchte man dagegen deutlich machen, dass **genau** ein $x$ existiert, dann schreibt man das $\exists ! x (H(x))$.
Damit wäre $\exists ! x (2x \ge x)$ eine falsche Aussage, da jedes $x$ das oben definierte $H(x)$ erfüllt.

Sei $G = \mathbb{Z}$ und $H(x) := ``2x \ge x''$.
$\forall x (2x \ge x)$ ist nun eine falsche Aussage, da sich der Grundbereich geändert hat.
Dagegen ist $\forall x (x \in \mathbb{N} \rightarrow 2x \ge x)$ wieder wahr.
Statt dieser Schreibweise findet man häufig folgende inexakte Schreibweisen für solche Aussagen:
$$
\begin{equation*}
    \forall x \in \mathbb{N}:\ 2x \ge x
\end{equation*}
$$

Eine Aussagenform wird natürlich nur dann zu einer Aussage, wenn alle Variablen gebunden sind oder, falls freie Variablen existieren,
diese durch eine konkrete Aussage ersetzt wurden.
Folgende Beispiele sind nur Aussagenformen, da nicht alle Variablen gebunden vorkommen.  
Sei $G = \mathbb{Z}$.
- $x + y = 0$
- $\forall x:\ x + y = 0$

Dagegen sind sie quantifiziert oder ersetzt bspw. folgende Aussagen:
- $\forall x:\ x + 1 = 0$ ist falsch.
- $\forall x\ \exists y:\ x + y = 0$ ist wahr.
- $\exists y\ \forall x:\ x + y = 0$ ist falsch.

Am letzten Beispiel erkennt man, dass die Reihenfolge der Quantoren eine wichtige Rolle spielt:
Die Aussage "Für alle $x$ gibt es ein $y$ \[...\]" ist eine grundlegend andere Aussage als "Es gibt ein y für alle x \[...\]".