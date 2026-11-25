# Datasheets

Deze map bevat de beschikbare datasheets, elektronische schema's, pinouts en aanvullende technische specificaties van de componenten die gebruikt worden in de Line Following Robot.

Wanneer geen officiële datasheet van de exacte component of breakoutmodule beschikbaar is, wordt aanvullende technische documentatie voorzien op basis van fabrikantgegevens, fysieke inspectie, componentopschriften en eigen projectdocumentatie.

## Overzicht componenten

| Component | Beschikbare documentatie |
|---|---|
| STM32F103C8T6 | Officiële datasheet |
| STM32 Smart V2.0 | Elektronisch schema en pinout |
| TB6612FNG | Datasheet en modulepinout |
| TCRT5000 | Datasheet en modulespecificaties |
| HM-10 | Datasheet |
| GA12-N20 6 V 300 rpm | Algemene datasheet en aanvullende motorspecificaties |
| 24LC256 | Datasheet |
| Limskey 2S LiPo | Technische specificaties en pinout |
| Bistabiele tuimelschakelaar | Technische specificaties en pinout |
| MP1584EN | Datasheet en modulespecificaties |

## STM32F103C8T6 en STM32 Smart V2.0

De STM32F103C8T6 vormt de centrale microcontroller van de linefollower.

Naast de officiële datasheet van de microcontroller is aanvullende documentatie van het gebruikte STM32 Smart V2.0-ontwikkelbord opgenomen.

Aanvullende bestanden:

- [STM32 Smart V2.0 – elektronisch schema](STM32_Smart_V2.0_Schematic.pdf)
- [STM32 Smart V2.0 – pinout](STM32_Smart_V2.0_Pinout.md)

De aanvullende documentatie bevat:

- technische specificaties van het ontwikkelbord;
- pinvolgorde en pinfuncties;
- beschikbare ADC-kanalen;
- beschikbare PWM-kanalen;
- alternatieve timerfuncties;
- 5 V-tolerantie;
- voedingsaansluitingen;
- SWD-programmeerinterface;
- gebruikte aansluitingen binnen de linefollower.

## TB6612FNG-motordriver

De TB6612FNG wordt gebruikt voor het onafhankelijk aansturen van de twee DC-motoren.

Naast de officiële datasheet van het IC is aanvullende documentatie van de breakoutmodule opgenomen.

Aanvullend bestand:

- [TB6612FNG – modulepinout](TB6612FNG_Module_Pinout.md)

Dit bestand bevat de elektrische specificaties, pinfuncties, referentiepinvolgorde, waarheidstabel en aansluitingen op de STM32.

De fysieke pinvolgorde en afmetingen van de referentiemodule kunnen verschillen van die van de daadwerkelijk gebruikte breakoutmodule.

## TCRT5000-sensormodule

De gebruikte sensormodules bestaan uit een TCRT5000-reflectiesensor en bijkomende elektronische componenten, waaronder een comparator en instelpotentiometer.

De officiële Vishay-datasheet beschrijft de TCRT5000-sensor zelf.

Aanvullend bestand:

- [TCRT5000 – modulespecificaties](TCRT5000_Module_Specificaties.md)

Dit bestand bevat:

- technische specificaties;
- fysieke pinvolgorde;
- analoge en digitale uitgang;
- werkingsprincipe;
- aansluitingen op de STM32;
- toepassing in de finale software;
- verwijzing naar de proof of concept.

In het gerealiseerde prototype worden zes sensormodules gebruikt. Alle zes sensoren worden analoog uitgelezen, waarvan vijf actief deelnemen aan de lijnregeling.

De digitale uitgang wordt niet gebruikt.

## HM-10 Bluetoothmodule

De HM-10 Bluetoothmodule is voorzien in het elektronische ontwerp voor draadloze communicatie.

De beschikbare datasheet is opgenomen in deze map.

Bluetoothcommunicatie is niet geïmplementeerd in de finale lijnvolgsoftware van het Plan-B-prototype.

## GA12-N20 6 V 300 rpm DC-motor

De linefollower wordt aangedreven door twee GA12-N20 DC-motoren met metalen tandwielreductie.

Voor de exacte gebruikte motorvariant is geen officiële fabrikantendatasheet beschikbaar.

De algemene GA12-N20-datasheet wordt daarom aangevuld met afzonderlijke technische documentatie.

Aanvullend bestand:

- [GA12-N20 – motorspecificaties](GA12_N20_300RPM_Specificaties.md)

Dit bestand bevat:

