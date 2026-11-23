# Finale code

Deze map bevat de finale broncode van het Plan-B-prototype van de snelle line-following robot.

De software is geschreven in C voor de STM32F103C8T6 en verzorgt de uitlezing van de lijnsensoren, de aansturing van beide motoren en de detectie van kruispunten.

Het gerealiseerde prototype werd met deze software geprogrammeerd en heeft succesvol drie volledige rondes op het parcours afgelegd.

## Bestandsstructuur

### Inc

- `sensors.h` – definities en functies voor de lijnsensoren
- `motors.h` – definities en functies voor de motorsturing
- `bluetooth.h` – voorzien voor de HM-10 Bluetoothmodule
- `eeprom.h` – voorzien voor de 24LC256 EEPROM

### Src

- `main.c` – hoofdprogramma en lijnvolgalgoritme
- `sensors.c` – ADC-uitlezing en berekening van de lijnpositie
- `motors.c` – aansturing van de TB6612FNG en beide motoren
- `bluetooth.c` – gereserveerd bestand; Bluetoothfunctionaliteit niet geïmplementeerd
- `eeprom.c` – gereserveerd bestand; EEPROM-functionaliteit niet geïmplementeerd

De bestanden `bluetooth.c` en `eeprom.c` bevatten momenteel uitsluitend commentaar en maken geen deel uit van de actieve lijnregeling.

## Lijnvolging

De robot beschikt over zes TCRT5000-reflectiesensoren.

Alle zes sensoren worden analoog uitgelezen door de ADC van de STM32.

In de huidige lijnregeling worden de eerste vijf sensoren gebruikt voor:

- het berekenen van de lijnpositie;
- het detecteren van kruispunten.

De zesde sensor wordt wel uitgelezen, maar niet meegenomen in de regeling omdat deze in de gemonteerde opstelling een foutief hoge meetwaarde op wit gaf.

De positie van de zwarte lijn wordt berekend aan de hand van een gewogen gemiddelde van de sensorwaarden.

Op basis van deze lijnpositie wordt een proportionele correctie berekend:

`correctie = P × lijnpositie`

De motorsnelheden worden bepaald volgens:

`motor A = basissnelheid + correctie`

`motor B = basissnelheid - correctie`

Hierdoor stuurt de robot zichzelf terug naar de zwarte lijn.

## Snelheidsregeling

De in de repository gedocumenteerde instellingen zijn:

- snelheid recht stuk: `300`
- snelheid bocht: `150`
- grenswaarde bochtdetectie: `120`
- maximale motorsnelheid: `600`
- proportionele correctiefactor: `0,50`

Wanneer de absolute waarde van de lijnpositie groter wordt dan `120`, schakelt de software over naar de lagere bochtsnelheid.

De parameters kunnen experimenteel worden aangepast om de snelheid en stabiliteit te optimaliseren.

## Kruispuntdetectie

Een brede zwarte zone wordt als kruispunt beschouwd wanneer minimaal drie van de vijf gebruikte lijnsensoren tegelijk zwart detecteren.

Tijdens de kruispuntmodus:

1. wordt de normale lijncorrectie tijdelijk uitgeschakeld;
2. krijgen beide motoren dezelfde snelheid;
3. rijdt de robot rechtdoor;
4. wordt de kruispuntmodus pas verlaten nadat opnieuw gedurende meerdere meetcycli een normale lijn wordt waargenomen.

Instellingen:

- minimaal aantal zwarte sensoren: `3`
- aantal meetcycli voor vrijgave: `300`

## Motorsturing

De twee GA12-N20 DC-motoren worden aangestuurd via een TB6612FNG dubbele H-brug.

De motorsnelheid wordt geregeld met PWM.

### Motor A

- PWMA → PA8 (TIM1_CH1)
- AIN1 → PB13
- AIN2 → PB12

### Motor B

- PWMB → PB3 (TIM2_CH2, partial remap)
- BIN1 → PB15
- BIN2 → PA9

### TB6612FNG

- STBY → PB14
- VCC → 3,3 V
- VM → 5 V
- GND → gemeenschappelijke GND

Voor het gebruik van PB3 als PWM-uitgang wordt de JTAG-functionaliteit op deze pin uitgeschakeld, terwijl SWD beschikbaar blijft.

## Sensoren

