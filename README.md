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
- `resultater/`: renselogg, koeffisienter, konfidensintervaller, valideringsresultater, følsomhetsanalyse og testresultater.
- `figurer/`: oppdaterte figurer fra hovedanalysene og regresjonsdiagnostikk.
- `rapportforslag.md`: konkret forslag til rapportstruktur og introduksjon, som avventer godkjenning. Overleaf endres ikke av denne koden.

Hovedanalysen avgrenses til `Profession == Student`. Manglende/ugyldige analyseverdier dokumenteres før de utelates.
Null i CGPA og studiepress beholdes i hovedanalysen og undersøkes separat. Like svar slettes ikke som dubletter;
bare helt identiske rader behandles som rådatadubletter. Dupliserte/manglende person-ID-er stopper kjøringen for avklaring.
Råfilens SHA256 lagres og kontrolleres ved slutten av kjøringen.
Begge hovedmodellene gjentas uten nullverdiene, og gjenværende personer beholder sin opprinnelige
tilhørighet til trening/test. Endrede utvalgsstørrelser rapporteres; variantene brukes ikke til modellutvelgelse.

Den opprinnelige testdelen på 25 % og frø 42 beholdes. De resterende 75 % deles stratifisert
i 60 % trening og 15 % validering. To uregulariserte logistiske modeller (tre og fem variabler)
tilpasses på 60 % og sammenlignes på 15 %. Femvariabelmodellen er den fastlagte hovedmodellen;
valideringsresultatene brukes ikke til automatisk modellvalg eller terskelendring.
Deretter tilpasses hovedmodellen på hele 75 %-delen og evalueres på testsettet med terskel 0,5.
Referansen bruker vanligste klasse i 75 %-delen. Logistisk regresjon bruker statsmodels uten
regularisering eller standardisering, og oddsratioer vises i opprinnelige måleenheter.
OLS tilpasses samme 75 %-del og sammenlignes med treningsgjennomsnittet på testsettet.
Bare k-means standardiserer variablene. Vi optimaliserer ikke mot det allerede observerte testsettet.
Klyngeanalysen beholdes som et utforskende tillegg og brukes ikke til å velge hovedmodellene.

## Tolkning og begrensninger

Residualplott og QQ-plott brukes til å vurdere modellforutsetningene.
OLS-tabellen bruker klassiske standardfeil; normalitet, konstant feilvarians og uavhengighet må drøftes.
Skårene for press og stress brukes numerisk, som antar like avstander mellom nabonivåer.
Verifiser dokumentasjonen for måleenheter, innsamling og selvrapportert depresjon før rapporten ferdigstilles.
Intern testytelse er ingen ekstern validering eller dokumentasjon på årsak eller klinisk diagnostikk.

Tidligere klassifikasjonstall fra den regulariserte modellen må erstattes med de nye resultatene.
Bruk samme kodeversjon for alle rapporttabeller og figurer. Overleaf oppdateres ikke i denne endringen.

KI er brukt til forslag, kodeoppdeling, datakontroll og regresjonsdiagnostikk. Gruppen må selv kontrollere og forklare
analysene og deklarere bruken i rapporten. Se oppgaveteksten for krav til rapport, referanser og KI-deklarasjon.
