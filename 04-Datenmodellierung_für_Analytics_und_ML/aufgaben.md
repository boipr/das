# Aufgabe 1

a)
Skizzieren Sie (vereinfacht) ein Star- und ein Snowflake-Schema für den folgenden Kontext:
Energieversorger mit Kunden, Zählpunkten, Tarifen und täglichen Messwerten.

Ergebnisformat: zwei logische Datenmodelle

b)
Beantworten Sie:
- Wo liegen die Vorteile des Star-Schemas für BI-Analysen?
- Wo liegen die Vorteile des Snowflake-Schemas aus technischer Sicht?
- Was ist mit „technisch sauberer, aber pflegeintensiver“ in diesem Zusammenhang gemeint?

Ergebnisformat: drei Listen mit stichpunktartigen Antworten

# Aufgabe 2

a)
Erläutern Sie in eigenen Worten, was ein zeitlich konsistenter Join ist.

Ergebnisformat: kurze stichpunktartige Erläuterung

b)
Sie haben zwei Tabellen:
- FAKT_VERBRAUCH (kunde_id, datum, tarif_id, ...) mit täglichen Messwerten
- DIM_TARIF (tarif_id, preis_kwh, ...) historisiert mit Gültigkeitszeiträumen

Schreiben Sie eine Abfrage, die für einen gegebenen Kunden und einen gegebenen Zeitraum den täglichen Verbrauch und die täglichen Kosten ausgibt.

Ergebnisformat: formlose Query

c)
Warum ist Historisierung (wie in dieser Aufgabe) eine Voraussetzung für reproduzierbare ML-Modelle?

Ergebnisformat: kurze stichpunktartige Erläuterung

# Aufgabe 3

a)
Beantworten Sie:
- Was ist der Unterschied zwischen Feature-Historisierung und Feature-Versionierung.
- Warum ist ein Feature Store eine Voraussetzung für Reproduzierbarkeit im ML?
- Wie hilft Lineage Tracking, die Verbindung zwischen Daten, Features und Modellen sicherzustellen.

Ergebnisformat: drei Listen mit stichpunktartigen Antworten

b)
Nennen Sie drei konkrete Maßnahmen, um Lineage Tracking im Analytical Stack umzusetzen.

Ergebnisformat: Liste mit stichpunktartigen Antworten

c)
Beantworten Sie:
- Warum gehört auch die Verknüpfung zu einer Versionsverwaltung für Dateien (git, MLflow, ...) zur vollständigen Lineage?
- Welche Vorteile hat Lineage Tracking für Fehleranalyse, Audits, Datenverantwortung?

Ergebnisformat: zwei Listen mit stichpunktartigen Antworten
