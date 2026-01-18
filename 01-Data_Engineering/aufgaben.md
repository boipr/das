# Aufgabe 1

Bei dieser Aufgabe geht es darum, den Data Engineering Lifecycle im Kleinen zu durchlaufen.

Grundlage für diese Aufgabe sind diese Daten (`orders.csv`):

```
order_id,customer,product,qty,price
1001,Alice,Book,1,12.99
1002,Alice,Pen,3,1.50
1003,Bob,Book,2,12.99
1004,Carol,Notebook,1,5.90
1005,Bob,Pen,5,1.50
```

1. Schreiben Sie ein kleines Skript (z.B. in Python), das folgende Schritte ausführt:
    + Daten einlesen und in einer Tabelle ablegen, auf die mit SQL zugegriffen werden kann
    + folgende Information ermitteln:
        - Gesamtumsatz pro Kunde, absteigend sortiert
        - Top-Produkt nach Umsatz, absteigend sortiert
    + diese Resultate als Datenframes ablegen

2. Ordnen Sie die Bestandteile Ihres Codes den Aktivitäten des Data-Engineering-Lifecycles zu.

3. Erläutern Sie den Aufbau Ihrer Lösung mit den Begriffen aus den Folien zu Data Engineering.

Bei der Bearbeitung dieser Aufgabe sind ggf. folgende Python-Module hilfreich:

- `pandas`
- `duckdb`

# Aufgabe 2

Grundlage für diese Aufgabe ist Ihre Lösung zur vorherigen Aufgabe.

1. Definieren Sie ein Schema zur Validierung der Daten (Datentypen, Pflichtfelder, Wertebereiche), insbesondere:
    - qty > 0, price ≥ 0
	- order_id eindeutig
	- customer, product nicht leer
2. Ergänzen Sie Ihr Skript um die Schema-Validierung und stellen Sie sicher, dass nur gültige Eingabedaten verarbeitet werden.
3. Ergänzen Sie Ihr Skript um einen strukturierten Datenqualitätsbericht, z.B. in Form eines Datenframes, aus dem für jede Regel hervogeht, welche Prüfungen zu welchen Ergebnissen geführt haben.

Beispiel-Dateien zum Testen Ihrer Lösung:
```
order_id,customer,product,qty,price,order_ts
1006,Alice,Notebook,2,5.90,2024-01-12T10:15:00
1007,Dave,Book,1,13.49,2024-01-13T09:02:00
1003,Bob,Book,3,12.99,2024-01-14T12:30:00
```

```
order_id,customer,product,qty,price
1006,Alice,Notebook,-1,5.90
1006,Dave,Book,1,13.49
,Bob,Book,0,12.99
1007,Carla,Book,1,13.49
1008,Bob,Pencil,7,5.23
```

# Aufgabe 3

Wählen Sie aus Ihrem beruflichen Umfeld ein Quellsystem (z.B. Smartmeter-Messdaten), die technischen Details für Ingestion (z.B. CSV-Dateien, API, Events) und einen Konsumenten (z.B. BI, ML, fachliches Ziel). Definieren Sie davon ausgehend ein geeignetes Datenprodukt.

Ergebnisformat: Name des Datenprodukts, Auflistung aller relevanten Eigenschaften

Skizzieren Sie für dieses Datenprodukt Ingest, Transform, Serve, Storage. Gehen Sie dabei insbesondere auch auf die Wahl der Datenarten, Speicherformen und Schnittstellen ein.

Ergebnisformat: Schaubild + Beschreibung, aus denen die Aufgaben/Tätigkeiten der jeweiligen Bestandteile und die Kommunikation zwischen diesen hervorgeht.


# Aufgabe 4

Ordnen Sie Ihr berufliches Umfeld in das Datenreife-Raster aus den Folien ein:
1. Starting with Data
2. Scaling with Data
3. Leading with Data

Woran machen Sie das fest?

Ergebnisformat: Name des Reifegrads, stichpunktartige Begründung zur Einordnung gemäß den Punkten Fokus und Risiken

Beantworten Sie dann:
- Was sind aktuell die TOP3 Painpoints?
- Was ist aktuell der schwerwiegendste Engpass?
- Was wären die nächsten 2-3 wirksamsten Schritte?

Ergebnisformat: je Frage eine Auflistung mit stichpunktartigen Beschreibungen
