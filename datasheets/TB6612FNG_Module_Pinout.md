# TB6612FNG – Motorsturing en pinout

## Beschrijving

De TB6612FNG is een dubbele H-brug waarmee twee DC-motoren onafhankelijk van elkaar kunnen worden aangestuurd.

De module wordt in de linefollower gebruikt voor het regelen van de snelheid en draairichting van twee GA12-N20 DC-motoren.

## Technische specificaties

| Eigenschap | Specificatie |
|---|---|
| IC | Toshiba TB6612FNG |
| Type | Dubbele H-brug |
| Aantal motorkanalen | 2 |
| Logische voedingsspanning VCC | 2,7 – 5,5 V DC |
| Motorvoedingsspanning VM | 2,5 – 13,5 V DC |
| Absolute maximale motorspanning | 15 V DC |
| Nominale uitgangsstroom | 1,2 A per kanaal |
| Maximale kortstondige piekstroom | 3,2 A per kanaal |
| Maximale PWM-frequentie | 100 kHz |
| Thermische beveiliging | Aanwezig |
| Onderspanningsdetectie | Aanwezig |
| Standbyfunctie | Aanwezig |
| Referentieafmetingen breakoutmodule | 20,32 × 20,32 mm |
| Referentiepinafstand | 2,54 mm |

De toelaatbare uitgangsstroom is afhankelijk van de thermische omstandigheden en de uitvoering van de breakoutmodule. De piekstroom mag niet continu worden aangehouden.

De afmetingen zijn gebaseerd op de SparkFun-referentiemodule. De exacte afmetingen van de gebruikte module zijn niet bevestigd.

## Pinout

| Pin | Type | Functie |
|---|---|---|
| VM | Voeding | Voedingsspanning van de motoren |
| VCC | Voeding | Logische voedingsspanning |
| GND | Voeding | Gemeenschappelijke massa |
| PWMA | Ingang | Snelheidsregeling motor A |
| AIN1 | Ingang | Richtingssignaal 1 motor A |
| AIN2 | Ingang | Richtingssignaal 2 motor A |
| AO1 | Uitgang | Eerste aansluiting motor A |
| AO2 | Uitgang | Tweede aansluiting motor A |
| PWMB | Ingang | Snelheidsregeling motor B |
| BIN1 | Ingang | Richtingssignaal 1 motor B |
| BIN2 | Ingang | Richtingssignaal 2 motor B |
| BO1 | Uitgang | Eerste aansluiting motor B |
| BO2 | Uitgang | Tweede aansluiting motor B |
| STBY | Ingang | Activeren of uitschakelen van de H-bruggen |

## Fysieke pinvolgorde

Onderstaande pinvolgorde is gebaseerd op de SparkFun TB6612FNG-referentiemodule, gezien vanaf de achterzijde met de pinlabels zichtbaar.

| Positie | Linker header | Rechter header |
|---|---|---|
| 1 | PWMA | VM |
| 2 | AIN2 | VCC |
| 3 | AIN1 | GND |
| 4 | STBY | AO1 |
| 5 | BIN1 | AO2 |
| 6 | BIN2 | BO2 |
| 7 | PWMB | BO1 |
| 8 | GND | GND |

De fysieke pinvolgorde kan verschillen tussen fabrikanten. Bij het aansluiten van de gebruikte module moeten daarom steeds de op de printplaat aangebrachte pinlabels gevolgd worden.

## Aansluitingen van de linefollower

| TB6612FNG-pin | Aansluiting | Functie |
|---|---|---|
| VM | Buckconverter 5 V | Motorvoeding |
| VCC | Buckconverter 3,3 V | Logische voeding |
| GND | Gemeenschappelijke GND | Massa |
| PWMA | STM32 PA8 | TIM1_CH1 |
| AIN1 | STM32 PB13 | Draairichting motor A |
| AIN2 | STM32 PB12 | Draairichting motor A |
| AO1 | Motor A | Motoruitgang 1 |
| AO2 | Motor A | Motoruitgang 2 |
| PWMB | STM32 PB3 | TIM2_CH2 met remap |
| BIN1 | STM32 PB15 | Draairichting motor B |
| BIN2 | STM32 PA9 | Draairichting motor B |
| BO1 | Motor B | Motoruitgang 1 |
| BO2 | Motor B | Motoruitgang 2 |
| STBY | STM32 PB14 | Vrijgave motorsturing |

## Werkingsprincipe

De draairichting van iedere motor wordt bepaald door twee digitale richtingssignalen.

De snelheid wordt geregeld door de dutycycle van het PWM-signaal te wijzigen.

De standby-ingang moet logisch hoog zijn voordat de motoren kunnen worden aangestuurd.

## Waarheidstabel

| STBY | IN1 | IN2 | PWM | Werking |
|---|---|---|---|---|
| 0 | X | X | X | Standby, uitgangen hoogohmig |
| 1 | 1 | 0 | 1 | Draairichting 1 |
| 1 | 0 | 1 | 1 | Draairichting 2 |
| 1 | 1 | 1 | X | Kortsluitremming |
| 1 | 0 | 0 | 1 | Stop, uitgangen hoogohmig |
| 1 | 1 | 0 | 0 | Kortsluitremming |
| 1 | 0 | 1 | 0 | Kortsluitremming |

X betekent dat de toestand van het betreffende signaal geen invloed heeft op de aangegeven werkingsmodus.

De effectieve mechanische draairichting is afhankelijk van de polariteit waarmee de motor wordt aangesloten.

## Gebruik in de finale software

De STM32 genereert twee onafhankelijke PWM-signalen:

- TIM1_CH1 op PA8 voor motor A.
- TIM2_CH2 op PB3 voor motor B.

Hierdoor kunnen beide motoren onafhankelijk van elkaar worden geregeld.

De proportionele lijnregeling bepaalt het snelheidsverschil tussen beide motoren, zodat de robot de zwarte lijn kan volgen.

Tijdens het rijden over een kruispunt krijgen beide motoren dezelfde ingestelde snelheid.

## Bronnen

### Bron 1 – Toshiba

- Bron: TB6612FNG-datasheet, aanwezig in de map `datasheets`.
- Vindplaats: Operating Range, Absolute Maximum Ratings en H-SW Control Function.
- Gebruikte informatie: elektrische specificaties, maximale stroom, voedingsspanning en werkingsmodi.

### Bron 2 – SparkFun TB6612FNG Hookup Guide

- Bron: https://learn.sparkfun.com/tutorials/tb6612fng-hookup-guide/board-overview
- Vindplaats: Board Overview en pinouttabel.
- Gebruikte informatie: moduleaansluitingen, fysieke referentiepinvolgorde, PWM, standby en werkingsmodi.

### Bron 3 – SparkFun Motor Driver

- Bron: https://www.sparkfun.com/sparkfun-motor-driver-dual-tb6612fng-1a.html
- Vindplaats: Features & Specs en Documentation.
- Gebruikte informatie: referentieafmetingen, pinafstand, maximale PWM-frequentie en beveiligingsfuncties.

### Bron 4 – Eigen projectdocumentatie

- Bron: elektronisch schema en finale broncode van de linefollower.
- Vindplaats: `technische tekeningen/elektronisch` en `code/finaal/Src`.
- Gebruikte informatie: aansluitingen van de TB6612FNG op de STM32, motoren en buckconverters.
