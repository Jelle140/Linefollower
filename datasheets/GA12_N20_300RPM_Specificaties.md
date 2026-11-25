# GA12-N20 – DC-motor met tandwielreductie

## Beschrijving

De linefollower wordt aangedreven door twee compacte GA12-N20 DC-motoren met metalen tandwielreductie.

De tandwielreductie verlaagt het toerental van de motor en verhoogt het beschikbare koppel aan de uitgaande as.

Beide motoren worden onafhankelijk aangestuurd via een TB6612FNG dubbele H-brug.

## Technische specificaties

| Eigenschap | Specificatie |
|---|---|
| Motorserie | GA12-N20 |
| Motortype | DC-motor met borstels |
| Nominale spanning volgens componentkeuze | 6 V DC |
| Toerental volgens componentkeuze | 300 rpm |
| Tandwielreductie | Metaal |
| Reductieverhouding | Niet bevestigd |
| Aantal elektrische aansluitingen | 2 |
| Draairichting | Omkeerbaar |
| Snelheidsregeling | PWM |
| Motorsturing | TB6612FNG |
| Nominale stroom | Niet bevestigd |
| Blokkeerstroom | Niet bevestigd |
| Nominaal koppel | Niet bevestigd |
| Afmetingen motor | Niet opgemeten |
| Wieldiameter | 44 mm |
| Wielbreedte | 17 mm |
| Aantal gebruikte motoren | 2 |
| Exacte fabrikant | Onbekend |

De spanning en het toerental zijn gebaseerd op de oorspronkelijke componentkeuze. Deze waarden zijn niet opnieuw gemeten op het gerealiseerde prototype.

## Pinout

| Aansluiting | Functie |
|---|---|
| M1 | Eerste motoraansluiting |
| M2 | Tweede motoraansluiting |

De draairichting van de motor wordt omgekeerd door de polariteit over de twee motoraansluitingen om te keren.

## Aansluiting op de TB6612FNG

| Motor | Motoraansluiting | TB6612FNG |
|---|---|---|
| Motor A | M1 | AO1 |
| Motor A | M2 | AO2 |
| Motor B | M1 | BO1 |
| Motor B | M2 | BO2 |

De TB6612FNG wordt aangestuurd door de STM32F103C8T6.

## Snelheidsregeling

De motorsnelheid wordt geregeld door middel van pulsbreedtemodulatie (PWM).

Door de dutycycle van het PWM-signaal te wijzigen, wordt de gemiddelde motorspanning beïnvloed.

De twee motoren kunnen onafhankelijk van elkaar worden geregeld. Hierdoor kan de robot sturen zonder een afzonderlijk stuurmechanisme.

## Theoretische maximale rijsnelheid

Uitgaande van een toerental van 300 rpm en een wieldiameter van 44 mm kan de theoretische rijsnelheid worden berekend.

### Wielomtrek

O = π × d

O = π × 0,044

O = 0,1382 m

### Aantal omwentelingen per seconde

n = 300 / 60

n = 5 omwentelingen per seconde

### Theoretische rijsnelheid

v = O × n

v = 0,1382 × 5

v = 0,691 m/s

De theoretische rijsnelheid bedraagt ongeveer 0,69 m/s of 2,49 km/h bij een wieltoerental van 300 rpm.

Dit is een theoretische waarde. De werkelijke snelheid is afhankelijk van:

- motorvoedingsspanning;
- PWM-dutycycle;
- mechanische belasting;
- wrijving;
- grip van de wielen;
- verliezen in de tandwielreductie.

## Toepassing in de linefollower

De twee motoren zijn aan de achterzijde van het chassis gemonteerd.

De proportionele lijnregeling berekent een snelheidsverschil tussen beide motoren om de robot naar de zwarte lijn te sturen.

Tijdens het rijden over een kruispunt krijgen beide motoren dezelfde snelheidsinstelling.

## Bronnen

### Bron 1 – Algemene GA12-N20-datasheet

- Bron: algemene GA12-N20-datasheet, aanwezig in de map `datasheets`.
- Vindplaats: algemene motorbeschrijving en technische gegevens.
- Gebruikte informatie: motortype, tandwielreductie en algemene werking.

### Bron 2 – Oorspronkelijke componentkeuze

- Bron: eigen componentenlijst en projectdocumentatie.
- Vindplaats: `bill of materials`.
- Gebruikte informatie: voorziene motorspanning van 6 V, toerental van 300 rpm en aantal motoren.

### Bron 3 – Fysieke inspectie

- Bron: eigen foto van de gemonteerde DC-motor.
- Vindplaats: motorbehuizing, tandwielreductie en wielmontage.
- Gebruikte informatie: fysieke uitvoering en montage van de motor.

### Bron 4 – Mechanisch ontwerp

- Bron: eigen mechanische projectdocumentatie.
- Vindplaats: `technische tekeningen/mechanisch`.
- Gebruikte informatie: wielafmetingen en mechanische opstelling.

### Bron 5 – Eigen technische berekeningen

- Bron: berekening op basis van wieldiameter en opgegeven toerental.
- Gebruikte informatie: theoretische rijsnelheid van 0,69 m/s.

### Bron 6 – Finale broncode

- Bron: `code/finaal/Src/motors.c` en `code/finaal/Src/main.c`.
- Gebruikte informatie: PWM-aansturing, onafhankelijke motorregeling en lijnvolging.

## Opmerking

Een specifieke fabrikantendatasheet van de exact gebruikte motorvariant is niet beschikbaar.

Daarom wordt de algemene GA12-N20-datasheet aangevuld met gegevens uit de oorspronkelijke componentkeuze, fysieke inspectie en eigen technische berekeningen.

De nominale stroom, blokkeerstroom, reductieverhouding, exacte afmetingen en het motorkoppel zijn niet bevestigd.
