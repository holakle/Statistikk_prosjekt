# Statistikk_prosjekt

ISTT1003: Student Depression Dataset. Analysen har to hovedspørsmål:

1. Hvordan henger CGPA sammen med arbeids-/studietimer, studiepress og økonomisk stress?
2. Hvor godt kan CGPA, arbeids-/studietimer, studiepress, økonomisk stress og alder klassifisere selvrapportert depresjon?

## Kjør analysen

Bruk Python 3.13 (versjonen kontrollkjøringen er utført med). Fra prosjektmappen:

```sh
python -m venv .venv
```

Aktiver miljøet med `.venv\Scripts\Activate.ps1` i PowerShell eller `source .venv/bin/activate` på Linux/macOS.

```sh
python -m pip install -r requirements.txt
python -m jupyterlab analyse.ipynb
```

Velg Python-miljøet som nettopp ble opprettet. I VS Code velges samme miljø som notebook-kjerne.
Kjør **Restart Kernel and Run All Cells**. Installasjonskommandoer kjøres ikke fra notatboken.

## Innhold og metodevalg

- `analyse.ipynb`: forklarte steg for datarensing, beskrivende statistikk, regresjon og klassifikasjon.
- `Student_Depression_Dataset.csv`: uendret råfil fra [Hopesb/Kaggle](https://www.kaggle.com/datasets/hopesb/student-depression-dataset).
- `resultater/`: renselogg, koeffisienter, konfidensintervaller, VIF, innflytelseskontroll, følsomhetsanalyse og testresultater.
- `figurer/`: oppdaterte figurer fra hovedanalysene og regresjonsdiagnostikk.
- `rapportforslag.md`: konkret forslag til rapportstruktur og introduksjon, som avventer godkjenning. Overleaf endres ikke av denne koden.

Hovedanalysen avgrenses til `Profession == Student`. Manglende/ugyldige analyseverdier dokumenteres før de utelates.
Null i CGPA og studiepress beholdes i hovedanalysen og undersøkes separat. Like svar slettes ikke som dubletter;
bare helt identiske rader behandles som rådatadubletter. Dupliserte/manglende person-ID-er stopper kjøringen for avklaring.
Råfilens SHA256 lagres og kontrolleres ved slutten av kjøringen.
Begge hovedmodellene gjentas uten nullverdiene, og gjenværende personer beholder sin opprinnelige
tilhørighet til trening/test. Endrede utvalgsstørrelser rapporteres; variantene brukes ikke til modellutvelgelse.

Den opprinnelige 75/25-delingen og frø 42 beholdes. Standardisering tilpasses bare treningsdata.
OLS tilpasses treningssettet og sammenlignes med treningsgjennomsnittet på testsettet.
Den logistiske modellen beholder fem forklaringsvariabler, L2-regularisering med C=1 og terskel 0,5,
og sammenlignes med vanligste treningsklasse. Vi optimaliserer ikke mot det allerede observerte testsettet.
Klyngeanalysen beholdes som et utforskende tillegg og brukes ikke til å velge hovedmodellene.

## Tolkning og begrensninger

Residualplott, QQ-plott, VIF og Cook-avstand er hjelp til vurdering, ikke automatiske godkjenninger av modellen.
OLS-tabellen bruker klassiske standardfeil; normalitet, konstant feilvarians og uavhengighet må drøftes.
Skårene for press og stress brukes numerisk, som antar like avstander mellom nabonivåer.
Verifiser dokumentasjonen for måleenheter, innsamling og selvrapportert depresjon før rapporten ferdigstilles.
Intern testytelse er ingen ekstern validering eller dokumentasjon på årsak eller klinisk diagnostikk.

KI er brukt til forslag, kodeoppdeling, datakontroll og regresjonsdiagnostikk. Gruppen må selv kontrollere og forklare
analysene og deklarere bruken i rapporten. Se oppgaveteksten for krav til rapport, referanser og KI-deklarasjon.
