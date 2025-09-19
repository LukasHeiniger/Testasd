# JSON-Web-Token

## Modul ........

## Was ist ein JSON-Web-Token?

Ein JSON-Web-Token, kurz JWT, ist ein sicherer und kompakter Token, der dazu dient, Ansprüche zwischen zwei Parteien zu übertragen. Der Einsatzbereich von JWT umfasst häufig Authentifizierungen und Autorisierungen. 

## Aufbau eines JWT
Ein JWT ist in drei Segmente unterteilt, nämlich Header, Payload und Signatur. Der Header ist ein Element des JSON-Formats, das den Typ des Tokens sowie die verwendete Signaturmethode beschreibt. Im Payload sind die Claims enthalten, die Aufschluss über die Gültigkeitsdauer des Tokens geben, das Datum seiner Ausstellung sowie weitere relevante Informationen. In der Signatur werden der codierte HEADER und die codierte Nutzlast durch einen geheimen Schlüssel (SecretKey) sowie den im Header angegebenen Signaturalgorithmus signiert.

### Was befindet sich im Header?

| Name | Feld | Beschreibung |
| ---- | ---- | ------------ |
| Type     | typ     |  Gibt den IANA Median Typ an, bedeutet, welche Art und Format hat die Daten in diesem falle wäre es application/jwt             |
| Content Type | cty     | Wird nur benötigt, wenn das JWT im Payload ein anderes JWT mit sich führt, ansonsten sollte man darauf verzichten.        |
| Algorithmus  | alg     | Definiert die Signaturmethode, welche zum einsatz kommt, Beispiel HMAC mit SHA-256 oder auch RSA mit SHA-256 |

```JSON

{
  "alg": "HS256",
  "typ": "JWT"
}

```

### Was befindet sich im  Payload?
| Name | Feld | Beschreibung |
| ---- | ---- | ------------ |
| Issuer     | iss     | Beschreibt den Austeller des Tokens             |
| Subject     |  sub    | Beschreibt, für welches Objekt die Claims gelten, zum Beispiel User mit bestimmter Mail|
| Issued At     | ita     | Zeit, ab welcher das Token ausgestellt worden ist.|
| Expiration Time     |exp      | Zeit, ab welcher das Token die gültigkeit verliert.|


```JSON
{
  "iss": "LoginService",
  "sub": "test@mail.ch",
  "iat": 1758270616,
  "exp": 1758274216
}

```

**Beachte, dass dies nur ein Beispiel ist, ein JWT Token kann im Payload weitere Felder beinhalten, diese sind aber für den Anfang aussreichend.**


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

### Erstellen einer JWT-Class

<img width="682" height="657" alt="image" src="https://github.com/user-attachments/assets/62e017de-fc6e-4a03-9400-45385b7a3844" />

## Wie validiere ich ein JWT Token?

https://www.jwt.io/

Auf dieser Webseite kannst du deinen erstellten Token genauer anschauen und dir mit deinem Secret auch einen neuen Funktionstüchtiges Token erstellen.

<img width="1497" height="840" alt="image" src="https://github.com/user-attachments/assets/0a586dd2-4aa3-473f-9cf7-c7cf42abddc6" />
