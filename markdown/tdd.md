# Test Driven Development

note: 
- Um die eben genannten Probleme zu lösen wurde ein neuer Ansatz gesucht
- Erst alle Tests, dann die Klasse
- Welche Antworten will ich haben? vs. Welche Fragen stelle ich?

--

## TDD Zyklus

![siehe Tafel](img/TDD Zyklus.png) <!-- .element: height="350px"-->

***
[TDD - so einfach und doch so schwer, Daniel Zappold](https://improuv.com/blog/daniel-zappold/tdd-so-einfach-und-doch-so-schwer)<!-- .element: style="font-size: 20px" -->

note: 
- Schritt 1 gibt klaren Fokus, Großes Problem in Teilschritte zerlege
- Schritt 2 Code erfüllt, Test so einfach wie möglich bestehen
- Lösungen aus Schritt 2 sind häufig nicht schön -> nicht generisch zum Beispiel
- Schritt 3 anpassen der Code und Teststruktur das Design optimiert wird

--

## 3 Goldene Regeln

1) You can't write any production code until you have first written a failing unit test. <!-- .element: class="fragment" height="100px"-->

2) You can't write more of a unit test than is sufficient to fail, and not compiling is failing. <!-- .element: class="fragment" height="100px"-->

3) You can't write more production code than is sufficient to pass the currently failing unit test. <!-- .element: class="fragment" height="100px"-->

