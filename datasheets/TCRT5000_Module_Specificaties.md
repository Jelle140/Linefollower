# TCRT5000 – Sensormodule en technische specificaties

## Beschrijving

De TCRT5000-sensormodule is een infraroodreflectiesensor die gebruikt wordt voor het onderscheiden van lichte en donkere oppervlakken.

De module bestaat uit een infraroodled, een fototransistor, een comparator, een instelpotentiometer en indicatieleds.

In de linefollower worden zes sensormodules naast elkaar gemonteerd aan de voorzijde van het chassis.

## Technische specificaties

| Eigenschap | Specificatie |
|---|---|
| Sensortype | TCRT5000 |
| Meetprincipe | Infraroodreflectie |
| Golflengte infraroodled | 950 nm |
| Voedingsspanning in het project | 3,3 V DC |
| Analoge uitgang | A0 |
| Digitale uitgang | D0 |
| Aantal aansluitpinnen | 4 |
| Comparator | Vermoedelijk LM393 |
| Instelpotentiometer | Aanwezig |
| Indicatieleds | Aanwezig |
| Optimale meetafstand van de TCRT5000 | 2,5 mm |
| Detectiebereik van de TCRT5000 volgens datasheet | 0,2 – 15 mm bij meer dan 20% relatieve collectorstroom |
| Stroomverbruik volledige module | Niet gemeten |
| Afmetingen module | Niet opgemeten |
| Aantal gemonteerde modules | 6 |
| Aantal actief gebruikte sensoren in de lijnregeling | 5 |

De optische specificaties hebben betrekking op de TCRT5000-sensor zelf. De prestaties van de volledige module zijn afhankelijk van de elektronische schakeling, montagehoogte en reflectie-eigenschappen van het oppervlak.

## Pinout

Gezien vanaf de componentenzijde, met de aansluitheader bovenaan zoals op de foto van het prototype:

| Positie van links naar rechts | Pin | Functie |
|---|---|---|
| 1 | VCC | Positieve voedingsspanning |
| 2 | GND | Gemeenschappelijke massa |
| 3 | D0 | Digitale uitgang |
| 4 | A0 | Analoge uitgang |

De pinlabels op de printplaat moeten steeds gecontroleerd worden voordat de module wordt aangesloten.

## Werkingsprincipe

De infraroodled zendt infraroodlicht uit in de richting van het parcours.

De fototransistor ontvangt een gedeelte van het gereflecteerde infraroodlicht.

Een wit oppervlak reflecteert meer infraroodlicht dan een zwart oppervlak.

De elektronische schakeling op de module zet deze reflectie om in een elektrisch signaal.

Bij de gebruikte modules werd tijdens de praktijktesten vastgesteld:

- Wit oppervlak: lage analoge meetwaarde.
- Zwart oppervlak: hoge analoge meetwaarde.

## Analoge uitgang

De analoge uitgang A0 wordt aangesloten op een ADC-ingang van de STM32F103C8T6.

De STM32 beschikt over een 12-bit ADC, waardoor de digitale meetwaarden tussen 0 en 4095 liggen.

De analoge uitgang wordt gebruikt om de positie van de zwarte lijn te bepalen.

## Digitale uitgang

De digitale uitgang D0 wordt aangestuurd door de comparator op de module.

Met de instelpotentiometer kan de schakeldrempel van de comparator worden aangepast.

De digitale uitgang wordt niet gebruikt in de finale lijnvolgsoftware.

De detectie van zwart en wit gebeurt softwarematig op basis van de analoge meetwaarden.

## Aansluitingen op de STM32

| Sensor | Analoge uitgang | STM32-pin | ADC-kanaal |
|---|---|---|---|
| S0 | A0 | PA0 | ADC1_IN0 |
| S1 | A0 | PA1 | ADC1_IN1 |
| S2 | A0 | PA4 | ADC1_IN4 |
| S3 | A0 | PA5 | ADC1_IN5 |
| S4 | A0 | PA6 | ADC1_IN6 |
| S5 | A0 | PA7 | ADC1_IN7 |

Voor alle zes modules geldt:

- VCC wordt aangesloten op 3,3 V.
- GND wordt aangesloten op de gemeenschappelijke massa.
- A0 wordt aangesloten op de overeenkomstige ADC-ingang.
- D0 wordt niet gebruikt.

## Proof of concept

Tijdens de proof of concept werden de analoge meetwaarden van de zes sensoren gecontroleerd op een wit en een zwart oppervlak.

De resultaten toonden aan dat de sensoren onderscheid kunnen maken tussen de zwarte lijn en de witte achtergrond.

De testcode en bijbehorende meetresultaten zijn terug te vinden in:

`code/proof of concepts/sensor`

## Gebruik in de finale software

Alle zes sensoren worden analoog uitgelezen.

De eerste vijf sensoren worden gebruikt voor:

- detectie van de zwarte lijn;
- berekening van de lijnpositie;
- proportionele motorcorrectie;
- detectie van kruispunten.

De zesde sensor wordt wel uitgelezen, maar niet meegenomen in de lijnregeling omdat deze in de gemonteerde opstelling een foutief hoge meetwaarde op wit gaf.

De finale software gebruikt een vaste softwarematige detectiedrempel.

## Bronnen

### Bron 1 – Vishay Semiconductors

- Bron: https://www.vishay.com/docs/83760/tcrt5000.pdf
- Document: TCRT5000 / TCRT5000L – Reflective Optical Sensor with Transistor Output.
- Vindplaats: Features, Basic Characteristics en Relative Collector Current versus Distance.
- Gebruikte informatie: meetprincipe, golflengte, optimale meetafstand en optisch detectiebereik.

### Bron 2 – Fysieke inspectie

- Bron: eigen foto van de zes gemonteerde TCRT5000-sensormodules.
- Vindplaats: componentenzijde en aansluitheader van de printplaat.
- Gebruikte informatie: aantal modules, pinlabels, fysieke pinvolgorde, instelpotentiometer en indicatieleds.

### Bron 3 – Eigen proof of concept

- Bron: `code/proof of concepts/sensor`.
- Vindplaats: testcode en meetresultaten op wit en zwart.
- Gebruikte informatie: analoge sensorwerking en onderscheid tussen zwarte en witte oppervlakken.

### Bron 4 – Finale broncode

- Bron: `code/finaal/Src/sensors.c` en `code/finaal/Src/main.c`.
- Vindplaats: sensorinitialisatie, ADC-uitlezing en lijnpositieberekening.
- Gebruikte informatie: ADC-kanalen, aantal sensoren en toepassing binnen de lijnregeling.

## Opmerking

De officiële Vishay-datasheet beschrijft de TCRT5000-reflectiesensor zelf en niet de volledige breakoutmodule.

Omdat de exacte fabrikant van de breakoutmodule onbekend is, zijn de aanvullende modulegegevens gebaseerd op fysieke inspectie en de eigen projectdocumentatie.

Het exacte comparatortype, de afmetingen, het stroomverbruik en het volledige toegelaten voedingsspanningsbereik van de module zijn niet bevestigd.
