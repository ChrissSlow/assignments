# Assignment 3: Architektur-Archäologie

Ziel des Assignments ist es, die grobe Architektur von Tomcat zu analysieren und zu dokumentieren. Am Ende sollten Sie einen Überblick haben, der es Ihnen erlaubt, sich im Code von Tomcat zurecht zu finden und eventuell Änderungen daran vorzunehmen.


## Indiana Jones

Versuchen Sie die Architektur von Tomcat zu ergründen. Von besonderem Interesse ist, wie ein Request durch den Server läuft und verarbeitet wird, da dies ein Ablauf ist, in den wir später vielleicht eingreifen wollen. Außerdem ist das Zusammenspiel der Klassen und die Paketstruktur von Interesse, damit Sie verstehen, welche Aufgaben welche Bereiche des Servers haben.

Den *Ablauf eines Requests* können Sie am besten mit einem Debugger herausfinden, d.h. indem Sie eine eingehende Anfrage durch den Server verfolgen und entsprechend notieren, wie der Ablauf ist.

Die *grundlegende Struktur* lässt sich gut aus den Quelltexten extrahieren, indem Sie die `import`-Statements der Klassen anschauen. Diese Struktur können Sie mit Werkzeugen wie _graphviz_ visualieren. Schauen Sie im Internet, ob Sie noch andere Werkzeuge finden können, um die Aufgabe zu erledigen. Bei der Analyse der Abhängigkeiten wollen Sie möglicherweise die Standardbibliothek (`java.*`) ignorieren, damit . Wichtige Werkzeuge für die Analyse der Quelltexte sind `sed` und `grep`, die Sie sich ansehen sollten.

```shell
echo "digraph {" > test.dot ; grep -R "^import" * | sed -E "s/\//./g" | \
sed -E "s/\.java//g" | sed -E "s/\.\*//g" | sed -E "s/import //g" | \
grep -v ":java" | grep -v ":javax" | sed -E "s/;//g" | sed -E "s/:/ -> /" | \
grep -v "\.properties" | sed -E "s/\./_/g" | sed -E "s/_[A-Z].* ->/ ->/g" | \
sed -E "s/-> ([a-z_]*)_[A-Z][a-zA-Z]*/-> \1/g" | sed -E "s/org_apache_//g" | \
grep -v "juli_logging" | grep -v "tomcat_util" | grep -v "cataline_util" | \
sort | uniq >> test.dot ; echo "}" >> test.dot ; \
dot -Tpdf test.dot > test.pdf
```

## Tomcat einchecken

Nach der letzten Stunde sollten Sie einen lauffähigen Tomcat haben. Dafür mussten Sie möglicherweise Änderungen an der `build.xml` und anderen Dateien machen. Sichern Sie diesen Stand, indem Sie die Quelltexte unter Versionsverwaltung (git) stellen und in das GitHub-Repository Ihrer Gruppe committen. Legen Sie hierfür ein Verzeichnis `tomcat` in Ihrem Repository an.


## Abgabe

_Abgabe_: Dokumentieren Sie die von Ihnen gefundene Architektur und checken Sie die Ergebnisse in das GitHub-Repository Ihrer Gruppe im Verzeichnis `documentation` ein. Wählen Sie eine adäquate Darstellung (Text/Diagramm) für die Ergebnisse.
