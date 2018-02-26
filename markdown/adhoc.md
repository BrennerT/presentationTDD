# Klassischer Ad Hoc Ansatz

Was ist der klassische Ansatz?

---

## Welche Arten von Tests gibt es?

- Unit
- Integration
- System

-- 

## Unit Tests

```php
    public class Calculator{
        
        public static int Add(int x, int y){ 
            return x + y; 
        }
        
        public static int Divide(int dividend, int divisor){ 
            return dividend / divisor;
        }

    }
``` 

-- 

## Unit Tests

```php
    public void AddTest(){
        int x = 1;
        int y = 2;
        int expected = 3;
        int actual = Calculator.Add(x, y);
        Assert.AreEqual(expected, actual);
    }
```

note: 
Code Example
Testen ob eine Einheit ihre Funktion erfüllt
Unit Tests sollen die Ergebnisse anderer Unit Tests nicht beeinflussen
Was ist eine Unit?

--

## Integration Test

--

## System Test

--

## End-to-End Test

Prüfen ob die UI sich so verhält wie es erwartet wird.

--

## Black Box vs. White Box

![This should be an image with black box and white box comparison](../img/blackbox und whitebox tests.jpg)

note: 
Whitebox: Einblick in das zu testende Programm ist vorhanden, Entwicklersicht
Blackbox: Kein Einblick in das getestete Programm, Anwendersicht 
Sollten Tests nach Black- oder White-Box Prinzip verarbeitet werden?
Im TDD werden zu Beginn Blackbox Tests geschrieben

---

# Frameworks

note:
Implementieren von automatisierten Tests
Programmiersprachen abhängig

-- 

## Automatisierte Tests 

note:
Ziel: Entscheidung ob ein Fehler im Code entstanden ist auf Knopfdruck 
schneller Überblick ob durch Codeänderungen Fehler im Programm entstehen
erleichtern das Testen in Druckphasen eines Projektes

-- 

## JUnit

- Jede Klasse erhält eine Testklasse 
- Annotation @Test zum kennzeichnen eines Tests

note: 
Java

-- 

## Jasmin

Tests schreiben:

describe: suit
it: spec
expect: matcher

note: 
JavaScript

-- 

## Property Based Testing

---

# Pattern

-- 

## Mocks

Wozu braucht man die?

---

# Ergebnisse & Probleme

- Fehler werden übersehen
- Warum Testen, das funktioniert
- Macht der Tests wirklich etwas?
- Code untestbar geschrieben
- Wer muss Tests schreiben? -> Tests sucken
- Externes Team ist schlecht
- Geringe Testabdeckung ist schlechter als gar keine Tests