# ⏳ Dove si vive di più (e in buona salute)?

Progetto di **Francesco Autorino** – Data Analyst.

🛠️ Strumenti: **Python · Excel · Power BI**

📊 Dati ISTAT: speranza di vita di **107 province** (2010-2024), anni in buona salute e stili di vita di **21 regioni**.

📅 Anno principale: **2024** (ultimo anno definitivo).

---

## 🧭 1. Il progetto in breve

❓ **La domanda**: quanti anni si vive in Italia, provincia per provincia, e quanti di questi in buona salute?

Le 5 domande più piccole:

1️⃣ 🗺️ Quanti anni si vive in ogni provincia?

2️⃣ 💚 Quanti di questi anni sono in buona salute?

3️⃣ ⚖️ Quanto è grande la distanza tra Nord e Sud? E tra uomini e donne?

4️⃣ 📈 Come è cambiata dal 2010 a oggi, Covid compreso?

5️⃣ 🚬 Gli stili di vita (sport, peso, fumo) c'entrano?

📌 **Speranza di vita** = quanti anni vive in media chi nasce oggi, se la mortalità resta quella di quell'anno.

📌 **Anni in buona salute** = la parte di quegli anni in cui le persone dicono di stare bene o molto bene.

---

## 🎯 2. I risultati principali

🗺️ In Italia si vive **83,5 anni**. Da **85,0** a **Treviso** a **81,5** a **Caserta**: **3,5 anni** di differenza.

💚 In buona salute si vivono **58,2 anni** (il 70% della vita). Da **69,7** a **Bolzano** a **53,4** in **Calabria**: oltre **16 anni** di differenza.

⚖️ Il **Nord** vive **1,4 anni** in più del **Sud** (erano 0,9 nel 2010).

👫 Le **donne** vivono **85,6 anni**, gli **uomini 81,5**. Ma in buona salute le donne vivono **meno**: **56,6** contro **59,8**.

📉 Il **Covid** ha tolto **1,1 anni** nel 2020 (da 83,2 a 82,1). **Lodi, Cremona e Bergamo**: **−3,7 anni**.

📈 Nel **2024** l'Italia è a **83,5**, sopra il livello del 2019. **93 province su 107** sono tornate al 2019.

🚶 Dove ci sono più persone **sedentarie**, gli anni in buona salute sono meno (Spearman **−0,88**).

---

## 🛠️ 3. Perché questi strumenti

🐍 **Python**: unire 3 fonti ISTAT, controllarle, fare mappe, andamenti e correlazioni.

📗 **Excel**: un file facile da usare, con **"La mia provincia"** e il **confronto tra 2 province** (menu a tendina e formule).

📊 **Power BI**: la dashboard con la mappa delle province e i pulsanti per **zona** e **sesso**.

---

## 🔄 4. Il percorso dei dati

```
ISTAT tavole di mortalità ─┐
ISTAT BES dei territori ───┼─► 01_scarica.py ─► 02_pulizia.py ─► ✅ 5 tabelle pulite ─┬─► 🐍 Python
ISTAT BES regionale ───────┘   (1GrezziNonPuliti)                 (2Puliti)          ├─► 📗 Excel
                                                                                     └─► 📊 Power BI
```

🧹 **Cosa ho fatto durante la pulizia**

| Passo | Cosa | Risultato |
|---|---|---|
| 1 | Lette le tavole di mortalità (nascita e 65 anni, uomini, donne, totale) | 18.084 righe |
| 2 | Controllati valori vuoti e doppioni | 0 e 0 |
| 3 | Tenuti gli anni fino al 2024: il 2025 è ancora provvisorio | 2010-2024 |
| 4 | Province × anni × sesso | 4.815 righe, 107 province |
| 5 | Controllo: tavole di mortalità e BES dei territori danno lo stesso valore (2024) | differenza massima 0,2 anni |
| 6 | Aggiunte coordinate e sigle delle province (dal progetto Costo della vita) | 107 su 107 |
| 7 | Letto il BES regionale: anni in buona salute, fumo, sport, peso, morti evitabili | 21 regioni |
| 8 | Controllo: Italia 2024 uguale nelle due fonti | 83,5 = 83,5 ✅ |
| 9 | Controllo: nessuna provincia sotto 75 o sopra 90 anni | 0 |

⚠️ Nel BES dei territori il **totale** (uomini + donne) mancava per alcune province in alcuni anni (2010, 2016, 2021): per questo ho usato le **tavole di mortalità**, che sono complete.

---

## 📁 5. I file in questo repository

| File | A cosa serve |
|---|---|
| `README.md` | Questo file |
| `DESCRIZIONE_GITHUB.md` | Nome, descrizione e topics del repository |
| `00_LEGGIMI.md` (in ogni cartella) | Una spiegazione corta di quella cartella |

### 📂 01Python

| File | A cosa serve |
|---|---|
| `01_analisi_speranza_di_vita.ipynb` | 📓 L'analisi completa con 7 grafici (si legge anche su GitHub) |
| `02_CONCLUSIONI.md` | ✅ Le risposte alle 5 domande |

