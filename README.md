# Explorative Datenanalyse – Veloverkehr

Dieses Repository enthält die **explorative Datenanalyse (EDA)** im Rahmen der
Projektarbeit im Modul **Statistik II**.

Die Analyse dient der **Plausibilitätsprüfung der Daten** und der Vorbereitung
der weiteren statistischen Auswertung (Zwischenpräsentation 2).

---

## 📊 Daten

### `data/data.csv` – Velodaten
Enthält hochfrequente Zeitreihendaten zu Fuss- und Veloverkehrszählungen.

Wichtige Variablen:
- `DATUM`: Zeitstempel (Datum und Uhrzeit)
- `FK_STANDORT`: Standort-ID der Zählstelle
- `VELO_IN`, `VELO_OUT`: Anzahl Velofahrten
- `FUSS_IN`, `FUSS_OUT`: Anzahl Fussgänger
- `OST`, `NORD`: Koordinaten der Zählstelle

Die Velodaten werden für die EDA auf **Tagesebene aggregiert**.

---

### `data/loc.csv` – Standortdaten
Enthält **statische Informationen zu den Zählstellen** (z.B. Name, ID, Koordinaten).

Diese Datei wird **nicht zeitlich analysiert**, sondern dient ausschliesslich dazu,
Zählstellen (z.B. *Station Langstrasse*) eindeutig zu identifizieren und zu lokalisieren.

---

## 📓 Notebook

- `explor_data.ipynb`:  
  Explorative Datenanalyse der Velodaten für die Station *Langstrasse*.
  Der Fokus liegt auf:
  - Plausibilität der Zeitreihe
  - Wochenend- und Saisonmustern
  - Eignung der Daten zur Bearbeitung der Hypothesen

> Hinweis: Das Notebook enthält bewusst **keine statistischen Modelle** und
> **keine Zeitreihen-Dekomposition**.

---

## ▶ Reproduzierbarkeit
- Alle Pfade sind relativ
- Das Notebook ist von oben nach unten ausführbar
- Es werden ausschliesslich Standard-Python-Bibliotheken verwendet
