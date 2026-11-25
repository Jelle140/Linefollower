# MP1584EN – DC-DC-buckconverter

## Beschrijving

De MP1584EN is een schakelende DC-DC-step-downconverter waarmee een hogere gelijkspanning wordt omgezet naar een lagere gelijkspanning.

In de linefollower worden deze modules gebruikt om de batterijspanning van de 2S LiPo om te zetten naar de benodigde voedingsspanningen voor de elektronische componenten.

## Technische specificaties

| Eigenschap | Specificatie |
|---|---|
| Regel-IC | MP1584EN |
| Fabrikant IC | Monolithic Power Systems (MPS) |
| Type | DC-DC-step-downconverter |
| Ingangsspanningsbereik IC | 4,5 – 28 V DC |
| Maximale uitgangsstroom IC | 3 A |
| Instelbare schakelfrequentie IC | 100 kHz – 1,5 MHz |
| Feedbackreferentiespanning | 0,8 V |
| Uitgangsspanning | Instelbaar via potentiometer |
| Spoel | 4,7 µH (4R7) |
| Thermische beveiliging IC | Aanwezig |
| Soft-start | Aanwezig |
| Nominale ingangsspanning in project | 7,4 V DC |
| Maximale batterijspanning | 8,4 V DC |
| Afmetingen module | Niet opgemeten |

De maximale uitgangsstroom van 3 A geldt voor het regel-IC onder geschikte bedrijfsomstandigheden. De maximaal toelaatbare continue stroom van de volledige module is afhankelijk van de koeling en de overige componenten op de printplaat.

## Pinout van de module

| Aansluiting | Functie |
|---|---|
| IN+ | Positieve ingangsspanning |
| IN- | Negatieve ingangsspanning / GND |
| OUT+ | Positieve geregelde uitgangsspanning |
| OUT- | Negatieve uitgangsspanning / GND |

Bij het aansluiten moeten de pinlabels op de printplaat gevolgd worden.

De ingangsmassa en uitgangsmassa zijn bij dit type niet-geïsoleerde buckconverter elektrisch verbonden.

## Instellen van de uitgangsspanning

De uitgangsspanning kan worden ingesteld met de potentiometer op de module.

De uitgangsspanning moet met een multimeter gecontroleerd worden voordat de elektronische componenten worden aangesloten.

Een buckconverter kan uitsluitend een lagere uitgangsspanning produceren dan de beschikbare ingangsspanning, rekening houdend met de benodigde spanningsmarge.

## Toepassing in de linefollower

Op het gerealiseerde prototype zijn drie MP1584EN-modules aanwezig.

De gedocumenteerde voedingsspanningen zijn:

### Voeding 3,3 V

- Logische voeding TB6612FNG.
- HM-10 Bluetoothmodule.
- 24LC256 EEPROM.

### Voeding 5 V

- Voedingsingang STM32 Smart V2.0.
- Motorvoeding TB6612FNG.

### Derde buckconverter

Een bijkomende voedingsspanning van 6 V werd tijdens het ontwerp overwogen voor de motorvoeding.

De exacte instelling en functie van de derde gemonteerde buckconverter zijn nog niet opnieuw gecontroleerd.

## Werkingsprincipe

De MP1584EN gebruikt een schakelende regelkring om de uitgangsspanning te regelen.

De spoel, Schottkydiode en condensatoren zorgen samen voor de omzetting en afvlakking van de spanning.

Via de feedbackkring wordt de uitgangsspanning geregeld op de ingestelde waarde.

## Voordelen

- Hoger rendement dan een klassieke lineaire spanningsregelaar.
- Compacte afmetingen.
- Instelbare uitgangsspanning.
- Geschikt voor batterijgevoede toepassingen.
- Verschillende voedingsspanningen kunnen uit dezelfde batterij worden verkregen.

## Veiligheid

- Controleer de polariteit van de voedingsaansluitingen.
- Meet de uitgangsspanning voordat componenten worden aangesloten.
- Vermijd kortsluiting.
- Respecteer de thermische en elektrische grenzen van de module.
- Isoleer blootliggende geleiders.
- Koppel de batterij los tijdens werkzaamheden aan de bedrading.

## Bronnen

### Bron 1 – Monolithic Power Systems

- Bron: https://www.monolithicpower.com/en/mp1584.html
- Document: MP1584-datasheet.
- Vindplaats: Features, Electrical Characteristics en Pin Functions.
- Gebruikte informatie: ingangsspanningsbereik, uitgangsstroom, schakelfrequentie, feedbackspanning en beveiligingsfuncties.

### Bron 2 – Fysieke inspectie

- Bron: eigen foto van de buckconverters op het gerealiseerde prototype.
- Vindplaats: printplaat, typeaanduiding en spoel.
- Gebruikte informatie: MP1584EN-typeaanduiding, aanwezigheid van drie modules, instelpotentiometer en 4R7-spoel.

### Bron 3 – Eigen projectdocumentatie

- Bron: elektronisch ontwerp en voedingsconfiguratie van de linefollower.
- Vindplaats: `technische tekeningen/elektronisch`.
- Gebruikte informatie: voorziene voedingsspanningen en aangesloten componenten.

## Opmerking

De officiële datasheet beschrijft het MP1584-regel-IC. De exacte fabrikant van de breakoutmodule is onbekend.

De fysieke afmetingen, maximale continue modulestroom en instelling van de derde buckconverter zijn niet bevestigd.