De analoge sensoren zijn aangesloten op:

| Sensor | STM32-pin | ADC-kanaal |
|---|---|---|
| S0 | PA0 | ADC1_IN0 |
| S1 | PA1 | ADC1_IN1 |
| S2 | PA4 | ADC1_IN4 |
| S3 | PA5 | ADC1_IN5 |
| S4 | PA6 | ADC1_IN6 |
| S5 | PA7 | ADC1_IN7 |

De sensoren worden gevoed via de 3,3 V-uitgang van de STM32.

De ADC werkt met een resolutie van 12 bit, waardoor de ruwe meetwaarden tussen `0` en `4095` liggen.

De lijnherkenning gebruikt een vaste drempelwaarde:

`LINE_THRESHOLD = 450`

Er wordt geen automatische sensorkalibratie uitgevoerd.

## Project opbouwen in STM32CubeIDE

Deze repository bevat de eigen broncode en headerbestanden van de finale lijnvolger, maar geen volledig exporteerbaar STM32CubeIDE-project.

De oorspronkelijke projectconfiguratie, startupcode en het linkerscript zijn niet opgenomen in deze map.

Om de broncode opnieuw te compileren, moet een STM32-project worden aangemaakt met de juiste ondersteuning voor de STM32F103C8T6.

### Benodigdheden

- STM32CubeIDE
- STM32F103C8T6 als doelmicrocontroller
- ARM GCC-toolchain, meegeleverd met STM32CubeIDE
- geschikte STM32-startupcode
- geschikt linker script voor de gebruikte microcontroller
- ST-LINK-programmer voor het programmeren via SWD

### Stappen

1. Open STM32CubeIDE.
2. Maak een nieuw STM32-project aan voor de STM32F103C8T6.
3. Gebruik een passende startupconfiguratie en linker script voor deze microcontroller.
4. Voeg de bestanden uit `Src` toe aan de broncode van het project.
5. Voeg de bestanden uit `Inc` toe aan de include-map.
6. Controleer of het project de map `Inc` als include-pad gebruikt.
7. Controleer de clockconfiguratie en de beschikbare systeemondersteuning.
8. Zorg ervoor dat de eigen registerconfiguratie in `motors.c` en `sensors.c` niet wordt overschreven door conflicterende automatisch gegenereerde initialisatiecode.
9. Compileer het project met de ARM GCC-toolchain.
10. Programmeer de STM32 via ST-LINK en SWD.

De registerinstellingen voor GPIO, ADC en PWM zijn rechtstreeks in de broncode opgenomen. Hiervoor wordt geen HAL-bibliotheek gebruikt in de eigen lijnvolgmodules.

**Opmerking:** deze stappen beschrijven hoe de broncode in een nieuw STM32CubeIDE-project kan worden geïntegreerd. Een onafhankelijke compilatie van deze repository in een opnieuw aangemaakt project is nog niet uitgevoerd of bevestigd.

## Huidige uitvoering

De finale lijnvolgsoftware bevat:

- analoge uitlezing van zes TCRT5000-sensoren;
- berekening van de lijnpositie met vijf sensoren;
- proportionele lijncorrectie;
- afzonderlijke PWM-aansturing van beide motoren;
- aangepaste basissnelheid voor rechte stukken en bochten;
- kruispuntdetectie;
- rechtdoor rijden over kruispunten.

De HM-10 Bluetoothmodule en de 24LC256 EEPROM zijn voorzien in het elektronische ontwerp, maar worden niet actief gebruikt door de finale lijnvolgsoftware.

De software werd op het fysieke prototype getest. De robot heeft succesvol drie volledige rondes op het parcours afgelegd.

## Beperkingen

- De zesde lijnsensor wordt momenteel niet gebruikt voor de lijnpositieberekening.
- De lijnherkenning gebruikt een vaste ADC-drempelwaarde.
- Er is geen automatische kalibratie.
- Bluetoothcommunicatie is niet geïmplementeerd.
- EEPROM-opslag is niet geïmplementeerd.
- De repository bevat geen volledig STM32CubeIDE-project en is daardoor niet rechtstreeks als zelfstandig project te bouwen.

Deze beperkingen zijn bewust gedocumenteerd zodat duidelijk is welke onderdelen daadwerkelijk in het Plan-B-prototype werden gerealiseerd.
