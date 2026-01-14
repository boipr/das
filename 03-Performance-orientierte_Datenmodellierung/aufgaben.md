# Aufgabe 1

Muster "Aggregat" anwenden.

## Kontext

Ein Energieversorger verwaltet Lieferverträge für Zählpunkte. Relevante Objekte:

- KUNDE `(kunde_id, name, adresse, kontaktprefs …)`
- ZAEHLPUNKT `(zaehlpunkt_id, adresse, netzgebiet …)`
- LIEFERVERTRAG `(vertrag_id, kunde_id, zaehlpunkt_id, tarif_id, start, ende, status …)`
- ABSCHLAGSPLAN `(vertrag_id, gueltig_ab, betrag, turnus …)`  
- RECHNUNG `(rechnung_id, vertrag_id, zeitraum_von, zeitraum_bis, summe, status …)`
- ZAHLUNG `(zahlung_id, vertrag_id, datum, betrag, referenz …)`  
- TARIF `(tarif_id, name, arbeitspreis_ct, grundpreis_eur …)`

Beispiele für fachliche Invarianten:
- Pro Vertrag gibt es zu einem Zeitpunkt genau einen aktiven Abschlagsplan.
- Eine Rechnung kann nur von „OFFEN“ → „BEZAHLT“ wechseln, wenn eine Zahlung verbucht wird.
- Nach Vertragsende (status = BEENDET) dürfen keine neuen Rechnungen erzeugt werden.

## Aufgabenstellung

a) Wählen Sie einen Aggregat-Kandidaten aus dem obigen Modell. Welcher Entitätstyp ist die Wurzel des Aggregats, welche weiteren Bestandteile gehören dazu? Welcher Schlüssel hält das Aggregat zusammen? Begründen Sie den Schnitt des Aggregats mit Blick auf Invarianten und die Transaktionsgrenze. (Bei Bedarf gerne weitere Invarianten für Ihre Argumentation ergänzen.)

Ergebnisformat:
- ein ER-Modell (vereinfacht, ohne Attribute) mit Kennzeichnung des Aggregats, der Bestandteile, des Schlüssels
- stichpunktartige Begründung, ggf. weitere Invarianten

b) Formulieren Sie zwei beispielhafte Transaktionen, die innerhalb der Aggregatgrenze bleiben.

Ergebnisformat: Transaktionen formlos (was wird gelesen, verändert, neu erzeugt)

c) Formulieren Sie eine Transaktion, die die Aggregatgrenze verletzt, z. B. indem sie einen Join/Update über mehrere Aggregate erzwingt oder Entitäten außerhalb des Aggregats mit einbezieht. Was bedeutet dieser Grenzübertritt für die Modellierung?

Ergebnisformat:
- Transaktion formlos
- stichpunktartige Begründung

# Aufgabe 2

Muster "Bounded Contexts" anwenden.

## Kontext

Die Fachverfahren eines Energieversorgers decken alle Anwendungsfälle ab, die vom Online-Vertragsschuss über die Erfassung von Messwerten bis hin zur Rechnungsstellung benötigt werden und einen konkreten Kundenbezug haben.

a) Definiere Sie drei Bounded Contexts und geben Sie für jeden davon an:
   - Welche Kern-Entitäten gehören hinein?  
   - Welche Keys/IDs sind dort „native“ (lokale Primärschlüssel)?  

Ergebnisformat: drei (vereinfachte) ER-Modelle mit den lokalen Primärschlüsseln

b) Wählen Sie einen konkreten Portal-Use-Case, für den Daten aus verschiedenen Bounded Contexts benötigt werden. Welche Daten liegen in welchem Bounded Context? Wo würde ein Cross-Context-Join entstehen, wenn man alles in einem Schema hält? Wie kann man das hier ohne Cross-Context-Join lösen?

Ergebnisformat: Use Case in einem Satz, Auflistung der zugehörigen Entitäten/Attribute, Cross-Context-Join (formlos)

c) Entscheiden Sie für einen konreten Use Case, ob der zugehörige Datenfluss eher ACID oder eher eventual consistency braucht. Fachliche Begründung.

Ergebnisformat: Ergebnis mit stichpunktartiger Begründung

# Aufgabe 3

Muster "Sharding" anwenden.

## Kontext

Die Smart Meter Ihres Unternehmens liefern alle 15 Minuten einen Messwert pro Zählpunkt.

Datenformat: ZAEHLER_WERTE `(zaehlpunkt_id, ts, kWh, …)`  

Beispiele für Abfragen:
- die letzten 96 Werte (24h) für einen Zählpunkt (häufig, Portal) 
- summierter Tagesverbrauch pro Netzgebiet über alle Netzgebiete (täglich, Monitoring)
- Verbrauch für Vertrag X im letzten Monat (monatlich, Vertrieb)

## Aufgabenstellung

a) Wählen Sie eine Sharding-Strategie. Geben Sie den Shard-Key bzw. die Shard-Keys an. Begründen Sie mit Blick auf Lokalität von Abfragen und potentielle Hotspots.

Ergebnisformat: Shard-Keys, stichpunktartige Begründung

b) Konkretisieren Sie zwei der obigen Abfragen. Welcher Shard, welche Shards sind betroffen?

Ergebnisformat: formlose Queries, jeweils Angabe der betroffenen Shards

c) Geben Sie eine Abfrage an, die häufig ausgeführt wird und über ein Shard hinausgeht. Wie kann der Shard-übergreifende Zugriff vermieden werden?

Ergebnisformat: formlose Query, Benennung und stichpunktartige Beschreibung des Ansatzes
