# Test Driven Development

note: 
- Um die eben genannten Probleme zu lösen wurde ein neuer Ansatz gesucht
- Erst alle Tests, dann die Klasse
- Unterschied zum klassischen Test -> Design
- Welche Antworten will ich haben? vs. Welche Fragen stelle ich?

--

## TDD Zyklus

![siehe Tafel](../img/TDD Zyklus.png) <!-- .element: height="300px"-->

***
[https://improuv.com/blog/daniel-zappold/tdd-so-einfach-und-doch-so-schwer](https://improuv.com/blog/daniel-zappold/tdd-so-einfach-und-doch-so-schwer)<!-- .element: style="font-size: 20px" -->

note: 
- Für Agile Softwareentwicklung 
- Zyklus sorgt dafür das keine unnötigen Funktionen implementiert werden

--

## 3 Goldene Regeln

1) You can't write any production code until you have first written a failing unit test. <!-- .element: class="fragment" height="100px"-->

2) You can't write more of a unit test than is sufficient to fail, and not compiling is failing. <!-- .element: class="fragment" height="100px"-->

3) You can't write more production code than is sufficient to pass the currently failing unit test. <!-- .element: class="fragment" height="100px"-->

note: 
- 1 überlegen warum ich überhaupt eine funktion benötige
- 2 nicht über mehr als eine funktion gleichzeitig nachdenken
- 3 stellt sicher das kein unnötiger Code geschrieben wird

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

# Ansätze

--

## Outside-In TDD

![top down](../img/tdd-outside-in.jpg)

***
[https://image.slidesharecdn.com/tddcommented-130125160145-phpapp01/95/tdd-outsidein-6-638.jpg?cb=1383700832](https://image.slidesharecdn.com/tddcommented-130125160145-phpapp01/95/tdd-outsidein-6-638.jpg?cb=1383700832)<!-- .element: style="font-size: 20px" -->

note: 
- Entwicklung von Nutzungsebene ab
- Mocks werden sehr oft benötigt

--

## Bottom-Up TDD

![bottom up](../img/tdd-bottom-up.jpg)

***
[https://image.slidesharecdn.com/tddcommented-130125160145-phpapp01/95/tdd-outsidein-4-638.jpg?cb=1383700832](https://image.slidesharecdn.com/tddcommented-130125160145-phpapp01/95/tdd-outsidein-4-638.jpg?cb=1383700832)<!-- .element: style="font-size: 20px" -->

note:
- Beginn bei Datenmodelierungsebene
- Keine Mocks benötigt

---

# Praktische Erfahrungen

- Wie strikt wird TDD eingehalten?<!-- .element: class="fragment" -->
- Aller Anfang ist schwer<!-- .element: class="fragment" -->
- Erfahrungen IBM <!-- .element: class="fragment" -->

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

- Anforderungen werden verstanden<!-- .element: class="fragment" -->
- Keine unnötigen Funktionen werden implementiert <!-- .element: class="fragment" -->
- Jede Zeile Code ist getestet <!-- .element: class="fragment" -->

note: 
- Anforderungen werden verstanden
- Unit Tests helfen bei der Dokumentation, indem sie beabsichtigte Verwendungen und Reaktionen aufzeigen

---

# Ausblick BDD

![Erweiterung TDD Zyklus](../img/bdd.jpg)<!-- .element: height="300px"-->

***
[http://blog.apollossc.com/tribunes/agile/lab-n1-tdd-atdd-bdd-cest-quoi-difference/](http://blog.apollossc.com/tribunes/agile/lab-n1-tdd-atdd-bdd-cest-quoi-difference/)<!-- .element: style="font-size: 20px" -->

note:
* Erweiterung von TDD
* Tests für Kunden verständlich sein
* Kunde beschreibt Feature
* In TDD wird aus Feature abgeleitetes Szenario in Testfall umgewandelt

-- 

## Beispiel

![Feature zu Szenario](../img/bdd-idee.png)<!-- .element: height="300px"-->

***
[https://support.smartbear.com/articles/testcomplete/bdd-testing-with-testcomplete/](https://support.smartbear.com/articles/testcomplete/bdd-testing-with-testcomplete/)<!-- .element: style="font-size: 20px" -->