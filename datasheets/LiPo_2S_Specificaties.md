# Limskey LiPo 2S – Technische specificaties

## Beschrijving

De linefollower wordt gevoed door een oplaadbare lithium-polymeerbatterij (LiPo) van het merk Limskey.

De batterij bestaat uit twee in serie geschakelde cellen (2S) en levert de voedingsspanning voor de buckconverters van de robot.

## Technische specificaties

| Eigenschap | Specificatie |
|---|---|
| Merk | Limskey |
| Batterijtechnologie | Lithium-polymeer (LiPo) |
| Configuratie | 2S |
| Aantal cellen | 2 |
| Nominale celspanning | 3,7 V |
| Nominale batterijspanning | 7,4 V |
| Maximale laadspanning | 8,4 V |
| Capaciteit | 1500 mAh |
| Nominale energie-inhoud | 11,1 Wh |
| Ontlaadfactor | 45C |
| Kortstondige ontlaadfactor | 60C |
| Theoretische continue ontlaadstroom | 67,5 A |
| Theoretische kortstondige ontlaadstroom | 90 A |
| Hoofdconnector | XT60 |
| Balansconnector | 3-polig, vermoedelijk JST-XH |
| Afmetingen | Nog niet opgemeten |

De ontlaadfactoren zijn afkomstig van het batterijlabel. De werkelijke maximaal toelaatbare stroom is niet onafhankelijk getest.

## Berekeningen

### Nominale spanning

U = 2 × 3,7 = 7,4 V

### Maximale laadspanning

Umax = 2 × 4,2 = 8,4 V

### Continue ontlaadstroom

I = 1,5 × 45 = 67,5 A

### Kortstondige ontlaadstroom

Iburst = 1,5 × 60 = 90 A

### Energie-inhoud

E = 7,4 × 1,5 = 11,1 Wh

## Aansluitingen

### XT60-hoofdconnector

| Draadkleur | Functie |
|---|---|
| Rood | Positieve batterijspanning |
| Zwart | Negatieve batterijspanning / GND |

### Balansconnector

| Aansluiting | Functie | Nominale spanning tegenover B- |
|---|---|---|
| B- | Negatieve aansluiting cel 1 | 0 V |
| B1 | Verbinding tussen cel 1 en cel 2 | 3,7 V |
| B+ | Positieve aansluiting cel 2 | 7,4 V |

De tabel geeft de elektrische aansluitvolgorde weer. De fysieke oriëntatie en polariteit van de connector moeten vóór aansluiting gecontroleerd worden.

## Toepassing in de linefollower

De batterij voedt twee DC-DC-buckconverters.

- Buckconverter 1: uitgangsspanning 5 V.
- Buckconverter 2: uitgangsspanning 3,3 V.

Hierdoor worden de verschillende elektronische componenten voorzien van hun vereiste voedingsspanning.

De batterijvoeding wordt in- en uitgeschakeld via een bistabiele schakelaar.

## Veiligheidsvoorschriften

- Gebruik uitsluitend een geschikte LiPo-balanslader.
- Selecteer de correcte 2S-laadconfiguratie.
- Overschrijd nooit 4,2 V per cel.
- Vermijd diepontlading en kortsluiting.
- Gebruik geen beschadigde of opgezwollen batterij.
- Laat de batterij tijdens het opladen niet onbeheerd achter.
- Respecteer de maximale stroom van de bekabeling, connectoren en schakelaar.

## Bronnen

### Bron 1 – Origineel batterijlabel

- Bron: fysieke Limskey LiPo-batterij van het gerealiseerde prototype.
- Vindplaats: etiket op de batterijbehuizing.
- Gebruikte informatie: merk, capaciteit, ontlaadfactor en kortstondige ontlaadfactor.

### Bron 2 – Fysieke inspectie

- Bron: eigen foto en inspectie van de gebruikte batterij.
- Vindplaats: hoofdconnector en driepolige balansconnector.
- Gebruikte informatie: XT60-aansluiting en bevestiging van de 2S-configuratie.

### Bron 3 – Eigen technische berekeningen

- Bron: batterijgegevens en standaard celspanningen van conventionele LiPo-cellen.
- Gebruikte informatie: nominale spanning, maximale laadspanning, energie-inhoud en theoretische ontlaadstromen.

### Bron 4 – Eigen projectdocumentatie

- Bron: elektronisch schema van de linefollower.
- Vindplaats: `technische tekeningen/elektronisch`.
- Gebruikte informatie: toepassing van de batterij, schakelaar en buckconverters.

## Opmerking

Een officiële datasheet van het exacte batterijmodel is niet beschikbaar in de repository. Daarom zijn de technische specificaties gebaseerd op het originele batterijlabel, fysieke inspectie en technische berekeningen.
