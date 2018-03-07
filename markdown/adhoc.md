# Klassischer Ansatz

note: 
- Eigene Teams für Testing
- Oft Outsourcing

---

# Tests

note: 
Ziel: Herausfinden ob Softwarefehler enthält
Was ist ein Softwaretest? 

--

## Definition Softwaretest

>"Programm testing can be used to show the presence of Bugs, but never their absence"

Edsger W. Dijkstra

note: 
- Testen = stichprobenartiges Prüfen
- keine Verifikation, d.h. Korrektheit durch logische Schlussfolgerung beweisen
- Ziel, vollständige Testabdeckung
- Problem, wie werden Tests ausgeführt? durchklicken oder automatisiert

-- 

## Black Box vs. White Box

![This should be an image with black box and white box comparison](../img/blackbox und whitebox tests.jpg)

***
[http://m.softwaretestinggenius.com/?page=details&url=white-box-unit-testing-a-bottom-up-approach-of-software-testing](http://m.softwaretestinggenius.com/?page=details&url=white-box-unit-testing-a-bottom-up-approach-of-software-testing)<!-- .element: style="font-size: 25px" -->

note: 
Whitebox: Einblick in das zu testende Programm ist vorhanden, Entwicklersicht
Blackbox: Kein Einblick in das getestete Programm, Anwendersicht 
Sollten Tests nach Black- oder White-Box Prinzip verarbeitet werden?
Im TDD werden zu Beginn Blackbox Tests geschrieben

-- 

## Arten von Tests

--

## Unit Test

- Testen einer Komponente der Software <!-- .element: class="fragment" -->
- Ziel: fehlerfreie Funktion jeder einzelnen Komponente <!-- .element: class="fragment" -->
- Black-Box Test <!-- .element: class="fragment" -->

note:

--

## Was zeichnet gute Unit Tests aus

- sind isoliert <!-- .element: class="fragment" -->
- sichern jeweils genau eine Eigenschaft ab <!-- .element: class="fragment" -->
- sind leicht verständlich und kurz <!-- .element: class="fragment" -->
- testen relevanten Code <!-- .element: class="fragment" -->
- weisen genauso hohe Code Qualität auf, wie der Produktiv Code selbst <!-- .element: class="fragment" -->

note: 
- Tests sollen in beliebiger Reihenfolge ausführbar sein
- Falsches Verhalten soll sich nur an einer Stelle zeigen
- leicht verständlich, unterstützt Dokumentation
- keine Getter und Setter testen
--

## Integration Test

- Testen der Kopplung der Komponenten <!-- .element: class="fragment" -->
- System wird als White-Box betrachtet <!-- .element: class="fragment" -->
- Jede Systemkomponente muss zuvor getestet werden <!-- .element: class="fragment" -->
- Ziel: Fehlerfreies zusammenwirken der Systemkomponenten <!-- .element: class="fragment" -->

note:
- Integrationstests prüfen ob Komponenten richtig zusammenarbeiten
- Prüfen ob die Logik funktioniert wie geplant

--
## End-to-End Test

- Prüfen wie sich die Software unter real Bedingungen verhält <!-- .element: class="fragment" -->
- Häufig Performance Tests <!-- .element: class="fragment" -->
- Testen aus der Nutzer Perspektive <!-- .element: class="fragment" -->

note: 
- Prüfen ob die UI sich so verhält wie es erwartet wird.
- Kann auch für Kundenvorführung verwendet werden

--

## Testautomatisierung

![Tests werden heute nicht auf Knopfdruck gezeigt](../img/test-auf-knopfdruck.jpg)<!-- .element: height="300px" -->

***
[https://www.isg-stuttgart.de/fileadmin/_processed_/csm_Fotolia_131459855_L_Testautomatisierung_55885ae42f.jpg](https://www.isg-stuttgart.de/fileadmin/_processed_/csm_Fotolia_131459855_L_Testautomatisierung_55885ae42f.jpg)<!-- .element: style="font-size: 25px" -->

note:
- Ausgangssituation: (symbolische Ausführung) Entwickler klickt sich vor commit durch einen Ablauf um zu prüfen ob alles noch funktioniert
- Problem: Sehr Fehler anfällig -> nicht alle Fehler werden erkannt
- Lösung: Tests werden automatisiert -> Ergebnisse auf Knopfdruck
- Vorteile: 
erleichtert das Testen in Druckphasen eines Projektes
Feedback auf Knopfdruck

--

## Automatisierungs Pyramide

![Das Antipattern will sich nicht zeigen](../img/antipattern-automated-tests.png)<!-- .element: height="350px" -->

***
[https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQrgB1E6r9R5Sjj2he_81PxP_MkHG5y_XXSiW9M1jx6DmYNPdjHzw](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQrgB1E6r9R5Sjj2he_81PxP_MkHG5y_XXSiW9M1jx6DmYNPdjHzw)<!-- .element: style="font-size: 25px"-->

note:
- Unit Tests sind die billigsten Tests
- Mid Layer, immer hier automatisieren anstatt in der UI
- UI Layer, am wenigstens tests, da diese die aufwändigsten Tests sind


---

# Praktische Erfahrungen

---

# Frameworks

note:
- Helfen bei der Programmierung von Tests
- Beschreiben was eine Komponente macht, nicht wie sie es macht

-- 

## Beispiel JUnit

```Java
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

```Java
@Test
public void addTest(){
    int actual = Calculator.add(1, 2);
    Assert.AreEqual(3, actual);
}
```
<!-- .element: class="fragment" width="200px"-->

note:
- Unit Tests in Java
- makieren eines Tests mit Annotation 
- Was ist eine Unit?
- Bereits für TDD verwendet

-- 

## Beispiel Jasmine

```JavaScript
   function helloWorld() {
    return "Hello world!";
   }
```
<!-- .element: class="fragment" --> 

```JavaScript
   describe("HelloWorld", () => {
    it("says hello", () => {
     expect(helloWorld()).toEqual("Hello world!");
    })
   })
```
<!-- .element: class="fragment" --> 

note: 
- noch nicht verwendet
- keywords describe, it, expect

--

## Property Based Testing

---

# Pattern

-- 

## Mocks

![No image here](../img/mocking-pattern.png) 

***
[http://www.dotnetcurry.com/images/mvc/ASP.NET-MVC-Testing-Testing-Model-Separa_64AA/mocking.png](http://www.dotnetcurry.com/images/mvc/ASP.NET-MVC-Testing-Testing-Model-Separa_64AA/mocking.png)<!-- .element: style="font-size:25px" -->

note:
- bedeutet "vorgetäuscht"
- simulieren des verhaltens von realen Objekten, die sich schlecht im Unit Test einbinden lassen
- z. Bsp. Dateien, Daten, Uhrzeit
- Unit Tests sollen in beliebiger Reihenfolge ausgeführt werden können

---

# Ergebnisse & Probleme

note: 
- T: Fehler werden übersehen
    
- D: Warum Testen, das funktioniert
- D: Macht der Tests wirklich etwas?
- D: Code untestbar geschrieben
- D: Wer muss Tests schreiben? -> Tests sucken
- T: Externes Team ist schlecht
    Personalaufwand
    Testteam nervt -> Entwickler haben weniger Spaß
- T: Geringe Testabdeckung ist schlechter als gar keine Tests
    geben das gefühl man hätte etwas getestet, dass ist aber nicht wirklich so