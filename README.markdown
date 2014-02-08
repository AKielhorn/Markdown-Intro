Eine deutschen Einführung in Markdown (pandoc Dialekt)

Mit Beispieldatei und Makefile zur Konvertierung in diverse Format.
Für diejenigen, die kein Make auf ihrem Rechner haben gibt es
eine Sammlung von Kommandozeilen, die man einfach kopieren und
in der Shell bzw. Eingabeaufforderung einfügen kann.

Außerdem 3 LaTeX-templates mit Optimierungen für deutsche Texte als
Basis für eigene Experimente.

Seit Pandoc Version 1.9.4 ist default-de.latex nicht mehr notwendig,
da default-latex über Variablen auf Deutsch umgestellt werden kann
und fontenc für die Anführungsstriche unten enthält.

    -V lang=ngerman

Eine separate Datei für KOMA-Script und report ist ebenfalls nicht
mehr notwendig.

    -V documentclass=report
    -V documentclass=scrrprt

Pandoc 1.10 Erweiterungen eingepflegt:

 -  Neues Template für 1.10
 -  Beschreibung Pipe-Tabelle
 -  Beschreibung Zeilenblock
 -  Syntax highlight Beschreibung erweitert
 -  Römische Zahlen in Aufzählungen.

Pandoc 1.12 Erweiterungen eingepflegt:

 - Neues Template für 1.12
 - Booktabs für Tabellen
 - YAML für Variablen und Metadaten
   (Literaturverzeichnis, Abstract, epub)