### 📂 02Excel

| File | A cosa serve |
|---|---|
| `01_Speranza_Di_Vita_Analisi.xlsx` | 📗 11 fogli: **La mia provincia**, **confronto tra 2 province**, province, regioni, zone, andamento |

### 📂 03PowerBi

| File | A cosa serve |
|---|---|
| `01_SperanzaDiVitaDashboard.zip` | ⭐ **La dashboard**: estrai lo zip e apri `SperanzaDiVita_Dashboard.pbip` con Power BI Desktop |
| `02_SperanzaDiVita_Dashboard.pdf` | 📄 La dashboard in PDF |
| `03_misure_DAX.txt` | 🧮 Le 34 misure DAX |

📊 **Le 7 pagine della dashboard**

1. **Panoramica**: 6 numeri chiave, l'Italia disegnata con le province, le zone
2. **Le province**: tutte le province in classifica e l'andamento anno per anno
3. **In buona salute**: anni in buona salute e non, regione per regione
4. **Nord e Sud, uomini e donne**: le zone dal 2010 e la differenza tra donne e uomini
5. **2010-2024**: il Covid e il recupero, provincia per provincia
6. **Stili di vita**: sport, peso e morti evitabili a confronto con la buona salute
7. **Conclusioni**

🎛️ In alto si sceglie la **zona** (Nord, Centro, Sud, Isole) e il **sesso** (Totale, Uomini, Donne).

---

## 📦 6. Dati e script

📌 Qui ci sono solo i **risultati**: analisi, file Excel e dashboard.

📥 I dati si possono riscaricare dalle fonti (link più sotto).

🐍 Gli script Python di raccolta e pulizia dei dati sono disponibili su richiesta.

---

## ⚠️ 7. Limiti

📌 Gli **anni in buona salute** ci sono solo per **regione**: vengono da un'indagine a campione.

📌 Dipendono da come le persone **giudicano** la propria salute. Nel 2020-2021 molti l'hanno giudicata migliore del solito: per questo il valore sale proprio negli anni del Covid.

📌 La speranza di vita è una **media**: non dice quanto vivrà una persona.

📌 Gli stili di vita sono confrontati su 21 regioni: si vede un legame, non la causa.

📌 Il 2025 non è usato perché è ancora provvisorio.

---

## 🔗 8. Da dove arrivano i dati (link)

| Fonte | Cosa ho preso | Link |
|---|---|---|
| ISTAT – IstatData (esploradati) | La banca dati da cui ho scaricato le tavole di mortalità e il BES dei territori | https://esploradati.istat.it/databrowser/ |
| ISTAT – Tavole di mortalità (API SDMX) | Speranza di vita alla nascita e a 65 anni, province, regioni, Italia, 2004-2025 | https://esploradati.istat.it/SDMXWS/rest/data/IT1,26_295_DF_DCIS_MORTALITA1_1,1.0/A..LIFEXP.1+2+9.Y_UN4+Y65-69?startPeriod=2004 |
| ISTAT – BES dei territori, Salute (API SDMX) | Mortalità evitabile per provincia | https://esploradati.istat.it/SDMXWS/rest/data/IT1,DF_BES_TERRIT_1,1.0/all |
| ISTAT – Gli indicatori del Bes | La pagina con l'appendice statistica, la dashboard e il rapporto | https://www.istat.it/statistiche-per-temi/focus/benessere-e-sostenibilita/la-misurazione-del-benessere-bes/gli-indicatori-del-bes/ |
| ISTAT – Appendice statistica BES, edizione 2026 | Anni in buona salute e stili di vita per regione | https://www.istat.it/wp-content/uploads/2026/10/Appendice-statistica-bes-edizione-2026.zip |

📅 Dati scaricati il **27 ottobre 2026**.

---

## 🪜 9. Tutti i passaggi fatti, in ordine

1️⃣ **Scelta del progetto**: non solo quanto si vive, ma anche quanto si vive bene.

2️⃣ **Domande**: ho fissato le 5 domande e il periodo 2010-2024.

3️⃣ **Raccolta** (`01_scarica.py`): tavole di mortalità e BES dei territori dall'API ISTAT, BES regionale dal sito ISTAT.

4️⃣ **Controllo**: totali mancanti nel BES dei territori, anni provvisori, confronto tra le fonti.

5️⃣ **Pulizia** (`02_pulizia.py`): province, regioni, zone e Italia, anno per anno e per sesso.

6️⃣ **Python**: notebook con 7 grafici, mappa delle province e correlazioni.

7️⃣ **Excel**: 11 fogli con 1.728 formule, "La mia provincia" e il confronto tra 2 province, 0 errori.

8️⃣ **Power BI**: dashboard di 7 pagine con mappa e pulsanti per zona e sesso, aperta e controllata in Power BI Desktop.

9️⃣ **PDF**: esportata la dashboard in `SperanzaDiVita_Dashboard.pdf`.

🔟 **Conclusioni**: risposte alle 5 domande e limiti.
