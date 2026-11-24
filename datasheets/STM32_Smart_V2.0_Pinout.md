# STM32 Smart V2.0 – Pinout en technische specificaties

## Algemene specificaties

| Eigenschap | Specificatie |
|---|---|
| Ontwikkelbord | STM32 Smart V2.0 |
| Microcontroller | STM32F103C8T6 |
| Processor | ARM Cortex-M3 |
| Maximale klokfrequentie | 72 MHz |
| Flashgeheugen | 64 kB |
| SRAM | 20 kB |
| Logische spanning | 3,3 V |
| Voedingsingang | 5 V of 3,3 V |
| ADC-resolutie | 12 bit |
| Afmetingen PCB | 42 × 54 mm |
| Programmeerinterface | SWD / JTAG |
| Spanningsregelaar | AMS1117-3.3 |

## Pinout Header 1

| Positie | Pin | Functie |
|---|---|---|
| 1 | GND | Massa |
| 2 | BT0 | Bootselectie |
| 3 | 3V3 | Voeding 3,3 V |
| 4 | PB9 | GPIO / TIM4_CH4 |
| 5 | PB8 | GPIO / TIM4_CH3 |
| 6 | PB7 | GPIO / I2C1_SDA / TIM4_CH2 |
| 7 | PB6 | GPIO / I2C1_SCL / TIM4_CH1 |
| 8 | PB5 | GPIO / TIM3_CH2 bij remap |
| 9 | PB4 | GPIO / JTAG / TIM3_CH1 bij remap |
| 10 | PB3 | GPIO / JTAG / TIM2_CH2 bij remap |
| 11 | PA15 | GPIO / JTAG / TIM2_CH1 bij remap |
| 12 | PA12 | GPIO / USB_DP |
| 13 | PA11 | GPIO / USB_DM / TIM1_CH4 |
| 14 | PA10 | GPIO / USART1_RX / TIM1_CH3 |
| 15 | PA9 | GPIO / USART1_TX / TIM1_CH2 |
| 16 | PA8 | GPIO / TIM1_CH1 / MCO |
| 17 | PB15 | GPIO / SPI2_MOSI / TIM1_CH3N |
| 18 | PB14 | GPIO / SPI2_MISO / TIM1_CH2N |
| 19 | PB13 | GPIO / SPI2_SCK / TIM1_CH1N |
| 20 | PB12 | GPIO / SPI2_NSS / TIM1_BKIN |

## Pinout Header 2

| Positie | Pin | Functie |
|---|---|---|
| 1 | 3V3 | Voeding 3,3 V |
| 2 | GND | Massa |
| 3 | VBAT | Voeding back-updomein |
| 4 | PC13 | GPIO / ingebouwde LED |
| 5 | PC14 | GPIO / OSC32_IN |
| 6 | PC15 | GPIO / OSC32_OUT |
| 7 | VDDA | Analoge voedingsspanning |
| 8 | PA0 | GPIO / ADC_IN0 / TIM2_CH1 |
| 9 | PA1 | GPIO / ADC_IN1 / TIM2_CH2 |
| 10 | PA2 | GPIO / ADC_IN2 / USART2_TX / TIM2_CH3 |
| 11 | PA3 | GPIO / ADC_IN3 / USART2_RX / TIM2_CH4 |
| 12 | PA4 | GPIO / ADC_IN4 / SPI1_NSS |
| 13 | PA5 | GPIO / ADC_IN5 / SPI1_SCK |
| 14 | PA6 | GPIO / ADC_IN6 / SPI1_MISO / TIM3_CH1 |
| 15 | PA7 | GPIO / ADC_IN7 / SPI1_MOSI / TIM3_CH2 |
| 16 | PB0 | GPIO / ADC_IN8 / TIM3_CH3 |
| 17 | PB1 | GPIO / ADC_IN9 / TIM3_CH4 |
| 18 | PB2 | GPIO / BOOT1 |
| 19 | PB10 | GPIO / I2C2_SCL / USART3_TX |
| 20 | PB11 | GPIO / I2C2_SDA / USART3_RX |

De tabellen vermelden de belangrijkste pinfuncties. Voor alle alternatieve functies en remapmogelijkheden wordt verwezen naar de datasheet van STMicroelectronics.

## Analoge ingangen (ADC)

| Pin | ADC-kanaal | Toepassing linefollower |
|---|---|---|
| PA0 | ADC1_IN0 | Sensor S0 |
| PA1 | ADC1_IN1 | Sensor S1 |
| PA2 | ADC1_IN2 | Niet gebruikt als ADC |
| PA3 | ADC1_IN3 | Niet gebruikt als ADC |
| PA4 | ADC1_IN4 | Sensor S2 |
| PA5 | ADC1_IN5 | Sensor S3 |
| PA6 | ADC1_IN6 | Sensor S4 |
| PA7 | ADC1_IN7 | Sensor S5 |
| PB0 | ADC1_IN8 | Niet gebruikt als ADC |
| PB1 | ADC1_IN9 | Niet gebruikt als ADC |

De ADC heeft een resolutie van 12 bit. De digitale meetwaarden liggen tussen 0 en 4095.

Bij een analoge referentiespanning van 3,3 V komt dit overeen met een analoog meetbereik van 0 tot 3,3 V.

## PWM-uitgangen

