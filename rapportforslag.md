# Forslag til minimale endringer i Overleaf

**Status: forslag til godkjenning. Ingen endringer er gjort i Overleaf.**

Forslaget gjelder [ISTT1003 Prosjektoppgave](https://www.overleaf.com/project/6ae86172808331c30e9716d0).
Behold eksisterende bakgrunnsavsnitt, forfattere, hovedseksjoner, poengangivelser og malinnhold.
Resultattekst skal bygge på den kjørte notatboken og formuleres og kontrolleres av gruppen.

## 1. Tittel

Endre bare teksten i `\prosjekttittel` i `main.tex` til:

> Studenters karaktergjennomsnitt og psykiske helse: regresjon og klassifikasjon

Forside, forfattere, logo og øvrig oppsett beholdes.

## 2. Introduksjon

Behold bakgrunnsavsnittet som starter «Samfunnets fokus på mental helse …».
Erstatt bare den markerte problemstillingen i `deler/02-introduksjon.tex` med:

```latex
\hl{Vi vil undersøke hvordan arbeids-/studietimer, studiepress og økonomisk stress henger sammen med studenters karaktergjennomsnitt ved hjelp av multippel lineær regresjon. I tillegg vil vi bruke logistisk regresjon for å undersøke hvor godt karaktergjennomsnitt, arbeids-/studietimer, studiepress, økonomisk stress og alder kan brukes til å forutsi om studentene har rapportert depresjon.}
```

Dette bevarer den opprinnelige problemstillingen om CGPA og gjør de fem forklaringsvariablene
i klassifikasjonen eksplisitte. Fem forklaringsvariabler er ikke det samme som fem modellparametere;
skjæringspunktet kommer i tillegg. CGPA brukes som respons i OLS og som forklaringsvariabel i klassifikasjonen.

Datakildeavsnittet beholdes foreløpig. Påstanden om undersøkelser fra ulike universiteter i India må
underbygges med kildedokumentasjon før rapporten ferdigstilles; vi legger ikke til antakelser om
rekruttering eller målemetode. Bruk «selvrapportert depresjon» gjennomgående.

## 3. Struktur: behold hovedseksjonene, juster underseksjonene

| Del | Foreslått innhold/endring |
| --- | --- |
| 1 Sammendrag | Behold malen. Fyll inn til slutt med de to hovedanalysene og viktigste funn. |
| 2 Introduksjon | Behold bakgrunn og «Datasett og formål». Erstatt bare den markerte problemstillingen over. |
| 3 Beskrivende dataanalyse | Behold eksisterende punkter. Dokumenter analysevariabler, renselogg, verdiområder og klassefordeling. |
| 4 Metoder | 4.1 Databehandling (behold), 4.2 Multippel lineær regresjon (ny), 4.3 Klassifikasjon (behold), 4.4 Utforskende tillegg: klyngeanalyse (eksisterende innhold). |
| 5 Resultater | 5.1 Multippel lineær regresjon (ny), 5.2 Klassifikasjon (behold), 5.3 Utforskende tillegg: klyngeanalyse (behold), 5.4 Begrensninger (behold). |
| 6 Diskusjon og konklusjon | Behold eksisterende punkter. Svar først på de to hovedspørsmålene, og skill fra utforskende klyngefunn. |
| Referanser, kode og KI-deklarasjon | Behold eksisterende deler. Oppdater kodehenvisning og dokumenter faktisk KI-bruk. |

LaTeX nummererer automatisk; behold filnavn, `\input`-rekkefølge og øvrig oppsett.
Bytt «de to metodene» til «regresjons- og klassifikasjonsanalysen» der hovedanalysene menes.
Bytt «de samme faktorene» bare der femvariabelmodellen ellers blir feil beskrevet.
Huskelister i malen beholdes til gruppen har fylt inn innholdet.

## 4. Innhold i de nye regresjonsdelene

**Metode:** formelen med tre forklaringsvariabler, minste kvadraters metode, 75/25-deling,
koeffisienttolkning og forutsetninger. Beskriv residualplott, QQ-plott, korrelasjoner/VIF,
Cook-avstand og separat følsomhetsanalyse for nullverdier. Forklar at diagnostikken ikke
automatisk avgjør hvilke observasjoner som er riktige eller gale.

**Resultater:** en koeffisienttabell med klassiske 95 % konfidensintervaller og p-verdier,
treningens R²/justert R², testens RMSE/R² og referansemodellens feil. Velg relevante
diagnostikkfigurer og forklar observerte avvik. Følsomhetsanalysen rapporteres med endrede
utvalgsstørrelser; den brukes til robusthetsvurdering, ikke modellutvelgelse.

## 5. Hva dette forslaget ikke endrer

Bakgrunnsavsnittet skrives ikke om. Forfattere, rapportmal, kildeliste og eksisterende
klyngepunkter beholdes. Det legges ikke inn ferdig resultattekst eller nye hypoteser etter
at resultatene er kjent. Overleaf endres først etter særskilt godkjenning av forslaget.