***
[The Three Laws of Test-Driven-Development, Uncle Bob](http://programmer.97things.oreilly.com/wiki/index.php/The_Three_Laws_of_Test-Driven_Development)<!-- .element: style="font-size:20px" -->

note: 
Vorteile
- Debugging
- Courage
- Documentation
- Design
- Professionalism

-- 
## Bottom-Up TDD

![bottom up](img/bottom-up-tdd.png)<!-- .element: height="350px" -->

***
[https://image.slidesharecdn.com/tddcommented-130125160145-phpapp01/95/tdd-outsidein-4-638.jpg?cb=1383700832](https://image.slidesharecdn.com/tddcommented-130125160145-phpapp01/95/tdd-outsidein-4-638.jpg?cb=1383700832)<!-- .element: style="font-size: 20px" -->

note:
- Beginn bei Datenmodelierungsebene
- Keine Mocks benötigt


--

## Outside-In TDD

![top down](img/outside-in-tdd.jpg)<!-- .element: height="350px" -->

***
[https://image.slidesharecdn.com/tddcommented-130125160145-phpapp01/95/tdd-outsidein-6-638.jpg?cb=1383700832](https://image.slidesharecdn.com/tddcommented-130125160145-phpapp01/95/tdd-outsidein-6-638.jpg?cb=1383700832)<!-- .element: style="font-size: 20px" -->

note: 
- Entwicklung von Nutzungsebene ab
- Mocks werden sehr oft benötigt

--

## Greybox 

![Greybox](img/greybox.jpeg)

***
[Grey-Box-Testing: entwicklungsnah testen](https://jaxenter.de/grey-box-testing-entwicklungsnah-testen-28915)<!-- .element: style="font-size:20px" -->

---

# Beispiel

- `primeFactors` nimmt eine Ganzzahl
- `primeFactors` gibt eine Liste von Ganzzahlen zurück
- `primeFactors` berechnet Primfaktoren

--

### Test & Implement

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

### Test & Implement

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

### Test & Implement

``` kotlin
    "2 has prime factors [2]" {
        primeFactors(2) shouldEqual listOf(2)
    }
```

``` kotlin
    fun primeFactors(n: Int): List<Int> =
        if (n == 1) emptyList()
        else listOf(2)
```
<!-- .element: class="fragment"-->


--

### Test & Implement

``` kotlin
    "3 has prime factors [3]" {
        primeFactors(2) shouldEqual listOf(2)
    }
```

``` kotlin
    fun primeFactors(n: Int): List<Int> =
        if (n == 1) emptyList()
        if (n == 3) listOf(3)
        else listOf(2)
```
<!-- .element: class="fragment"-->

--

### Refactor

``` kotlin
    fun primeFactors(n: Int): List<Int> =
        if (n == 1) emptyList()
        else listOf(n)
```

--

### Test & Implement

``` kotlin
    "4 has prime factors [2, 2]" {
        primeFactors(4) shouldEqual listOf(2, 2)
    }
```

``` kotlin
    fun primeFactors(n: Int): List<Int> =
        if (n == 1) emptyList()
        else if (n == 4) listOf(2, 2)
        else listOf(n)
```
<!-- .element: class="fragment"-->


--

### Test & Implement

``` kotlin
    "6 has prime factors [2, 3]" {
        primeFactors(6) shouldEqual listOf(2, 3)
    }
```

``` kotlin
    fun primeFactors(n: Int): List<Int> =
        if (n == 1) emptyList()
        else if (n == 4) listOf(2, 2)
        else if (n == 6) listOf(2, 3)
        else listOf(n)
```
<!-- .element: class="fragment"-->

--

### Refactor


``` kotlin
    fun primeFactors(n: Int): List<Int> =
        if (n == 1) emptyList()
        if (n > 2 && n % 2 == 0) listOf(2, n / 2)
        else listOf(n)
```


--

### Test & Implement

``` kotlin
    "8 has prime factors [2, 2, 2]" {
        primeFactors(8) shouldEqual listOf(2, 2, 2)
    }
```

``` kotlin
    fun primeFactors(n: Int): List<Int> =
        if (n == 1) emptyList()
        if (n == 8) listOf(2, 2, 2)
        if (n > 2 && n % 2 == 0) listOf(2, n / 2)
        else listOf(n)
```
<!-- .element: class="fragment"-->


--

### Refactor

``` kotlin
    fun primeFactors(n: Int): List<Int> {
        if (n == 1) return emptyList()

        var nn = n
        val result = mutableListOf<Int>()
        while (nn > 2 && nn % 2 == 0) {
            result.add(2)
            nn /= 2
        }
        if (nn != 1) {
            result.add(nn)
        }

        return result
    }
```


--

### Test & Implement

``` kotlin
    "9 has prime factors [3, 3]" {
        primeFactors(9) shouldEqual listOf(3, 3)
    }
```

``` kotlin
    fun primeFactors(n: Int): List<Int> {
        if (n == 1) return emptyList()

        var nn = n
        val result = mutableListOf<Int>()
        while (nn > 2 && nn % 2 == 0) {
            result.add(2)
            nn /= 2
        }
        while (nn > 3 && nn % 3 == 0) {
            result.add(3)
            nn /= 3
        }
        if (nn != 1) {
            result.add(nn)
        }

        return result
    }
```
<!-- .element: class="fragment"-->


--

### Refactor

``` kotlin
    fun primeFactors(n: Int): List<Int> {
        if (n == 1) return emptyList()

        var nn = n
        val result = mutableListOf<Int>()

        for (factor in 2 .. n) {
            while (nn > factor && nn % factor == 0) {
                result.add(factor)
                nn /= factor
            }
        }
        if (nn != 1) {
            result.add(nn)
        }

        return result
    }
```
<!-- .element: height=500px -->

--

### Test 

``` kotlin
    "prime factors works for really big numbers" {
        val primeFactors = listOf(2, 2, 3, 3, 3, 31, 31, 41)
        val n = primeFactors.reduce(Int::times)

        primeFactors(n) shouldBe primeFactors
    }
```

--

### Refactor

``` kotlin
    fun primeFactors(n: Int): List<Int> {
        if (n == 1) return emptyList()

        var nn = n
        val result = mutableListOf<Int>()

        for (factor in 2 .. n) {
            while ( nn % factor == 0) {
                result.add(factor)
                nn /= factor
            }
        }

        return result
    }
```

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

--

## Tests in der Praxis

``` kotlin
    "1 has no prime factors" {
        primeFactors(1) shouldEqual emptyList()
    }
    
    "primes only have themself as prime factors" {
        val prime = randomPrime()
        primeFactors(prime) shouldEqual listOf(prime)
    }
    
    "other numbers have prime factors" {
       val primes = randomListOf(::randomPrime).sort()
       val n = primes.reduce(Int::times)
       primeFactors(n) shouldEqual primes
    }
```

--

## Geringere Defect Rate

![Klassisch](img/ibm-adhoc.png)<!-- .element: style="height: 180px" -->
![TDD](img/ibm-tdd.png)<!-- .element: style="height: 220px" -->

***

[Assessing Test-Driven Development at IBM](https://pdfs.semanticscholar.org/a3d3/51a7dfd1c4b03ba0611e467054644c4c8450.pdf) <!-- .element: style="font-size: 20p20px" -->

---

# Ergebnisse und Probleme  

-- 

# Nachteile

- Dauert länger?
- Schwerer Einstieg

note: 
- dauert länger wird häufig behauptet

-- 

# Vorteile

- Anforderungen werden verstanden<!-- .element: class="fragment" -->
- Keine unnötigen Funktionen werden implementiert <!-- .element: class="fragment" -->
- Jede Zeile Code ist getestet <!-- .element: class="fragment" -->
- Fügt sich gut in agile Methoden ein <!-- .element: class="fragment" -->

note: 
- Anforderungen werden verstanden
- Unit Tests helfen bei der Dokumentation, indem sie beabsichtigte Verwendungen und Reaktionen aufzeigen

---

# Ausblick BDD

![Erweiterung TDD Zyklus](img/bdd.jpg)<!-- .element: height="300px"-->

***
[http://blog.apollossc.com/wp-content/uploads/2017/11/bdd2.png](http://blog.apollossc.com/wp-content/uploads/2017/11/bdd2.png)<!-- .element: style="font-size: 20px" -->

note:
* Erweiterung von TDD
* Tests für Kunden verständlich sein
* Kunde beschreibt Feature
* In TDD wird aus Feature abgeleitetes Szenario in Testfall umgewandelt

-- 

## Beispiel

![Feature zu Szenario](img/bdd-idee.png)<!-- .element: height="300px"-->

***
[BDD TESTING WITH TESTCOMPLETE, SmartBear Software](https://support.smartbear.com/articles/testcomplete/bdd-testing-with-testcomplete/)<!-- .element: style="font-size: 20px" -->
