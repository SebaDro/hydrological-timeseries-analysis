# GI-Projekt KI SoSe 2021 - Hydrological Timeseries Analysis
Im Rahmen eines ersten kleineren Projekts sollen die erlernten Skills aus der ersten Lerneinheit vertieft werden. Hierzu
werden einige umfangreichere Zeitreihenanaylsen hydrologischer Messwerte eigenständig durchgeführt.

## Beschreibung
Die Teilnehmer sollen Fähigkeiten zur Analyse von Zeitreihen ausbauen, indem sie die aus der Einführungsveranstaltung
bekannten Data Science Bibliotheken ([Matplotlib](https://matplotlib.org/) und [pandas](https://pandas.pydata.org/))
selbständig anwenden, um Abfluss- und Niederschlagszeitreihen einiger ausgewählter Einzugsgebiete aus dem
[CAMELS-Dataset](./data/README.md) auszuwerten. Neben der Bestimmung von statistischen Kennwerten erfolgt außerdem die
Analyse zeitlicher Trends der hydrologischen Messwerte. Die Auswertung erfolgt in einer selbst einzurichtenden Data
Science Umgebung mit dem Python Paketmanager [conda](https://docs.conda.io/) und [Juypter Lab](https://jupyterlab.readthedocs.io/).
Dabei sollen in einem Jupyter Notebook die Auswertungsergebnisse angemessen visualisiert, analysiert interpretiert werden.

## Vorbereitung
### Einrichtung der Data Science Umgebung
Die Auswertung der Zeitreihen erfolgt unter Nutzung einiger Python Bibliotheken für Data Science. Nutzen Sie hierfür die
erstellte conda Umgebung aus der ersten Lehreinheit. Falls diese nicht mehr vorhanden sein sollte oder falls Sie diese
Übung in einer separaten Umgebung bearbeiten möchten, nutzen Sie die bereitgestellte _environment.yml_. Starten Sie
anschließend Jupyter Lab, um mit der Auswertung zu beginnen.
### Daten einlesen
Laden Sie die Niederschlags- und Abflusszeitreihen eines ausgewählten Einzugsgebiets ein. Die Daten finden Sie im
_./data_ Ordner. Nutzen Sie für das Einlesen das _dataio_ Modul im _scripts_ Package. Beachten Sie, dass einige der Werte
im Angloamerikanisches Maßsystem vorliegen und vor der Auswertung in eine sinnvolle Maßeinheit des metrischen Systems
umgewandelt werden sollten.

## Aufgaben
### 1 Statistische Kennwerte berechnen
Ermitteln Sie für das ausgewählte Einzugsgebiet die aus der Einführungsveranstaltung vorgestellten gewässerkundlichen
Hauptzahlen für den Abfluss in einen selbst gewählten Zeitraum (dieser sollte jedoch mindestens 10 Jahre betragen). Stellen Sie
diese tabellarisch dar.
### 2 Auswertung des zeitlichen Verlaufs von Messwerten
Stellen Sie den zeitlichen Verlauf des Niederschlags innerhalb eines Jahres für jeweils 6 unterschiedliche Jahre grafisch
dar. Nutzen Sie hierfür die Matplotlib Bibliothek und wählen Sie eine angemessene Form der Visualisierung. Führen Sie
dasselbe für den Verlauf der Abflussmengen separat durch. Lassen sich Regelmäßigkeiten im zeitlichen Verlauf der Niederschlags-
und Durchflussmengen innerhalb eines Jahres erkennen?
#### Optional
Stellen Sie auf ähnliche Weise den zeitlichen Verlauf der Abflussmengen für 6 unterschiedliche Jahre in einer
Summenlinie dar.
### 3 Intraannuelle Auswertung
Ermitteln Sie für den gewählten Zeitraum die monatlichen Durchschnittswerte für Abfluss und Niederschlag und visualisieren Sie
diese angemessen. Lassen sich monatliche Korrelationen zwischen den Niederschlags- und Abflussmengen erkennen?
### 4 Temporale Trendanalyse
Untersuchen Sie, ob sich für den Abfluss im gewählten Einzugsgebiet sowie für den Temperatur- und Niederschlagsverlauf
zeitliche Trends erkennen lassen. Führen Sie hierfür eine lineare Regression durch und visualisieren Sie die
Regressionsgrade mit Matplotlib. Nutzen Sie für die lineare Regression SciPy: https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.linregress.html
#### Optional
Stellen Sie für den Durchfluss die Ganglinie der höchsten jährlichen Abflüsse, einschließlich der Regressionsgrade
gemeinsam in einem Diagramm dar.
### 5 Korrelationsanalyse (Optional)
Untersuchen Sie inwiefern die Abflussmengen eines Tages mit den Niederschlagssummen vorangegangener Tage korrelieren. Bereiten
Sie hierfür die Niederschlags- und Abflusswerte eines wählbaren Zeitraums so auf, dass in einem DataFrame für jedes Datum
jeweils der aktuelle Abflusswert sowie die Niederschlagswerte der vorangegangenen n-Tage aufgeführt werden. Der DataFrame
würde dann in etwa wie folgt aussehen:  

| date       | discharge | prec_actual | prec_offset_1 | prec_offset_2 | ... |
|------------|-----------|-------------|---------------|---------------|-----|
| 2015-01-01 | 99.0      | 0.75        | 0.45          | 0.87          | ... |
| 2015-01-02 | 105.5     | 0.68        | 0.75          | 0.45          | ... |
| 2015-01-03 | 103.3     | 0.54        | 0.68          | 0.75          | ... |
| ...        | ...       | ...         | ...           | ...           |     |  

Eine paarweise Korrelationsmatrix kann anschließend mit pandas erstellt werden
(https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.corr.html).
Stellen Sie den (möglichen) Zusammenhang zwischen Abfluss und dem Niederschlag vorangegangener Tage in jeweils einem
Scatterplot dar.

