# JSON-Web-Token

## Modul ........

## Was ist ein JSON-Web-Token?

Ein JSON-Web-Token kurz JWT ist ein sicherer und Kompakter Token zum Übertragen von Ansprüchen zwischen zwei Parteien. JWT wird häufig für Authentifizierungen und Autorisierungen eingesetzt. JWT ist zwar einfach einzubauen und hat auch viele Vorteile und Nachteile wie zum Beispiel:

| Vorteile | Nachteile |
| -------- | --------- |




## Aufbau eine JWT
Ein JWT besteht aus drei Teilen dem Header, Payload und der Signatur. Beim Header, handelt es sich um ein JSON Element, welches beschreibt um welchen Token Typ es sich handelt und welche Signaturmethode verwendet wird. 

**Was befindet sich im Header:**

| Name | Feld | Beschreibung |
| ---- | ---- | ------------ |
| Type     | typ     |  Gibt den IANA Median Typ an, bedeutet, welche Art und Format hatben die Daten in diesem falle wäre es application/jwt             |
| Content Type | cty     | Wird nur benötigt, wenn das JWT im Payload ein anderes JWT mit sich führt ansonsten sollte man darauf verzichten.        |
| Algorithmus  | alg     | Definiert die Signaturmethode, welche zum einsatz kommt, Beispiel HMAC mit SHA-256 oder auch RSA mit SHA-256 |

**Was befindet sich im  Payload**
| Name | Feld | Beschreibung |
| ---- | ---- | ------------ |
|      |      |              |
|      |      |              |
|      |      |              |
|      |      |              |
|      |      |              |
|      |      |              |
|      |      |              |
|      |      |              |
|      |      |              |
|      |      |              |

**Was befindet sich in der Signatur**




## Wie erstelle ich ein JWT Token?

### Maven-Dependency

Füge in deinem pom.xml folgende Dependencies hinzu:

```xml
        <dependency>
            <groupId>io.jsonwebtoken</groupId>
            <artifactId>jjwt-api</artifactId>
            <version>0.11.5</version>
        </dependency>
        <dependency>
            <groupId>io.jsonwebtoken</groupId>
            <artifactId>jjwt-impl</artifactId>
            <version>0.11.5</version>
            <scope>runtime</scope>
        </dependency>
        <dependency>
            <groupId>io.jsonwebtoken</groupId>
            <artifactId>jjwt-jackson</artifactId>
            <version>0.11.5</version>
            <scope>runtime</scope>
        </dependency>
```

Auf [Maven Central](https://central.sonatype.com/) findest du die aktuellen Versionen zu jedem Artefact.

### Konfiguration von JWT

Im application.properties musst du JWT konfigurieren, dass ist ein Beispiel wie eine basic Konfiguration aussehen kann.

<img width="473" height="100" alt="image" src="https://github.com/user-attachments/assets/f44abba6-40a4-4e99-83ba-a5f41a8d7aa4" />

**jwt.secret:** 
Das Secret, das zur Signatur (nicht zur Verschlüsselung) eines Tokens verwendet wird. Dieses Secret darf niemals öffentlich zugänglich sein oder im Versions‑Repository(Bitbucket etc.) gespeichert werden. Wenn ein Angreifer das Secret kennt, kann er gültige Tokens erzeugen und so unberechtigten Zugriff erlangen.

**jwt.expiration:** 
Definiert die länge der Gültigkeit des Tokens die Dauer wird in Milisekunden angegeben im angegeben Beispiel, wäre das Token für eine Stunde gültig. Nach Ablauf der Zeit ist das Token wertlos und nicht mehr zugebrauchen.

**jwt.issuer:** 
Gibt an, welcher Dienst das Token ausgestellt hat. Ideal ist es eine eindeutige Bezeichnung, wie zum Beispiel eine URL oder ein aussagekräftiger String.

Dies soll eine grobe Idee geben, was für die Konfiguration benötigt wird, jedoch sieht eine solche Konfiguration in einer echte, profesionneller Anwendung deutlich anders aus.




## Wie validiere ich ein JWT Token?



## Alternativen zu JSON-Web-Token

