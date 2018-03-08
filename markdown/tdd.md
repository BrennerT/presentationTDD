# Test Driven Development

note: 
Hauptthema der Präsentation

---

# Theorie

note: 
- Software Entwicklungs Prozess
- Besteht nicht nur aus Test zu erst schreiben -> Das ist Test First
- Designstrategie

--

## TDD Zyklus

![siehe Tafel](../img/TDD Zyklus.png) <!-- .element: height="350px"-->

***
[https://improuv.com/blog/daniel-zappold/tdd-so-einfach-und-doch-so-schwer](https://improuv.com/blog/daniel-zappold/tdd-so-einfach-und-doch-so-schwer)

note: 
1) Write a Test -> Was soll meine Komponente machen -> Unterschied zum klassischen Unit Test
2) Make the Test pass -> Implementierung der Komponente
3) Refactor

--

## 3 Goldene Regeln

1) You can't write any production code until you have first written a failing unit test. <!-- .element: class="fragment" height="100px"-->

2) You can't write more of a unit test than is sufficient to fail, and not compiling is failing. <!-- .element: class="fragment" height="100px"-->

3) You can't write more production code than is sufficient to pass the currently failing unit test. <!-- .element: class="fragment" height="100px"-->

note: 
Hier sollen die Regeln nacheinander angezeigt werden
Fehler werden automatisch aufgedeckt

--

## Greybox 

---

# Beispiel

- `primeFactors` nimmt eine Ganzzahl
- `primeFactors` gibt eine Liste von Ganzzahlen zurück
- `primeFactors` berechnet Primfaktoren

--

``` kotlin
    "1 has no prime factors" {
        primeFactors(1) 
    }
```

``` kotlin 
    fun primeFactors(n: Int): List<Int> = TODO()
```
<!-- .element: class="fragment"-->

--

``` kotlin
    "1 has no prime factors" {
        primeFactors(1) shouldEqual emptyList()
    }
```

``` kotlin 
    fun primeFactors(n: Int): List<Int> = emptyList()
```
<!-- .element: class="fragment"-->

--

...

---

# Pattern

note: 
- Testbarer Code
- Entwicklung Bottom Up, Top-Down

--

## Top-Down TDD

![top down](../img/tdd-outside-in.jpg)

***
[https://image.slidesharecdn.com/tddcommented-130125160145-phpapp01/95/tdd-outsidein-6-638.jpg?cb=1383700832](https://image.slidesharecdn.com/tddcommented-130125160145-phpapp01/95/tdd-outsidein-6-638.jpg?cb=1383700832)

note: 
System analysieren?
Was soll mein System machen?

--

## Bottom-Up TDD

![bottom up](../img/tdd-bottom-up.jpg)

***
[https://image.slidesharecdn.com/tddcommented-130125160145-phpapp01/95/tdd-outsidein-4-638.jpg?cb=1383700832](https://image.slidesharecdn.com/tddcommented-130125160145-phpapp01/95/tdd-outsidein-4-638.jpg?cb=1383700832)

note:
Einzelne Komponenten des Systems beschreiben. 
Am Ende zusammensetzen.
Evolutionäres Prototyping?

---

# Praktische Erfahrungen

note: 
- TDD gegen nicht testen 
    - HTML Clients im Arsch
- Wie strikt wird es eingehalten?
    - Compilierfehler
    - Random Daten erzeugen (siehe Property based)
    - Was wird getestet?
- Große Probleme am Anfang
- Erfahrungen IBM 
    - Dauert ~10% länger
    - Aber 50% weniger Defects

---

# Ergebnisse und Probleme

note: 
- Was ist eine Unit?
- Anforderungen werden verstanden
- Anfang ist schwer, Neue Frameworks extrem schwer
- BDD
- Unit Tests helfen bei der Dokumentation, indem sie beabsichtigte Verwendungen und Reaktionen aufzeigen
