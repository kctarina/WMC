# KM3-04 – CSS-Selektoren: schriftliche Antworten

**Name:** Katarina Mlakic  
**Klasse:** 3CAIF  
**Abgabe:** __________________

## Beispiel 1

### a) Verwendete Selektoren

1. Kopfzeile: `main > section:last-child > table thead tr`
2. Jede zweite Datenzeile: `main > section:last-child > table tbody tr:nth-child(even)`
3. Letzter Eintrag, linker Rand: `main > section:last-child > table tbody tr:last-child td:first-child`

Die Auswahl ist auf den neuen Abschnitt begrenzt, damit die vorhandene Labor-Tabelle unverändert bleibt. Der Rand wird auf die erste Zelle gesetzt, damit er mit `border-collapse: collapse` sichtbar ist.

### b) Selektoren

- Zweiter Schritt: `main > section:last-child > ol > li:nth-child(2)`
- Vorletzter Schritt: `main > section:last-child > ol > li:nth-last-child(2)`

### c) Warum `:has()` statt `:is()`?

Mit `.kasten:has(img)` wird ein Kasten ausgewählt, **wenn er ein `img`-Element enthält**. `:is(img)` würde dagegen nur Elemente auswählen, die selbst ein Bild sind; es kontrolliert nicht, ob ein Kasten ein Bild als Nachfahren hat.

## Beispiel 2

### a) Richtig oder falsch?

- [x] `p.hinweis` trifft nur Absätze mit der Klasse `hinweis`.
- [x] `h2 ~ p` trifft Absätze, die nach einer `h2` stehen und denselben Elternknoten haben.
- [ ] `:nth-child(2)` und `:nth-of-type(2)` treffen immer dasselbe Element.
- [x] Bei sonst gleicher Priorität und Spezifität gewinnt die später notierte Regel.

**Begründung zu Aussage 3:** `:nth-child(2)` bezieht sich auf das zweite Kind insgesamt. `:nth-of-type(2)` bezieht sich auf das zweite Geschwisterelement desselben Elementtyps. Wenn etwa erst eine `h3` und danach zwei `p`-Elemente stehen, ist der erste Absatz das zweite Kind, aber nicht der zweite Absatz.

### b) Ein Selektor pro Ziel

| Ziel | Selektor |
| --- | --- |
| Alle Links, deren Ziel auf `.pdf` endet | `a[href$=".pdf"]` |
| Alle Absätze außer `.hinweis` | `p:not(.hinweis)` |
| Das erste `li` in jeder `ul` | `ul > li:first-child` |
| Jedes Element, das ein Bild enthält | `:has(img)` |
| Angehaktes Kontrollkästchen direkt vor einem Label: dessen Label auswählen | `input[type="checkbox"]:checked + label` |

### c) Fehler und richtige Regel

Die Regel `p:nth-child(1)` trifft nur dann einen Absatz, wenn er das erste Kind seines Elternteils ist. Steht vorher eine Überschrift, ist der erste Absatz nicht das erste Kind. Für den ersten Absatz seines Typs verwendet man:

```css
p:first-of-type {
    font-weight: bold;
}
```

Falls nur direkte Kinder **eines bestimmten Containers** gemeint sind, ergänzt man dessen Selektor vor `> p:first-of-type`.

## Beispiel 3

### a) bis c)

Die vollständigen CSS-Regeln stehen in `loesung.css`.

### d) Begründung in zwei Sätzen

Ich habe einen Attribut-Selektor verwendet, weil das `data-topic`-Attribut bereits im HTML vorhanden ist und die Sektion beschreibt. Mit `[data-topic^="css-adv"]` werden alle passenden Sektionen über den Beginn ihres Attributwerts ausgewählt, ohne dafür eine weitere Klasse einfügen zu müssen.
