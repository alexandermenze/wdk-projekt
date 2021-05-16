# klauswert
> Ein Modul zur Klausurauswertung


## Module einbinden

```
# exports
import pandas as pd
import yaml

```

## Klasse "Klauswert"

### Standard Konfiguration

```
# exports
stdConfig = '''headerPC: 4
pointCols: "A:L"
headerMC: 1
markCols: "N:O"
headerMP: 1
mxPointCols:  "A:L"
'''
```

```
pbx2020 = Klauswert('rawData/KlausurPunkte.xlsx')

```

```
my_show_doc(Klauswert)
```


<h2 id="Klauswert" class="doc_header"><code>class</code> <code>Klauswert</code><a href="" class="source_link" style="float:right"></a></h2>

> <code>Klauswert</code>(**`fname`**, **`configTxt`**=*`'headerPC: 4\npointCols: "A:L"\nheaderMC: 1\nmarkCols: "N:O"\nheaderMP: 1\nmxPointCols:  "A:L"\n'`*)

Aufgabe der Klasse: Klausurauswertung \
Konfiguration: YAML-Text (stdConfig)\
Ausgangslage: .xlsx-Datei mit einer Zeile je Student. In den Spalten  
config['pointCols'] stehen die Punkte für die jeweiligen Aufgaben. In den Spalten
config['markCols'] ist die Notenverteilung ersichtlich


```
pbx2020 = Klauswert('rawData/KlausurPunkte.xlsx')
print(pbx2020.getConfig()['headerMC'])
```

    1
    

### Die Funktionen

```
my_show_doc(Klauswert.getAllData)
```


<h4 id="Klauswert.getAllData" class="doc_header"><code>Klauswert.getAllData</code><a href="__main__.py#L42" class="source_link" style="float:right"></a></h4>

> <code>Klauswert.getAllData</code>()

Aufgabe: gesamten Dataframe zurück geben.


```
display(Markdown(pbx2020.getAllData().head().to_markdown()))
```


|    | Name        |   A1 |   A2 |   A3 |   A4 |   A5 |   A6 |   A7 |   A8 |   A9 |   A10 |   A11 |   sumP |
|---:|:------------|-----:|-----:|-----:|-----:|-----:|-----:|-----:|-----:|-----:|------:|------:|-------:|
|  0 | Alexander   |  4   |  6   |    4 |  7   | 11   |  4   |    4 |  5   |  5   |   4.5 |  10.5 |   65   |
|  1 | Andre       |  4   |  3.5 |    4 |  8   | 20.5 |  4   |    3 |  3.5 |  3.5 |   3   |   4   |   61   |
|  2 | Celine      |  4   |  3.5 |    2 |  7   | 13.5 |  5   |    5 |  5   |  4.5 |   5   |  11   |   65.5 |
|  3 | Christian   |  3.5 |  2.5 |    1 |  6.5 | 17   |  2.5 |    5 |  5   |  4   |   6   |   4   |   57   |
|  4 | Christopher |  3.5 |  0.5 |    0 |  4   |  7.5 |  0   |    0 |  0   |  0   |   0   |   0   |   15.5 |


Die folgende Tabelle ist eine Kopie der Codeausgabe der vorherigen Zelle:

|    | Name        |   A1 |   A2 |   A3 |   A4 |   A5 |   A6 |   A7 |   A8 |   A9 |   A10 |   A11 |   sumP |
|---:|:------------|-----:|-----:|-----:|-----:|-----:|-----:|-----:|-----:|-----:|------:|------:|-------:|
|  0 | Alexander   |  4   |  6   |    4 |  7   | 11   |  4   |    4 |  5   |  5   |   4.5 |  10.5 |   65   |
|  1 | Andre       |  4   |  3.5 |    4 |  8   | 20.5 |  4   |    3 |  3.5 |  3.5 |   3   |   4   |   61   |
|  2 | Celine      |  4   |  3.5 |    2 |  7   | 13.5 |  5   |    5 |  5   |  4.5 |   5   |  11   |   65.5 |
|  3 | Christian   |  3.5 |  2.5 |    1 |  6.5 | 17   |  2.5 |    5 |  5   |  4   |   6   |   4   |   57   |
|  4 | Christopher |  3.5 |  0.5 |    0 |  4   |  7.5 |  0   |    0 |  0   |  0   |   0   |   0   |   15.5 |

```
dfKerg=pd.read_excel('rawData/KlausurPunkte.xlsx', header=4, usecols='A:L')
```

```
my_dispMarkdown(dfKerg.head())
```


|    | Name        |   A1 |   A2 |   A3 |   A4 |   A5 |   A6 |   A7 |   A8 |   A9 |   A10 |   A11 |
|---:|:------------|-----:|-----:|-----:|-----:|-----:|-----:|-----:|-----:|-----:|------:|------:|
|  0 | Alexander   |  4   |  6   |    4 |  7   | 11   |  4   |    4 |  5   |  5   |   4.5 |  10.5 |
|  1 | Andre       |  4   |  3.5 |    4 |  8   | 20.5 |  4   |    3 |  3.5 |  3.5 |   3   |   4   |
|  2 | Celine      |  4   |  3.5 |    2 |  7   | 13.5 |  5   |    5 |  5   |  4.5 |   5   |  11   |
|  3 | Christian   |  3.5 |  2.5 |    1 |  6.5 | 17   |  2.5 |    5 |  5   |  4   |   6   |   4   |
|  4 | Christopher |  3.5 |  0.5 |    0 |  4   |  7.5 |  0   |    0 |  0   |  0   |   0   |   0   |


```
my_show_doc(Klauswert.getDurchgefallen)
```


<h4 id="Klauswert.getDurchgefallen" class="doc_header"><code>Klauswert.getDurchgefallen</code><a href="__main__.py#L52" class="source_link" style="float:right"></a></h4>

> <code>Klauswert.getDurchgefallen</code>()

Liefert eine Liste mit den Namen der Teilnehmer, die die Klausur nicht bestanden haben, 
sowie deren Zielerreichungswert.


```
my_dispMarkdown(pbx2020.getDurchgefallen().head())
```


|    | Name        |   pktProz |   Note |
|---:|:------------|----------:|-------:|
|  4 | Christopher |   17.2222 |      5 |
| 15 | Kamil       |   25      |      5 |
| 20 | Lukas       |   45      |      5 |
| 34 | Tim         |   47.2222 |      5 |
| 35 | Tobias      |   44.4444 |      5 |


|    | Name        |   pktProz |   Note |
|---:|:------------|----------:|-------:|
|  4 | Christopher |   17.2222 |      5 |
| 15 | Kamil       |   25      |      5 |
| 20 | Lukas       |   45      |      5 |
| 34 | Tim         |   47.2222 |      5 |
| 35 | Tobias      |   44.4444 |      5 |



