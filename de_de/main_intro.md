# YForm: Einführung

## Formulare im Frontend

Das AddOn YForm dient vor allem zur Generierung von Formularen im Frontend. Formulare sind komplex und ziehen oft umfangreiche Nacharbeit mit sich. YForm versucht, durch flexible Verzahnung verschiedener Komponenten möglichst viele dieser Aufgaben zu übernehmen.

YForm enthält nicht nur alle gängigen Formular-Feldtypen, sondern stellt auch vielfältige Validierungen bereit, Funktionen zum Versand von E-Mails sowie Aktionen, die zum Beispiel Daten in eine Datenbank schreiben oder Weiterleitungen ausführen.

Dazu installiert YFom ein Modul namens [YForm-Formbuilder](yform_formbuilder.md). Nach einer allgemeinen Einführung in den [Formbuilder]() werden die zahlreichen Optionen aller [Values](), [Validates]() und [Actions]() erklärt.

Das Erstellen von [E-Mail-Templates]() wird in einem eigenen Kapitel beschrieben.

## Tabellenverwaltung im Backend

YForm kann aber nicht nur Formulare für das Frontend generieren sowie Formulareingaben per E-Mail versenden oder in eine Datenbank speichern.

Der Admin kann mit Hilfe des Table Managers auch Datenbank-Tabellen "zusammenklicken" und diese - ergänzt z.B. durch Validierungen - im Backend samt Eingabemaske zur Verfügung stellen. Diese automatisch erzeugten Daten-Verwaltungen können dann wiederum den Code für ein dazu passendes Frontend-Formular generieren.