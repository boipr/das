# Aufgabe 1

Betrachten Sie folgende Anwendungsfälle:
1. gesetzlich notwendige Reports (z. B. Energiebilanzen, MaKo-Reporting, Audit)
2. Rohdatenarchiv Smart Meter und Data Science Experimente (z. B. Anomalien, Prognosen)
3. Stoerungsanalyse ueber mehrere Domänen (Netzbetrieb, Kunden, IoT) mit Self-Service fuer Fachbereiche
4. ein Anwendungsfall aus Ihrem beruflichen Umfeld

Geben Sie für jeden Anwendungsfall an:
- grobe Einordnung entlang der Achsen zentral-föderiert, Governance-Self Service
- passende(s) Architektur-Archetypen
- kurze Begründung
- wichtigster Tradeoff


# Aufgabe 2

Erstellen Sie einen minimalen Data Contract für das Datenprodukt "Smart Meter Messwerte 15-Minuten". Oder alternativ für ein Datenprodukt aus Ihrem beruflichen Umfeld. 

Orientieren Sie sich beim Spezifizieren des Data Contracts an den Empfehlungen in den Folien.

Ergebnisformat: Liste

# Aufgabe 3

Kontext: gleiches Datenprodukt wie in der vorherigen Aufgabe.

a) Skizzieren Sie den Weg der Daten mit Hilfe eines FMC-Diagramms.

b) Markieren Sie das wichtigste Quality-Gate und nennen Sie typische Fehlerfälle, die dort abgefangen werden sollen.

c) Wählen Sie zwei Undercurrents und nennen Sie je eine konkrete Maßnahme.


## Aufgabe 4:

Kontext: Bei Ihrer Datenplattform greifen mehrere Teams direkt auf Rohdaten zu. Dadurch entstehen Probleme (z.B. inkonsistente Semantik, unterschiedliche Filterlogiken, wiederkehrende Diskussionen bei Audit/Reporting). Sie wollen architektonisch aufräumen und Datenprodukte etablieren.

Wie könnte eine Datenarchitektur aussehen, mit der das gelingt? Dokumentieren Sie als ADR:
- Titel
- Kontext
- Entscheidung
- Konsequenzen (positive und negative)
- offene Punkte
- nächste Schritte