| Timer | Kanaal | Standaardpin | Alternatieve pin |
|---|---|---|---|
| TIM1 | CH1 | PA8 | - |
| TIM1 | CH2 | PA9 | - |
| TIM1 | CH3 | PA10 | - |
| TIM1 | CH4 | PA11 | - |
| TIM2 | CH1 | PA0 | PA15 |
| TIM2 | CH2 | PA1 | PB3 |
| TIM2 | CH3 | PA2 | PB10 |
| TIM2 | CH4 | PA3 | PB11 |
| TIM3 | CH1 | PA6 | PB4 |
| TIM3 | CH2 | PA7 | PB5 |
| TIM3 | CH3 | PB0 | - |
| TIM3 | CH4 | PB1 | - |
| TIM4 | CH1 | PB6 | - |
| TIM4 | CH2 | PB7 | - |
| TIM4 | CH3 | PB8 | - |
| TIM4 | CH4 | PB9 | - |

De alternatieve pinnen vereisen de juiste AFIO-remapconfiguratie.

Voor de linefollower worden de volgende PWM-uitgangen gebruikt:

- PA8: TIM1_CH1 voor motor A.
- PB3: TIM2_CH2 met partial remap voor motor B.

Om PB3 als PWM-uitgang te gebruiken, wordt JTAG uitgeschakeld met behoud van SWD.

## 5 V-tolerantie

De STM32F103C8T6 werkt met een logische spanning van 3,3 V. Niet alle GPIO-pinnen zijn geschikt voor digitale ingangssignalen van 5 V.

| Pinnen | 5 V-tolerant |
|---|---|
| PA0 t.e.m. PA7 | Nee |
| PA8 t.e.m. PA15 | Ja, FT |
| PB0 en PB1 | Nee |
| PB2 t.e.m. PB4 | Ja, FT |
| PB5 | Nee |
| PB6 t.e.m. PB15 | Ja, FT |
| PC13 t.e.m. PC15 | Nee |

FT betekent Five-volt Tolerant.

Deze tolerantie geldt uitsluitend onder de bedrijfsvoorwaarden beschreven in de datasheet van de microcontroller. Een FT-pin levert zelf geen uitgangsspanning van 5 V.

De analoge ADC-ingangen mogen niet rechtstreeks worden aangesloten op signalen van 5 V.

## Aansluitingen van de linefollower

| STM32-pin | Aangesloten component | Functie |
|---|---|---|
| PA0 | TCRT5000 S0 | Analoge ingang |
| PA1 | TCRT5000 S1 | Analoge ingang |
| PA4 | TCRT5000 S2 | Analoge ingang |
| PA5 | TCRT5000 S3 | Analoge ingang |
| PA6 | TCRT5000 S4 | Analoge ingang |
| PA7 | TCRT5000 S5 | Analoge ingang |
| PA8 | TB6612FNG PWMA | PWM motor A |
| PB3 | TB6612FNG PWMB | PWM motor B |
| PB13 | TB6612FNG AIN1 | Draairichting motor A |
| PB12 | TB6612FNG AIN2 | Draairichting motor A |
| PB15 | TB6612FNG BIN1 | Draairichting motor B |
| PA9 | TB6612FNG BIN2 | Draairichting motor B |
| PB14 | TB6612FNG STBY | Motorsturing inschakelen |
| PA13 | SWDIO | Programmeerinterface |
| PA14 | SWCLK | Programmeerinterface |
| 5V | Buckconverter | Voeding STM32-bord |
| 3V3 | TCRT5000-sensoren | Sensorvoeding |
| GND | Gemeenschappelijke massa | Referentiepotentiaal |

## Voedingsaansluitingen

Het ontwikkelbord beschikt over een geïntegreerde AMS1117-spanningsregelaar die de 5 V-voeding omzet naar 3,3 V.

De 5 V-aansluiting van de USB-connector is rechtstreeks verbonden met de 5 V-pinnen van het ontwikkelbord. Externe 5 V-voeding en USB-voeding mogen daarom niet gelijktijdig worden aangesloten zonder geschikte beveiliging.

## Bronnen

### Bron 1 – STM32-base

- Bron: https://stm32-base.org/boards/STM32F103C8T6-STM32-Smart-V2.0.html
- Vindplaats: Microcontroller, Power, Regulator, PCB en Connectors & headers.
- Gebruikte informatie: specificaties van het ontwikkelbord, fysieke pinvolgorde, voedingsaansluitingen en programmeerinterface.

### Bron 2 – STMicroelectronics

- Bron: https://www.st.com/resource/en/datasheet/stm32f103c8.pdf
- Document: STM32F103x8 / STM32F103xB datasheet.
- Vindplaats: Pinouts and pin description, Medium-density STM32F103xx pin definitions en Electrical characteristics.
- Gebruikte informatie: GPIO-functies, ADC-kanalen, timerkanalen, alternatieve pinfuncties en 5 V-tolerantie.

### Bron 3 – STMicroelectronics RM0008

- Bron: https://www.st.com/resource/en/reference_manual/cd00171190.pdf
- Vindplaats: GPIO and alternate function I/O, Analog-to-digital converter en Timers.
- Gebruikte informatie: ADC-configuratie, timerfunctionaliteit en AFIO-remapping.

### Bron 4 – Eigen projectdocumentatie

- Bron: elektronisch schema en finale broncode van de linefollower.
- Vindplaats: `technische tekeningen/elektronisch` en `code/finaal/Src`.
- Gebruikte informatie: daadwerkelijk gebruikte aansluitingen voor sensoren, motorsturing en voeding.
