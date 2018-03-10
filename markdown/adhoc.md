# Tests

note: 
- Wir wissen nun das wir Softwarequalität brauchen
- Wie erreichen wir sie?
- Was ist ein Softwaretest? 

--

## Definition Softwaretest

>"Program testing can be a very effective way to show the presence of bugs, but is hopelessly inadequate for showing their absence."

[The Humble Programmer, Edsger W. Dijkstra](http://www.cs.utexas.edu/~EWD/transcriptions/EWD03xx/EWD340.html)

note: 
- Testen = stichprobenartiges Prüfen
- keine Verifikation, d.h. Korrektheit nur durch logische Schlussfolgerung beweisbar

-- 


## Arten von Tests

--

## Unit Test

```java
public class Calculator{

    public static int add(int x, int y){ 
     return x + y; 
    }

    public static int divide(int dividend, int divisor){ 
     return dividend / divisor;
    }

}
``` 
<!-- .element: class="fragment" width="200px"-->

```java
@Test
public void addTest(){
    int actual = Calculator.add(1, 2);
    Assert.areEqual(3, actual);
}
```
<!-- .element: class="fragment" width="200px"-->

note:
- Testen einer Einheit der Software
- Ziel: fehlerfreie Funktion jeder einzelnen Einheit
- Problem: Was ist eine Einheit?

--

## Was ist eine Unit?

*"smallest piece of software"*, MSDN

*"unit of work"*, The Art of Unit Testing - Roy Osherove

***
[What exactly is a "unit" in unit testing?, Rui Figueiredo](https://www.blinkingcaret.com/2016/04/27/what-exactly-is-a-unit-in-unit-testing/)<!-- .element: style="font-size: 20px" -->

note:
- Nennt unterschiedliche definition aus der Literatur 
- unit of work bezeichnet summe aller aktionen die zwischem dem aufruf einer Methode und einem durch einen Test messbaren ergebniss stehen 
- Schlussfolgerung -> Unit ist logischer Pfad den das ausführen einer Methode benötigt

--

## Was zeichnet gute Unit Tests aus

- sind isoliert <!-- .element: class="fragment" -->
- sichern jeweils genau eine Eigenschaft ab <!-- .element: class="fragment" -->
- sind leicht verständlich und kurz <!-- .element: class="fragment" -->
- testen relevanten Code <!-- .element: class="fragment" -->
- weisen genauso hohe Code Qualität auf, wie der Produktiv Code selbst <!-- .element: class="fragment" -->

***
[Unit-Tests, it-agile](https://www.it-agile.de/wissen/agiles-engineering/unit-tests/)<!-- .element: style="font-size:20px" -->

note: 
- Tests sollen in beliebiger Reihenfolge ausführbar sein -> Parrallelisierung
- Falsches Verhalten soll sich nur an einer Stelle zeigen
- leicht verständlich, unterstützt Dokumentation
- Getter und Setter testen ja/nein?
- Reichen Unit Tests aus?

--
## Integration Test

![integration test failing](img/integration-test.jpg)<!-- .element: height="350px" -->

***
[https://chriskottom.com/images/unit-tests-passing-no-integration-tests.jpg](https://chriskottom.com/images/unit-tests-passing-no-integration-tests.jpg)<!-- .element: style="font-size: 20px"-->

note:
- Logik die zwischen den Komponenten Existiert kann fehlschlagen
- Integrationstests prüfen ob Komponenten richtig zusammenarbeiten
- Ziel: Fehlerfreies zusammenwirken der Systemkomponenten

--
## End-to-End Test

![end to end example](img/end-to-end-example.png)

***
[Why End to End Testing is Necessary and How to Perform It?](http://www.softwaretestinghelp.com/what-is-end-to-end-testing/)<!-- .element: style="font-size:20px" -->
note:
- Testen aus der Nutzer Perspektive
- Prüfen wie sich die Software unter realen Bedingungen verhält
- Integration -> Zwei Boxen
- E2E -> Alle Boxen

-- 

## Black Box Tests

![black box](img/blackbox.PNG)

- Grenzwertanalyse  <!-- .element: class="fragment" -->
- Equivalenzklassen <!-- .element: class="fragment" -->
- Fehler raten <!-- .element: class="fragment" -->


***
[White Box Testing and Black Box Testing in Software Testing](https://www.testing-whiz.com/blog/understanding-white-box-testing-and)<!-- .element: style="font-size: 20px" -->


note:
- Wie immer im Software Engeneering gibt es Black & White Boxes
- Im Grunde hat der Tester (wer auch immer das ist) keine Ahnung, wie das System implementiert ist
- Es werden nur die Spezifikationen genommen und daraus Testcases erstellt und in das Programm reingeworfen
- Dann macht das Programm etwas (was genau ist dem Tester egal)
- Und am Ende kommt ein richtiges oder falsches Ergebniss
- Das ganze kann manuell explorativ sein, oder automatisiert
- Es gibt auch negativ Cases
- Man kann Grenzwertanalyse machen (Beispiel?)
- Man kann Equivalenzklassen nutzen 
- Man kann Fehler raten
- Also alles in allem ziemlich Funktional

-- 


## White Box Tests

![white box](img/whitebox.PNG)

- Kontrollfluss  <!-- .element: class="fragment" -->
- Datenfluss <!-- .element: class="fragment" -->

***
[White Box Testing and Black Box Testing in Software Testing](https://www.testing-whiz.com/blog/understanding-white-box-testing-and)<!-- .element: style="font-size: 20px" -->

note:
- Offensichtlich das Gegenteil
- Tester kennt das System und entwickelt anhand der genauen implementierung Testcases
- Dazu muss er das System analysieren und verstehen und schreibt Cases um jede Zeile zu testen
- Tester schaut, welche Stellen fehleranfällig sein können
- Controllflow tests usw.

--

## Testautomatisierung

![Tests werden heute nicht auf Knopfdruck gezeigt](img/test-auf-knopfdruck.jpg)<!-- .element: height="300px" -->

***
[https://www.isg-stuttgart.de/fileadmin/_processed_/csm_Fotolia_131459855_L_Testautomatisierung_55885ae42f.jpg](https://www.isg-stuttgart.de/fileadmin/_processed_/csm_Fotolia_131459855_L_Testautomatisierung_55885ae42f.jpg)<!-- .element: style="font-size: 20px" -->

note:
- Wir wissen Jetzt was für Tests es gibt
- Sollen wir sie automatisieren?
- Testen von Hand fehler anfällig, dauert lange
- Testen auf Knopfdruck gibt direktes Feedback, Nimmt angst Code zu bearbeiten

--

## Automatisierungs Pyramide

![Das Antipattern will sich nicht zeigen](img/antipattern-automated-tests.png)<!-- .element: height="350px" -->

***
[Best Testing Practices for Agile Teams: The Automation Pyramid, Sofia Palamarchuk](https://abstracta.us/blog/test-automation/best-testing-practices-for-agile-teams-the-automation-pyramid/)<!-- .element: style="font-size: 20px"-->

note:
- Unit Tests sind die billigsten Tests
- GUI Tests umfangreich und Einheiten übergreifend -> Unit Tests geben Präzisere Fehler
- Weniger Exploratives Testen und Bug Suche am Ende
- Wir wissen jetzt das es sinnvoll ist automatisierte Tests zu schreiben
- Wie formuliere ich einen Test?

---

# Mocks

--

## Einfach zu testen

- Funktionaler Code
- Interfaces

***
[Which GOF design patterns work well with TDD, and which do not?](https://softwareengineering.stackexchange.com/questions/115020/which-gof-design-patterns-work-well-with-tdd-and-which-do-not) <!-- .element: style="font-size: 20px" -->

--

## Schwer zu testen

- (globaler) State
- Seiteneffekte


***
[Which GOF design patterns work well with TDD, and which do not?](https://softwareengineering.stackexchange.com/questions/115020/which-gof-design-patterns-work-well-with-tdd-and-which-do-not) <!-- .element: style="font-size: 20px" -->

--

## Ausgangssituation

- Objekt liefert nicht-deterministische Ergebnisse <!-- .element: class="fragment"-->
- Objekt besitzt Zustände die sich nicht erzeugen oder reproduzieren lassen <!-- .element: class="fragment"-->
- Objekt ist langsam <!-- .element: class="fragment"-->
- Objekt ist bisher noch nicht implementiert <!-- .element: class="fragment"-->
- Objekt müsste nur für die Tests Funktionen implementieren <!-- .element: class="fragment"-->

note:
- nicht deterministisch bedeutet bei jeder Ausführung anders (Datum)
- Zustände, Netzwerkfehler
- langsam z.Bsp. Datenbank
- Häufig im Top Down der Fall 
- Wie lösen wir das?

-- 

## Stubs

>**Stub**: stellt vorgefertigte Antworten zur Verfügung</br>

***
[Mocks aren't Stubs, Martin Fowler](https://www.martinfowler.com/articles/mocksArentStubs.html)<!-- .element: style="font-size: 20px" --> 

note:
- Simulieren das Verhalten von realen Objekten
- Interface ist identisch mit dem des simulierten Objekts
Beispiel:
- a stub cook - a hot dog vendor that always gives you hot dogs no matter what you order, or

-- 

## Mocks

>**Mock**: simuliert das Verhalten eines realen Objektes in einem vorgegebenen Weg</br>

note: 
- a mock cook - an undercover cop following a script pretending to be a cook in a sting operation.

--

## Fakes

>**Fake**: Besitzt eine funktionierende Implementation

note: 
- a fake cook - a someone pretending to be a cook by using frozen dinners and a microwave,

---

# Ergebnisse & Probleme

note:
- Das Test sinnvoll sind, haben bestimmt alle verstanden
- Mit den hier gezeigten Pattern, kann man auch ganz gut implementieren und testen
- Aber es gibt auch Probleme:
    1) *Kurs fragen* Wer testet? Wer mag testen?
       Generell macht testen einfach keinen Spaß... ich will entwickeln
       Da fehlt Befriedigung etwas zu erreichen
    2) Was ist die Motivation zu testen? Was ich schreibe funktioniert doch, dass **weiß** ich!
    3) Funktion sieht schwer testbar aus... aber die funktioniert bestimmt, also teste ich nicht

--

## Probleme

- Sinnlose Tests
- Bugs machen keinen Spaß... Testen auch nicht
- Mein Code funktioniert!
- Code schwierig zu testen...
- Was bringt geringe Testabdeckung?

note: 
- T: Fehler werden übersehen
    
- D: Warum Testen, das funktioniert
- D: Macht der Tests wirklich etwas?
- D: Code untestbar geschrieben
- D: Wer muss Tests schreiben? -> Tests sucken
- T: Externes Team ist schlecht
    externe Teams sind billiger
    Personalaufwand
    Testteam nervt -> Entwickler haben weniger Spaß
- T: Geringe Testabdeckung ist schlechter als gar keine Tests
    geben das gefühl man hätte etwas getestet, dass ist aber nicht wirklich so
    viele Tests bleiben unentdeckt

--

## Was macht der Test?

``` kotlin
    @Test
    fun `deleteAll deletes all fields from db`() {
        // Given: some fields in the db
        val fieldsInDb = createRandomFields()
        fieldsAccessor.insert(fieldsInDb)
        
        // When: we delete all fields
        fieldsAccessor.deleteAll()
        
        // Then: there are non left
        val fieldsLeft = fieldsAccessor.getAll()
        fieldsLeft should beEmpty
    }
```
<!-- .element: class="fragment" -->


``` kotlin
    fun getAll() {
        // hm... these are not fields
        return database.allProcesses()
    }
```
<!-- .element: class="fragment" -->

note:
- Es kann auch Tests geben, die eigentlich gar nichts bringen
- Hier ein Beispiel von meiner Arbeit
- *Test erklären*
- Der Test sieht eigentlich gut aus... aber die zu testene Funktion konnte man auskommentieren
- In der Implementierung sieht man, dass der Test in Wahrheit überhaupt nichts testet
- Das ist ein Fall, den man unbedingt vermeiden muss
