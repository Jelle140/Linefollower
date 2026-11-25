# Bistabiele tuimelschakelaar – Technische specificaties

## Beschrijving

De linefollower beschikt over een bistabiele miniatuur-tuimelschakelaar waarmee de voedingsspanning van de robot handmatig wordt in- en uitgeschakeld.

De schakelaar behoudt zijn mechanische positie nadat de bedieningshendel wordt losgelaten.

## Technische specificaties

| Eigenschap | Specificatie |
|---|---|
| Type | Miniatuur-tuimelschakelaar |
| Contactconfiguratie | SPST (Single Pole Single Throw) |
| Schakelfunctie | ON/OFF |
| Aantal stabiele posities | 2 |
| Aantal aansluitpinnen | 2 |
| Nominale contactspanning volgens opschrift | 125 V AC |
| Nominale contactstroom volgens opschrift | 3 A bij 125 V AC |
| Maximale DC-schakelstroom | Niet bevestigd |
| Geschakelde nominale batterijspanning | 7,4 V DC |
| Maximale batterijspanning | 8,4 V DC |
| Bedieningswijze | Handmatig |
| Montage | Schroefdraad met bevestigingsmoer |
| Aansluitmethode | Soldeeraansluitingen |
| Behuizing | Blauwe kunststof met metalen onderdelen |
| Afmetingen | Niet opgemeten |
| Fabrikant | Onbekend |
| Exact typenummer | Onbekend |

## Pinout

| Pin | Functie |
|---|---|
| 1 | Inkomende voedingsspanning |
| 2 | Uitgaande geschakelde voedingsspanning |

De pinnummering is functioneel gekozen voor de projectdocumentatie. De mechanische schakelaar heeft geen elektrische polariteit.

## Schakeltoestanden

| Positie | Contact tussen pin 1 en pin 2 | Werking |
|---|---|---|
| OFF | Open | Voeding onderbroken |
| ON | Gesloten | Voeding ingeschakeld |

## Elektrisch werkingsprincipe

De schakelaar wordt in serie opgenomen in de voedingskring van de linefollower.

In de ON-positie wordt de voedingskring gesloten en kunnen de buckconverters de elektronische componenten voeden.

In de OFF-positie wordt de voedingskring onderbroken.

De schakelaar wordt uitsluitend gebruikt voor het handmatig in- en uitschakelen van de robot. Er is geen softwarematige aansturing nodig.

## Toepassing in de linefollower

De schakelaar wordt gebruikt in combinatie met:

- Limskey 2S LiPo-batterij van 7,4 V;
- XT60-batterijconnector;
- DC-DC-buckconverter met uitgangsspanning van 5 V;
- DC-DC-buckconverter met uitgangsspanning van 3,3 V.

## Veiligheid

De op de schakelaar vermelde contactwaarde bedraagt 3 A bij 125 V AC.

Deze waarde mag niet rechtstreeks worden geïnterpreteerd als een toegelaten DC-schakelstroom. De geschiktheid voor het schakelen van de volledige DC-belasting moet afzonderlijk worden gecontroleerd.

De soldeeraansluitingen moeten elektrisch geïsoleerd worden om ongewenste kortsluiting te voorkomen.

## Bronnen

### Bron 1 – Opschrift op de gebruikte schakelaar

- Bron: fysieke schakelaar van het gerealiseerde prototype.
- Vindplaats: opschrift op de schakelaarbehuizing.
- Gebruikte informatie: nominale contactwaarde van 3 A bij 125 V AC.

### Bron 2 – Fysieke inspectie

- Bron: eigen foto en inspectie van de gebruikte schakelaar.
- Vindplaats: behuizing, bedieningshendel en aansluitpinnen.
- Gebruikte informatie: twee aansluitpinnen, montagewijze, bedieningswijze en contactconfiguratie.

### Bron 3 – Eigen projectdocumentatie

- Bron: elektronisch schema van de linefollower.
- Vindplaats: `technische tekeningen/elektronisch`.
- Gebruikte informatie: toepassing van de schakelaar in de voedingskring.

## Opmerking

Omdat het exacte merk en typenummer niet bekend zijn, is geen specifieke fabrikantendatasheet beschikbaar.

De bovenstaande technische gegevens zijn gebaseerd op het originele opschrift, fysieke inspectie en de toepassing binnen het gerealiseerde prototype. De maximale DC-schakelstroom en de exacte afmetingen zijn niet bevestigd.
