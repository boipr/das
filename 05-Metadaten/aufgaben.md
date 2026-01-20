# Aufgabe 1

Kontext: Onboarding für den Datensatz "raw_smartmeter_15min" mit Rohmessdaten.

a) Erstellen Sie einen Metadaten-Steckbrief für den Datensatz "raw_smartmeter_15min". Ein Metadaten-Steckbrief ist eine Auflistung der wichtigsten Metadaten eines Datensatz ("Datenblatt").

Orientieren Sie sich beim Metadaten-Steckbrief an den Fragen: Was? Wie? Woher? Wofür? Wer? Wie gut? Wann? (vgl. Folien)

Ordnen Sie jede Info einer der Kategorien fachlich, technisch, operational und Governance zu.

Ergebnisformat: Tabelle (Feld, Wert, Kategorie)

b) Definieren Sie ein „Minimum“ an Metadaten, ohne das der Datensatz nicht veröffentlicht werden darf (Definition of Done).

Ergebnisformat: Liste

# Aufgabe 2

Aufbauend auf der Lösung der vorherigen Aufgabe:

a) Mappen Sie fünf Felder auf Dublin-Core-Begriffe.

 Hilfestellung (Dublin Core „light“): `dc:title`, `dc:description`, `dc:creator`, `dc:publisher`, `dc:created`, `dc:modified`, `dc:identifier`, `dc:temporal`, `dc:spatial`, `dc:format`, `dc:rights`, `dc:source`

Ergebnisformat: Tabelle (Feld → Dublin-Core-Begriff)

b) Welche Metadaten verhindern in Ihrem Umfeld die meisten Fehlinterpretationen? Welche davon sollten automatisch kommen, welche bewusst manuell gepflegt werden?

Ergebnisformat: zwei Listen

# Aufgabe 3

Kontext:
- Die Smart-Meter-Daten werden für tägliche Lastprofile und zusammen mit Wetterdaten für Lastprognosen herangezogen.
- Die Smart-Meter liefern `value` ab nächstem Monat nicht mehr in kWh, sondern in Wh. Zusätzlich wird der Zeitstempel von UTC auf lokale Zeit umgestellt.

a) Zeichnen Sie einen Lineage-Graph.

Ergebnisformat: Graph mit Quell-/Zielsystemen, Datasets und Verarbeitungsschritten als Knoten

b) Erstellen Sie ausgehend vom Lineage-Graph eine Impact-Liste: Welche Artefakte, Teams, ... sind betroffen?

Ergebnisformat: Tabelle (betroffenes Artefakt, Begründung, Risiko, Owner, Maßnahme)

c) Erstellen Sie einen Automatisierungsplan: Welche Metadaten kommen aus welchen Quellen? Wie werden Sie jeweils für den Data Catalog erfasst?

Ergebnisformat: Tabelle (Metadaten, Quelle, Art der Erfassung, Aktualität)
