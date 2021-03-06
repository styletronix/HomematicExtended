[![SDK](https://img.shields.io/badge/Symcon-PHPModul-red.svg)](https://www.symcon.de/service/dokumentation/entwicklerbereich/sdk-tools/sdk-php/)
[![Version](https://img.shields.io/badge/Modul%20version-3.12-blue.svg)]()
[![License](https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-green.svg)](https://creativecommons.org/licenses/by-nc-sa/4.0/)  
[![Version](https://img.shields.io/badge/Symcon%20Version-5.1%20%3E-green.svg)](https://www.symcon.de/forum/threads/30857-IP-Symcon-5-1-%28Stable%29-Changelog)
[![Check Style](https://github.com/Nall-chan/HomematicExtended/workflows/Check%20Style/badge.svg)](https://github.com/Nall-chan/HomematicExtended/actions) [![Run Tests](https://github.com/Nall-chan/HomematicExtended/workflows/Run%20Tests/badge.svg)](https://github.com/Nall-chan/HomematicExtended/actions)  
[![Spenden](https://www.paypalobjects.com/de_DE/DE/i/btn/btn_donate_SM.gif)](../README.md#6-spenden) 

# HomeMatic RemoteScript Interface  <!-- omit in toc -->
   Native Schnittstelle zur CCU, um HomeMatic-Scripte durch die CCU ausführen zu lassen.  
   Direkte Rückmeldung der Ausführung durch einen Antwortstring im JSON-Format.  

## Dokumentation <!-- omit in toc -->

**Inhaltsverzeichnis**

- [1. Funktionsumfang](#1-funktionsumfang)
- [2. Installation](#2-installation)
- [3. Einrichten der Instanzen in IP-Symcon](#3-einrichten-der-instanzen-in-ip-symcon)
- [4. Statusvariablen und Profile](#4-statusvariablen-und-profile)
- [5. PHP-Befehlsreferenz](#5-php-befehlsreferenz)
- [6. Lizenz](#6-lizenz)

## 1. Funktionsumfang

   Dies Instanz ermöglicht es eigene Homematic-Scripte zur CCU zu senden.  
   Des weiteren wird die Rückgabe der Ausführung an den Aufrufer zurück gegeben.  
   So kann z.B. per PHP-Script in IPS ein dynamisches Homematic-Script als String erstellt werden,  
   und die erfolgte Ausführung ausgewertet werden.  


## 2. Installation

Dieses Modul ist Bestandteil der [HomeMaticExtended-Library](../).  


## 3. Einrichten der Instanzen in IP-Symcon


![Instanzen](../docs/HMExtendedInstanzen.png)  
   Unter Instanz hinzufügen ist das Gerät 'HomeMatic RemoteScript Interface' unter dem Hersteller 'HomeMatic' zu finden.  
   Nach dem Anlegen der Instanz sollte als übergeordnetes Gerät schon der HomeMatic Socket ausgewählt sein.  
   Existieren in IPS mehrere Homematic Socket, so ist der auszuwählen, an welche CCU die Scripte gesendet werden sollen.  

**Konfigurationsseite:**  

  Es gibt keine konfigurierbaren Parameter.  

## 4. Statusvariablen und Profile  

   Es werden keine Statusvariablen und Profile angelegt.  

## 5. PHP-Befehlsreferenz

   ```php
    string HM_RunScript(int $InstantID /*[HomeMatic RemoteScript Interface]*/,string $Script)
```
   **Beispiel:**

   Abfrage der Uhrzeit und Zeitzone von der CCU:
```php
    $HMScript = 'Now=system.Date("%F %T%z");' . PHP_EOL  
              . 'TimeZone=system.Date("%z");' . PHP_EOL;   
    $HMScriptResult = HM_RunScript(12345 /*[HomeMatic RemoteScript Interface]*/, $HMScript);  
    var_dump(json_decode($HMScriptResult));  
```

## 6. Lizenz

  [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/)  
