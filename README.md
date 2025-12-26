# Analyse von Veloverkehrsdaten mit Zeitreihenmethoden

## Projektüberblick

In diesem Projekt wird der zeitliche Verlauf von Velofahrten an städtischen
Zählstellen analysiert. Ziel ist es, zentrale zeitliche Muster sowie den
Einfluss von Wetterbedingungen auf das Verkehrsaufkommen zu untersuchen.

Der Fokus liegt auf einer erklärenden Analyse mithilfe von Zeitreihenmethoden.
Im Vordergrund steht die statistische Überprüfung klar definierter Hypothesen,
nicht die kurzfristige Prognose.

---

## Datenbasis

Die Analyse basiert auf drei Datensätzen:

- **Velodaten**  
  Täglich aggregierte Zählwerte von Velofahrten an mehreren Standorten.

- **Standortdaten**  
  Metadaten zu den Zählstellen. Diese werden im Projekt lediglich zur
  Einordnung verwendet.

- **Wetterdaten**  
  Tagesdaten zu Temperatur, Niederschlagsmenge und Regendauer.

Alle Analysen erfolgen auf Tagesebene.

---

## Hypothesen

Im Projekt werden folgende Hypothesen untersucht:

**H1:**  
An Regentagen werden deutlich weniger Velofahrten gezählt.

**H2:**  
An Werktagen werden mehr Velofahrten gezählt als am Wochenende.

**H3:**  
Die Velofahrten weisen einen saisonalen Verlauf über das Jahr auf.

---

## Methodisches Vorgehen

### Explorative Analyse und Prophet

Zu Beginn wurde das Prophet-Modell eingesetzt, um Trend, saisonale Muster
und externe Einflussfaktoren wie Wetter gemeinsam abzubilden.
Aufgrund der begrenzten Datenbasis von nur einem Jahr erwies sich Prophet
jedoch als ungeeignet, um stabile saisonale Effekte zuverlässig zu schätzen.

Die Prophet-Analyse dient daher primär als explorativer Einstieg und
Motivation für einen alternativen Analyseansatz.

---

### Zeitreihen-Dekomposition mit STL

Als zentrales Analyseinstrument wird eine STL-Dekomposition verwendet.
Diese zerlegt die Zeitreihe der täglichen Velofahrten in:

- einen langfristigen Trend  
- eine wöchentliche saisonale Komponente  
- Residuen als kurzfristige Abweichungen  

Durch diese Zerlegung lassen sich verschiedene Effekte klar voneinander trennen
und gezielt den einzelnen Hypothesen zuordnen.

---

## Ergebnisse nach Hypothese

### H3: Saisonaler Verlauf über das Jahr

Der Trend der STL-Dekomposition zeigt einen deutlichen jahreszeitlichen Verlauf.
Die Anzahl der Velofahrten steigt vom Winter in die Sommermonate an und nimmt
im Herbst und Winter wieder ab.

Da nur ein Jahr an Daten vorliegt, kann keine wiederkehrende jährliche
Saisonalität identifiziert werden. Der beobachtete Trend stützt jedoch die
Annahme eines saisonalen Zusammenhangs und bestätigt Hypothese H3
im Rahmen der verfügbaren Daten.

---

### H2: Wochentagseffekte

Die wöchentliche Saisonalität wird anhand der saisonalen Komponente der
STL-Dekomposition analysiert.
Durch Aggregation dieser Komponente nach Wochentagen werden systematische
Unterschiede sichtbar.

Werktage weisen deutlich positive Abweichungen vom Wochenmittel auf,
während Samstag und insbesondere Sonntag klar darunter liegen.
Damit wird Hypothese H2 eindeutig bestätigt.

---

### H1: Einfluss von Regen

Zur Prüfung von Hypothese H1 werden die Residuen der STL-Dekomposition untersucht.
Diese repräsentieren kurzfristige Abweichungen, die weder durch den
langfristigen Trend noch durch das Wochentagsmuster erklärt werden.

Da Niederschlag in den vorliegenden Daten nahezu täglich auftritt und die
Niederschlagsmenge nur geringe Variation zeigt, wird ein Regentag über die
Regendauer operationalisiert.
Die Analyse zeigt einen signifikanten negativen Zusammenhang zwischen der
Regendauer und den STL-Residuen.

An Tagen mit längerer Regenperiode werden somit weniger Velofahrten beobachtet,
als aufgrund von Trend und wöchentlicher Saisonalität zu erwarten wäre.
Hypothese H1 wird damit bestätigt.

---

## Modellwahl und statistische Einordnung

Obwohl die ursprünglichen Velofahrten Zähldaten darstellen, werden in der
Wetteranalyse die STL-Residuen als Zielvariable verwendet.
Diese sind kontinuierliche Abweichungen vom Erwartungswert und können sowohl
positive als auch negative Werte annehmen.

Aus diesem Grund wird ein lineares Regressionsmodell eingesetzt.
Count-basierte Modelle wie die Poisson-Regression sind in diesem Kontext
nicht geeignet.

---

## Fazit

Die Analyse zeigt, dass Velofahrten stark durch zeitliche Muster geprägt sind.
Der langfristige Verlauf weist auf saisonale Einflüsse hin, während
Wochentagseffekte einen stabilen und dominanten Einfluss haben.

Wetterbedingungen wirken sich vor allem kurzfristig aus.
Dabei spielt die Dauer des Regens eine wichtigere Rolle als die reine
Niederschlagsmenge.

Die Kombination aus STL-Dekomposition und linearer Regression erweist sich als
geeigneter Ansatz für eine erklärende Zeitreihenanalyse und ermöglicht eine
klare und nachvollziehbare Hypothesenprüfung.

---

## Reproduzierbarkeit

Die gesamte Analyse ist im bereitgestellten Jupyter Notebook dokumentiert
und vollständig reproduzierbar.
Alle Schritte von der Datenaufbereitung über die Modellierung bis zur
Interpretation sind im Notebook nachvollziehbar kommentiert.
