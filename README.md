# DSMR info <!-- omit in toc -->

Technical information about smart meters in the Netherlands (in Dutch: [slimme meter](https://nl.wikipedia.org/wiki/Slimme_meter)) adhering to the Dutch Smart Meter Requirements. 

## Table of contents  <!-- omit in toc -->
- [General info](#general-info)
- [DSMR versions: standards](#dsmr-versions-standards)
- [P1 port specifications](#p1-port-specifications)
- [Smart Electricity Meters](#smart-electricity-meters)
- [Other related overviews](#other-related-overviews)
- [Features](#features)
- [Status](#status)
- [Contributing](#contributing)
- [License](#license)
- [Credits](#credits)

## General info

In this GitHub repository, we collect public information about various smart meters adhering to the Dutch Smart Meter Requirements (DSMR). While working on the research projects [Twomes](https://edu.nl/9fv8w) and [REDUCEDHEATCARB](https://edu.nl/gutuc) and while developing our open hardware [twomes-p1-gateway-hardware](https://github.com/energietransitie/twomes-p1-gateway-hardware) and the open software [twomes-p1-reader-firmware](https://github.com/energietransitie/twomes-p1-reader-firmware), we noticed that information that was needed to create hardware and software designs that would work on as many smart meter in the Netherlands as possible was scattered all over the internet. In this repository, we aim to bring all this information together, mostly in tabular form as .CSV files.

## DSMR versions: standards 

| DSMR version |       Date | Main standard                                                                                                                             | P1                                                                                                                              | P2                                                                                                                              | P3                                                                                                                              | GPRS                                                                                   | IP  | Release Notes                                                                                                                      |
| :----------- | ---------: | ----------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- | --- | ---------------------------------------------------------------------------------------------------------------------------------- |
| 2.1          | 04-02-2008 |                                                                                                                                           | [P1](https://github.com/reneklootwijk/node-dsmr/blob/master/docs/P1%20Companion%20Standard%202.1.pdf)                           |                                                                                                                                 |                                                                                                                                 |                                                                                        |     |                                                                                                                                    |
| 2.2          | 18-04-2008 |                                                                                                                                           | [P1](https://github.com/reneklootwijk/node-dsmr/blob/master/docs/P1%20Companion%20Standard%202.2.pdf)                           |                                                                                                                                 |                                                                                                                                 |                                                                                        |     |                                                                                                                                    |
| 2.31         | 08-01-2009 |                                                                                                                                           | [P1](https://github.com/reneklootwijk/node-dsmr/blob/master/docs/P1%20Companion%20Standard%202.31.pdf)                          |                                                                                                                                 |                                                                                                                                 |                                                                                        |     |                                                                                                                                    |
| 3.0          | 24-03-2010 | [main](http://77.161.176.191/domoticx/handleidingen/p1-poort/Main%20Document%20DSMR%20v3.0%20%282010-03-24%29%20Netbeheer%20Nederland.7z) | [P1](https://github.com/reneklootwijk/node-dsmr/blob/master/docs/P1%20Companion%20Standard%203.0.pdf)                           |                                                                                                                                 |                                                                                                                                 |                                                                                        |     |                                                                                                                                    |
| 4.0          | 22-04-2011 | [main](https://github.com/matthijskooijman/arduino-dsmr/blob/master/specs/DSMR%20v4.0%20Main%20Document.pdf)                              | [P1](https://github.com/reneklootwijk/node-dsmr/blob/master/docs/P1%20Companion%20Standard%204.0.pdf)                           |                                                                                                                                 |                                                                                                                                 |                                                                                        |     |                                                                                                                                    |
| 4.0.4        | 03-04-2012 |                                                                                                                                           | [P1](https://github.com/reneklootwijk/node-dsmr/blob/master/docs/P1%20Companion%20Standard%204.0.4.pdf)                         |                                                                                                                                 |                                                                                                                                 |                                                                                        |     |                                                                                                                                    |
| 4.0.7        | 14-03-2014 | [main](https://web.archive.org/web/20190524205301/https://www.netbeheernederland.nl/_upload/Files/Slimme_meter_15_91e8f3e526.pdf)         | [P1](https://web.archive.org/web/20190524205310/https://www.netbeheernederland.nl/_upload/Files/Slimme_meter_15_2bff566986.pdf) | [P2](https://web.archive.org/web/20190524205313/https://www.netbeheernederland.nl/_upload/Files/Slimme_meter_15_8b8bc57ddd.pdf) | [P3](https://web.archive.org/web/20190524205318/https://www.netbeheernederland.nl/_upload/Files/Slimme_meter_15_1f3c5c9b2c.pdf) |                                                                                        |     | [notes](https://web.archive.org/web/20190524205321/https://www.netbeheernederland.nl/_upload/Files/Slimme_meter_15_40f025334f.pdf) |
| 4.2.2        | 14-03-2014 | [main](https://www.netbeheernederland.nl/_upload/Files/Slimme_meter_15_7b581ff014.pdf)                                                    | [P1](https://www.netbeheernederland.nl/_upload/Files/Slimme_meter_15_32ffe3cc38.pdf)                                            | [P2](https://www.netbeheernederland.nl/_upload/Files/Slimme_meter_15_5f06987971.pdf)                                            | [P3](https://www.netbeheernederland.nl/_upload/Files/Slimme_meter_15_0e376a0ec9.pdf)                                            | [GPRS](https://www.netbeheernederland.nl/_upload/Files/Slimme_meter_15_b4d3ea07ab.pdf) |     |                                                                                                                                    |
| 4.2.3        | 13-02-2019 | [main](https://www.netbeheernederland.nl/_upload/Files/Slimme_meter_15_bf3be9c18c.pdf)                                                    |                                                                                                                                 |                                                                                                                                 | [P3](https://www.netbeheernederland.nl/_upload/Files/Slimme_meter_15_9e94f87c14.pdf)                                            |                                                                                        |     | [notes](https://www.netbeheernederland.nl/_upload/Files/Slimme_meter_15_edb9de8bb4.pdf)                                            |
| 5.0          | 27-05-2014 |                                                                                                                                           | [P1](https://github.com/reneklootwijk/node-dsmr/blob/master/docs/P1%20Companion%20Standard%205.0.pdf)                           |                                                                                                                                 |                                                                                                                                 |                                                                                        |     |                                                                                                                                    |
| 5.0.2        | 26-02-2016 |                                                                                                                                           | [P1](https://www.netbeheernederland.nl/_upload/Files/Slimme_meter_15_a727fce1f1.pdf)                                            |                                                                                                                                 |                                                                                                                                 |                                                                                        |     |                                                                                                                                    |

## P1 port specifications

[dsmr-p1-specs.csv](dsmr-p1-specs.csv) contains a table with an overview of P1 port specifications for various DSMR versions. 

## Smart Electricity Meters

[dsmr-e-meters.csv](dsmr-e-meters.csv) contains a table with an overview of all smart electricity meters deployed in the Netherlands complying various DSMR versions.

## Other related overviews
* Milieucentraal
  * [P1: overview of realtime energy managers](https://www.milieucentraal.nl/energie-besparen/inzicht-in-je-energierekening/overzicht-energieverbruiksmanagers/#realtime-verbruik)
  * [P4: overview of delayed feedback energy managers](https://www.milieucentraal.nl/energie-besparen/inzicht-in-je-energierekening/overzicht-energieverbruiksmanagers/#vertraagde-feedback)
* Smart meter manuals
  * [Netbeheer Nederland](https://www.netbeheernederland.nl/veelgestelde-vragen)
  * [Enexis](https://www.enexis.nl/meter/handleiding-slimme-meter)
  * [Liander](https://www.liander.nl/mkb/meters/handleidingen/?field_meter_type_value[0]=2&field_smart_meter_value=1)
  * [Stedin](https://www.stedin.net/slimme-meter/overzicht-handleidingen)
    * [Stedin Zeeland f.k.a. Enduris](https://zeeland.stedin.net/slimme-meter/handleidingen)
  * [Coteq](https://coteqnetbeheer.nl/meters-meterstanden/handleidingen)
  * [RENDO](https://www.rendonetwerken.nl/thuis/meter-meterstanden/#info-handleidingen)
 
## Features

Currently ready:

* overview of DSMR versions;
* initial overview of P1 port specifications;
* initial overview of more than 85 smart meters compying with the DSMR standard in the Netherlands;

To-do:

* check recent overviews of published meter codes 

## Status

Dataset is: _work in progress_ 

## Contributing

If you have additional information, please feel free to send in corrections, updates and additions, preferably as a Pull Requests, or as an issue. via this repository. We're very interested in the meter code, but beware NOT to include your serial number. You may not want to share your smart meter serial number publicly: using this serial number, anyone who knows your zip code and street address number can register an account with an Overige Diensten Aanbieder (ODA) and get access to your smart  meter readings. 

The meter code and serial number are typically found combined in the following places:

- As plain text printed below the largest barcode on your smart meter enclosure
- Encoded as the largest barcode on your smart meter enclosure
- Encoded ain the OBIS code `0-0:42.0.0` or `0-0:96.1.1` in P1 telegrams, using a COSEM hexadecimal octet-string encoding, where each character is represented by two hexadecimal characters.

We advise not to share the full barcode, full text or full contents of the OBIS code 0-0:42.0.0 or 0-0:96.1.1 of your P1 telegrams in issues or in Pull Request in this GitHub repository. We ARE very interested in receiving updates of smart meters not yet in the list, including the smart meter code, but you may want to blackline the largest barcode, and serial number. 

If the text below the largest barcode starts with an E, then the following 4 digits are part of the meter code and the digits following contain the serial number. If the text below the largest barcode does NOT start with an E, then the first 4 characters (which may be letters and/or digits) are the meterc ode and the digits following contain the serial number.

## License

This data is made available under the [CC BY 4.0](./LICENSE.md) by the [Research group Energy Transition, Windesheim University of Applied Sciences](https://windesheim.nl/energietransitie) 

## Credits

Data collection was a joint effort of:

* Henri ter Hofte · [@henriterhofte](https://github.com/henriterhofte) · Twitter [@HeNRGi](https://twitter.com/HeNRGi)
* \<place future contributors here\> 
 
We gratefully acknowlegde the efforts of the authors of the following smart meter resources:

* [Netbeheer Nederland dossier slimme meter: documenten ](https://www.netbeheernederland.nl/dossiers/slimme-meter-15/documenten)
* [P1 poort slimme meter (hardware) on domoticx.com](https://domoticx.com/p1-poort-slimme-meter-hardware/)
  * [overview of DSMR standards](http://domoticx.phoenixinteractive.nl/handleidingen/p1-poort)
* [Slimme meter overzicht](https://smartgateways.nl/overzicht-slimme-meters/)
* [node-dsmr/docs](https://github.com/reneklootwijk/node-dsmr/), by [@rekeklootwijk](https://github.com/reneklootwijk)
  * [DSMR P1 standard documents](https://github.com/reneklootwijk/node-dsmr/tree/master/docs)
* [arduino-dsmr](https://github.com/matthijskooijman/arduino-dsmr), by [@matthijskooijman](https://github.com/matthijskooijman)
  * [DSMR standard documents](https://github.com/matthijskooijman/arduino-dsmr)
* [Rejected electricity meters](https://www.rdi.nl/onderwerpen/elektriciteitsmeters-gasmeters-en-warmtemeters/documenten/publicaties/2018/juli/16/overzicht-afgekeurde-meters)