- technische specificaties volgens de oorspronkelijke componentkeuze;
- nominale spanning;
- opgegeven toerental;
- elektrische aansluitingen;
- aansluiting op de TB6612FNG;
- wielafmetingen;
- theoretische berekening van de rijsnelheid.

De theoretische rijsnelheid bij 300 rpm en een wieldiameter van 44 mm bedraagt ongeveer 0,69 m/s.

De exacte nominale stroom, blokkeerstroom, reductieverhouding en het motorkoppel zijn niet bevestigd.

## 24LC256 EEPROM

De 24LC256 is een extern EEPROM-geheugen met I²C-interface.

De officiële datasheet is opgenomen in deze map.

Het geheugen is voorzien in het elektronische ontwerp, maar wordt niet actief gebruikt in de finale lijnvolgsoftware.

## Limskey 2S LiPo-batterij

De linefollower wordt gevoed door een Limskey lithium-polymeerbatterij.

De belangrijkste specificaties zijn:

- Configuratie: 2S.
- Nominale spanning: 7,4 V.
- Maximale laadspanning: 8,4 V.
- Capaciteit: 1500 mAh.
- Ontlaadfactor: 45C.
- Kortstondige ontlaadfactor: 60C.
- Hoofdconnector: XT60.
- Balansconnector: driepolig.

Aanvullend bestand:

- [LiPo 2S – technische specificaties](LiPo_2S_Specificaties.md)

De technische documentatie is gebaseerd op het originele batterijlabel, fysieke inspectie en eigen technische berekeningen.

## Bistabiele tuimelschakelaar

De hoofdvoeding van de linefollower wordt handmatig geschakeld met een bistabiele SPST-tuimelschakelaar.

De belangrijkste specificaties zijn:

- Schakelfunctie: ON/OFF.
- Aantal aansluitpinnen: 2.
- Contactwaarde volgens opschrift: 3 A bij 125 V AC.
- Geschakelde nominale batterijspanning: 7,4 V DC.
- Montage: schroefdraad met bevestigingsmoer.

Aanvullend bestand:

- [Schakelaar – technische specificaties](Schakelaar_Specificaties.md)

De maximale DC-schakelstroom is niet bevestigd. De vermelde AC-contactwaarde mag niet rechtstreeks als DC-contactwaarde worden geïnterpreteerd.

## MP1584EN-buckconverter

De voedingsregeling van de linefollower gebeurt met instelbare MP1584EN DC-DC-step-downconverters.

De belangrijkste gedocumenteerde voedingsspanningen zijn:

- 3,3 V voor de logische componenten;
- 5 V voor de STM32 en de gedocumenteerde motorvoeding.

Op het gerealiseerde prototype zijn drie MP1584EN-modules aanwezig. De exacte instelling en functie van de derde module zijn nog niet bevestigd.

Aanvullende bestanden:

- [MP1584EN – officiële datasheet](MP1584EN_Datasheet.pdf)
- [MP1584EN – modulespecificaties](MP1584EN_Module_Specificaties.md)

De aanvullende documentatie bevat de elektrische specificaties, pinout, het werkingsprincipe en de toepassing binnen de linefollower.

De officiële datasheet beschrijft het regel-IC. De maximaal toelaatbare continue uitgangsstroom van de volledige breakoutmodule is niet afzonderlijk bevestigd.

## Bronnen en traceerbaarheid

De aanvullende technische documenten bevatten afzonderlijke bronvermeldingen met:

- Bron: fabrikant, datasheet, componentopschrift of eigen projectdocumentatie.
- Vindplaats: relevante sectie, onderdeel of bestandslocatie.
- Gebruikte informatie: technische gegevens die uit de betreffende bron zijn overgenomen.

De documentatie is gebaseerd op:

- officiële fabrikantendatasheets;
- documentatie van ontwikkelborden en breakoutmodules;
- fysieke inspectie van het gerealiseerde prototype;
- originele componentopschriften;
- elektronische en mechanische schema's;
- bill of materials;
- proof of concepts;
- finale broncode;
- eigen technische berekeningen.

## Beperkingen

Niet voor iedere gebruikte breakoutmodule of componentvariant is een officiële fabrikantendatasheet beschikbaar.

Ontbrekende technische eigenschappen, waaronder bepaalde afmetingen, stroomwaarden, typenummers en module-instellingen, worden expliciet als niet bevestigd vermeld in de aanvullende documentatie.

Algemene datasheets worden uitsluitend als referentie gebruikt wanneer de exacte componentvariant niet geïdentificeerd kan worden.

Voor alle hierboven vermelde componenten is technische documentatie opgenomen, hetzij in de vorm van een datasheet, hetzij in de vorm van aanvullende Markdown-documentatie.
