# Aufgabe 1: Fit for use Anforderungen in Metriken und Reaktionen übersetzen

Kontext: Sie verantworten ein Data Product für die Monatsabrechnung. Die Abrechnung basiert auf Zählerständen und Verträgen.

a) Nennen Sie drei Stakeholder, die diese Daten nutzen, und beschreiben Sie kurz deren Perspektive (Owner, Consumer, On-Call oder vergleichbar).

b) Formulieren Sie drei "fit for use"-Anforderungen für die Abrechnung so, dass diese messbar sind.

c) Leiten Sie daraus fünf SLIs und SLOs ab.

d) Legen Sie pro Metrik eine Reaktion fest (stop, quarantine, alert, ticket). Begründung.

# Aufgabe 2
Wählen Sie drei der folgenden Tabellen aus, wenden Sie Data-Profiling (manuell) darauf an und stellen Sie typische Auffäligkeiten heraus.

Ergebnisformat: Liste mit betroffenen Tabelle(n)/Spalte(n)/Zeile(n), Regeltyp, mögliche Ursache


### Entitätstyp KUNDE

| KundeID | Vorname | Nachname | Straße      | Hnr | PLZ   | Ort           | Email                       |
|--------:|---------|----------|-------------|----:|------:|---------------|-----------------------------|
| 100101  | Hannah  | Schulz   | Wiesenweg   | 14  | 38100 | Braunschweig  | hannah.schulz@example.net   |
| 100102  | Hannah  | Schulz   | Wiesenweg   | 14  | 38100 | Braunschweig  | hannah.schulz@example.net   |
| 100103  | Omar    | Yilmaz   | Lange Str.  | 22  | 50667 | Köln          | o.yilmaz@web.de             |
| 100104  | Lea     | Kovac    | Ringstraße  | 5   | 04109 | Leipzig       | ""                          |
| 100105  | Demo    | Account  | Musterallee | 1   | 00000 | Musterstadt   | demo@local                  |
| 100106  | Sven    | Krüger   | Hauptplatz  | 9   | 70173 | Stuttgart     | <NULL>                      |
| 100107  | Nina    | Peters   | Feldrain    | 3   | 38100 | Braunschweig  | n/a                         |

### Entitätstyp VERTRAG

| VertragsID | KundeID | Tarif | ZTyp   | Ableseart | Von        | Bis        | Zustand |
|-----------:|--------:|------:|--------|-----------|------------|------------|---------|
| C81001     | 100101  | T1    | SMART  | REMOTE    | 2024-04-15 | NULL       | AKTIV   |
| C81002     | 100103  | T2    | ANALOG | MANUELL   | 2025-03-01 | 2025-03-20 | BEENDET |
| C81003     | 100104  | T1    | ANALOG | E-MAIL    | 2019-09-01 | NULL       | BEENDET |
| C81004     | 199999  | T3    | SMART  | REMOTE    | 2025-06-01 | 2025-12-31 | AKTIV   |
| C81005     | 100105  | T1    | SMART  | MANUELL   | 2026-02-01 | 2026-01-31 | AKTIV   |
| C81006     | 100106  | T2    | ANALOG | MANUELL   | 2025-11-15 | NULL       | AKTIV   |

### Entitätstyp RECHNUNG

| RNr           | VertragsID | Von        | Bis        | Betrag |
|---------------|------------|------------|------------|-------:|
| INV-2026-00421| C81001     | 2026-03-01 | 2026-03-31 |  79.90 |
| INV-2025-00088| C81002     | 2025-03-01 | 2025-03-31 |  39.10 |
| INV-2025-07110| C81004     | 2025-07-01 | 2025-07-31 | 110.00 |
| 2025/09/77    | C81001     | 2025-11-01 | 2025-11-30 | 118.45 |
| INV-2026-00422| C81001     | 2026-04-01 | 2026-04-30 |  -7.50 |
| INV-2025-09999| C99999     | 2025-10-01 | 2025-10-31 |  55.00 |

### Entitätstyp RECHNUNGSPOSITION

| RNr            | Pos | Betrag |
|----------------|----:|-------:|
| INV-2026-00421 | 1   |  19.95 |
| INV-2026-00421 | 2   |  59.95 |
| INV-2025-00088 | 1   |  60.00 |
| INV-2025-00088 | 2   |  40.00 |
| INV-2025-07110 | 1   | 110.00 |
| 2025/09/77     | 1   | 118.45 |
| INV-2026-00422 | 1   |  -7.50 |
| INV-2025-09999 | 1   |  55.00 |

### Entitätstyp MESSUNG

| MessungID | ZaehlerID | Timestamp           |   kWh |
|----------:|-----------|---------------------|------:|
| MS101     | ZM1001    | 2026-03-10 00:08:11 | 45012 |
| MS102     | ZM1001    | 2026-03-11 00:09:05 | 45025 |
| MS103     | ZM1001    | 2026-03-12 00:10:44 | 45020 |
| MS104     | ZM1001    | 2026-03-14 00:08:59 | 45190 |
| MS201     | ZM1002    | 2026-03-12 00:10:00 |  8800 |
| MS202     | ZM1002    | 2026-03-13 00:10:00 |  8803 |
| MS301     | ZM1003    | 2026-02-01 00:10:00 |     0 |
| MS302     | ZM1003    | 2026-02-02 00:10:00 |     0 |
| MS303     | ZM1003    | 2026-02-03 00:10:00 |     0 |

### Entitätstyp ZAEHLER

| ZaehlerID | AnschlussID | Zustand    | DemontiertAm | NaechsteInspektion |
|----------:|-------------|------------|--------------|--------------------|
| ZM1001    | N30001      | AKTIV      | NULL         | 2026-09-30         |
| ZM1002    | N30001      | DEMONTIERT | 2025-11-30   | NULL               |
| ZM1003    | N39999      | AKTIV      | 2025-12-05   | 2026-10-15         |
| ZM1004    | N38888      | DEMONTIERT | NULL         | 2026-04-20         |

### Entitätstyp ANSCHLUSS_EVENT

| AnschlussID | Timestamp           | Zustand     |
|-------------|---------------------|-------------|
| N2001       | 2025-02-10 09:00    | GEPLANT     |
| N2001       | 2025-02-25 08:00    | AKTIV       |
| N2001       | 2025-06-05 17:00    | DEAKTIVIERT |
| N2001       | 2025-06-06 09:30    | AKTIV       |
| N2002       | 2025-05-12 10:00    | AKTIV       |
| N2003       | 2025-08-01 12:00    | GEPLANT     |
| N2003       | 2025-07-31 18:00    | BEENDET     |


# Aufgabe 3

Kontext:
Sie betreiben eine Pipeline für Messdaten (z. B. 15-Minuten-Werte) mit folgenden Tabellen:

```
MESSUNG (messung_id, zaehler_id, messzeitpunkt, kwh, qualitaetskennzeichen)
ZAEHLER (zaehler_id, anschluss_id, status, von_ts, bis_ts)
ANSCHLUSS (anschluss_id, status, status_ts)
VERTRAG (vertrags_id, anschluss_id, von, bis, tarif)
RECHNUNG (rnr, vertrags_id, von, bis, betrag)
```

Entwerfen Sie ein kleines, aber robustes Regelset, das alle fünf Regeltypen abdeckt.

Ergebnisformat: Liste mit Regeln (kurze Beschreibung, formlose Abfrage, Reaktion, Ort der Prüfung mit Begründung)
