# Assignment 1: Anderer Leute Code

Ziel dieses Assignments wird es sein, fremden Code zu kompilieren und danach zu testen. Um eine hinreichend große Codebasis zu haben, werden wir den Quelltext von Apache Tomcat verwenden. Damit zumindest ein gewisses Legacy-Gefühl aufkommt, nehmen wir eine Version, die fast 10 Jahre alt ist (6.0).


## Voraussetzungen

Tomcat wird mit dem Build-Werkzeug [Ant](https://ant.apache.org) gebaut. Dieses müssen Sie zuerst herunterladen und installieren. Installieren Sie es so, dass es im Pfad liegt und einfach durch Aufurf von `ant` gestartet werden kann.


## Tomcat herunterladen

Laden Sie von der Seite der Apache Foundation die Version 6.0.53 von [Tomcat](http://tomcat.apache.org) herunter und entpacken Sie diese.


## Tomcat bauen

Versuchen Sie Tomcat mit dem vorhandenen Build-Skript `build.xml` und Ant zu bauen. Wahrscheinlich müssen Sie Änderungen sowohl an `build.xml` als auch an den Build-Einstellungen in `build.properties.default` vornehmen, damit der Build durchläuft. Hierfür werden Sie ein grundlegendes Verständnis des Build-Vorgangs brauchen und den Aufbau der `build.xml` verstehen müssen. Schauen Sie sich die `build.xml` aufmerksam an, um die Funktionsweise abzuleiten. Hinweise finden Sie auch in der Datei `BUILDING.txt`.


## Tomcat starten

Wenn Sie die Klassen erfolgreich kompilieren konnten, versuchen Sie Tomcat zu starten. Gehen Sie hierzu in das Verzeichnis `output/build/bin` und starten Sie ihn mit `sh catalina.sh run`. Wenn alles geklappt hat, können Sie im Browser [http://localhost:8080](http://localhost:8080) aufrufen.


## Unit-Tests ausführen

Führen Sie die Unit-Tests für Tomcat aus. Diese starten Sie über das Target `test` im Build.

Es werden nicht alle Tests funktionieren. Entfernen Sie diejenigen Tests, die fehlschlagen.


## Code Basis in Eclipse importieren

Legen Sie ein Eclipse-Projekt an und fügen Sie den Quelltext von Tomcat hinzu. Wichtig ist, dass der Quellcode von Eclipse compiliert werden kann und Sie Tomcat aus Eclipse heraus starten können. Hierzu müssen Sie wahrscheinlich einige Bibliotheken in Eclipse einbinden und Einstellungen zur Java-Version vornehmen.

Wenn Sie erfolgreich waren, sollte sich Tomcat auch aus Eclipse heraus starten lassen. Hierzu müssen Sie die Hauptklasse finden. (Tipp: Schauen Sie in `catalina.sh` nach, ob Sie einen Hinweis finden). Beim Start werden einige Fehler geworfen, Tomcat sollte aber trotzdem funktionieren.
