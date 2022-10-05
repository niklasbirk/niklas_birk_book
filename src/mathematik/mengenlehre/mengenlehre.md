# Mengenlehre
## Themen
In diesem Teil möchte ich über folgende Themen sprechen:

1. [Elemente der Logik](1_logik.md)
2. [Mengenbildung und Mengenalgebra](2_mengen.md)
3. [Relationen und Abbildungen](relationen/relationen.md)
   1. [Kartesisches Produkt](relationen/1_kartesisches_produkt_relationen.md)
   2. [Abbildungen](relationen/2_abbildungen.md)
   3. [Äquivalenzrelationen](relationen/3_aequivalenzrelationen.md)
   4. [Ordnungsrelationen](relationen/4_ordnungsrelationen.md)
4. [Verallgemeinerte mengentheoretische Relationen](4_verallgemeinerte_relationen.md)
5. [Endlichkeit und Kardinalzahlen](5_endlichkeit.md)

## Über die Mengenlehre
Die Logik und die Mengenlehre sind eng miteinander verknüpft und bilden die allgemeinen Grundlagen der Mathematik.
Sie wurde von [Georg Cantor](https://de.wikipedia.org/wiki/Georg_Cantor) im 19. Jahrh. begründet.
Cantor definierte dabei, was man unter einer *Menge* versteht und untersuchte diese Strukturen dann, u.a. die *Mächtigkeit* von Mengen.
Der Begriff der *Unendlichkeit* wurde dabei von ihm in besonderem Maße geprägt.

[David Hilbert](https://de.wikipedia.org/wiki/David_Hilbert), einer der bedeutendsten Mathematiker der Neuzeit, sagte einst:

> Aus dem Paradies, das Cantor uns geschaffen, soll uns niemand vertreiben können.
> 
> — David Hilbert

Allerdings führte das Cantor'sche Modell der Mengenlehre, auch *naive Mengenlehre* genannt, auch zu *Antinomien* (Widersprüchen).
[Bertrand Russell](https://de.wikipedia.org/wiki/Bertrand_Russell) entdeckte diese Widersprüche und machte sie publik.
Die heutige Mathematik beruht auf einer axiomatisierten Mengenlehre und wird auch *Zermelo-Fraenkel-Mengenlehre* genannt.
Doch ist die naive Mengenlehre ein Teil der ZF-Mengenlehre und daher nach wie vor ein einfacher und guter Zugang.

## Naive Mengenlehre nach Cantor
```admonish note title="Menge"
Unter einer *Menge* verstehen wir jede Zusammenfassung $M$ von bestimmten wohlunterschiedenen Objekten $m$ 
unserer Anschauung oder unseres Denkens zu einem Ganzen.
```

Mengen werden dabei mit den *Mengenklammern* $\{$ und $\}$ aufgeschrieben. 
Außerdem wird das Symbol $\in$ dafür verwendet um zu beschreiben, dass ein *Element* $m$ zu einer Menge $M$ gehört: $m \in M$.
Dagegen wird $\notin$ dafür verwendet, um zu beschreiben, dass ein Element $n$ nicht zur Menge $M$ gehört: $n \notin M$.

### Beispiele für Mengen
#### Ziffern 0 bis 5
Die Menge der Ziffern *0* bis *5*:
$$
   Z = \{ 0, 1, 2, 3, 4, 5 \}
$$
Dabei gilt z.B. $1 \in Z$ und $4 \in Z$, aber nicht $8 \in Z$, also $8 \notin Z$.

#### Ballarten
Folgendes könnte eine Menge von verschiedenen, aber nicht allen Ballarten sein:
$$
   B = \{ \text{Fußball}, \text{Tennisball}, \text{Baseball} \}
$$
Es gilt z.B. $\text{Fußball} \in B$ und $\text{Basketball} \notin B$.

### Antinomien
Diese *naive* Auffassung von Menge birgt allerdings Widersprüche, auch *Antinomien* genannt.

#### Russell'sche Menge
```admonish note title="Russell'schen Menge"
Menge aller Mengen, die sich nicht selbst als Element enthalten.
```

Sei die (russell'sche) Menge $X$ dadurch definiert, dass für alle Mengen $A$ gilt:
$$
   A \in X \text{ genau dann, wenn } A \notin A
$$

```admonish danger title="Enthält dich die Menfe selbst?"
Für $A := X$ erhält man den Widerspruch
$$
   X \in X \text{ genau dann, wenn } X \notin X
$$
```

Das funktioniert eben nicht: Wenn die Menge $X$ in $X$ selbst als Element liegt, dann darf sie aber nicht in $X$ liegen, 
da wir die Menge $X$ ja gerade so definiert haben, dass sie nur die Mengen enthält, die sich nicht selbst enthalten.
Andersherum heißt es, dass wenn $X$ nicht in $X$ ist, dann müsste sie in $X$ liegen wegen der Definition von $X$.

#### Barbier von Sevilla
Ein anderes Beispiel ist die Anekdote vom *Barbier von Sevilla*, die ebenfalls von Russell stammt.

```admonish note title="Barbier von Sevilla"
Der Barbier $B$ ist derjenige Mann von Sevilla, der genau die Männer $M$ von Sevilla rasiert, die sich nicht selbst rasieren.
```

Wir sagen nun, dass der Barbier $B$ sei. 
Der Barbier ist aber an sich keine Menge.
Die Anekdote kann man auch so formulieren, dass wir wieder nur "richtige" Mengen haben.
Für jetzt bezeichnen wir aber einfach die symbolische Schreibweise $M \in B$ als "*$M$ wird vom Barbier $B$ rasiert*".
Damit erhalten wir folgende Beziehung:
$$
   M \in B \text{ genau dann, wenn } M \notin M
$$

```admonish danger title="Rasiert der Barbier sich selbst?"
Für $M := B$ erhält man den Widerspruch
$$
   B \in B \text{ genau dann, wenn } B \notin B
$$
```

Also wenn der Barbier sich selbst rasiert, dann dürfte er sich ja nicht selbst rasieren, da er ja nur die rasiert, 
die sich nicht selbst rasieren.
Aber wenn der Barbier sich nicht selbst rasiert, dann müsste er sich ja entsprechend der Definition selbst rasieren.
Das funktioniert auch also nicht.

Cantor hat mit der naiven Mengenlehre einen großen Baustein der Mathematik geschaffen, auf dem die ganze Mathematik aufbaut.
Er hat außerdem den Begriffen Endlichkeit und Unendlichkeit Leben eingehaucht.
Doch hat sein Modell Schwächen, sodass man ein wenig daran arbeiten musste.
Viele weitere Dinge der Mengenlehre werden in den nächsten Kapiteln behandelt.
Bevor wir aber mit Mengen an sich weiter machen, folgt erstmal eine kurze Einführung in die Logik, auf der die weitere Mengenlehre aufbaut.
Zudem bildet die Logik das Fundament der mathematischen Beweise, die uns garantieren, dass Erkenntnisse eine allgemeine Gültigkeit haben.