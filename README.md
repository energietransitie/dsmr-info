# DSMR info 
Technical information about smart meters in the Netherlands (in Dutch: [slimme meter](https://nl.wikipedia.org/wiki/Slimme_meter)) adhering to the Dutch Smart Meter Requirements. 

## Table of contents
* [General info](#general-info)
* [DSMR versions](#dsmr-versions) 
* [P1 port specifications](#p1-port) 
* [Smart electricity meters](#smart-electricity-meters) 
* [Features](#features)
* [Status](#status)
* [Contributing](#contributing)
* [License](#license)
* [Credits](#credits)

## General info

In this GitHub repository, we collect public information about various smart meters adhering to the Dutch Smart Meter Requirements (DSMR). While working on the research projects [Twomes](https://edu.nl/9fv8w) and [REDUCEDHEATCARB](https://edu.nl/gutuc) and while developing our open hardware [twomes-p1-gateway-hardware](https://github.com/energietransitie/twomes-p1-gateway-hardware) and the open software [twomes-p1-reader-firmware](https://github.com/energietransitie/twomes-p1-reader-firmware), we noticed that information that was needed to create hardware and software designs that would work on as many smart meter in the Netherlands as possible was scattered all over the internet. In this repository, we aim to bring all this information together, mostly in tabular form as .CSV files.

# DSMR versions

| DSMR version | date standardized | link to P1 standard |
| -----------: | ----------------: | ------------------- |
| 2.1          | 4-2-2008          | TODO                |
| 2.2          | 18-4-2008         | TODO                |
| 2.31         | 8-1-2009          | TODO                |
| 3.0          | 24-3-2010         | TODO                |
| 4.0          | 22-4-2011         | TODO                |
| 4.0.4        | 3-4-2012          | TODO                |
| 4.2.2        | 14-3-2014         | TODO                |
| 4.2.3        | 13-2-2019         | TODO                |
| 5.0          | 27-5-2014         | TODO                |
| 5.0.2        | 26-2-2016         | TODO                |

## P1 port specifications

The file [dsmr-p1-specs.csv](dsmr-p1-specs.csv) contains a table with an overview of P1 port specifications for various DSMR versions. 

## Smart Electricity Meters

The file [dsmr-e-meters.csv](dsmr-e-meters.csv) contains a table with an overview of all smart electricity meters deployed in the Netherlands complying various DSMR versions.

## Features

Currently ready:

* overview of DSMR versions;
* initial overview of P1 port specifications;
* initial overview of more than 65 smart meters currently deployed in the Netherlands;

To-do:

* add links to DSMR specification documents
* check whether hosting (older) DSMR specification documents on GitHub is ok
* harvest more info from (photos in) [Liander smart meter manuals](https://www.liander.nl/mkb/meters/handleidingen/?field_meter_type_value[0]=2&field_smart_meter_value=1)

## Status

Dataset is: _work in progress_ 

## Contributing

If you have additional information, please feel free to send in corrections, updates and additions, preferably as a Pull Requests, or as an issue. via this repository. We're very interested in the meter code, but beware NOT to include your serial number. You may not want to share your smart meter serial number publicly: using this serial number, anyone who knows your zip code and street address number can register an account with an Overige Diensten Aanbieder (ODA) and get access to your smart  meter readings. 

The meter code and serial number are typically found combined in the following places:

- As plain text printed below the largest barcode on your smart meter enclosure
- Encoded as the largest barcode on your smart meter enclosure
- Encoded ain the OBIS code 0-0:42.0.0 or 0-0:96.1.1 in P1 telegrams, using a COSEM hexadecimal octet-string encoding, where each character is represented by two hexadecimal characters.

We advise not to share the full barcode, full text or full contents of the OBIS code 0-0:42.0.0 or 0-0:96.1.1 of your P1 telegrams in issues or in Pull Request in this GitHub repository. We ARE very interested in receiving updates of smart meters not yet in the list, including the smart meter code, but you may want to blackline the largest barcode, and serial number. 

If the text below the largest barcode starts with an E, then the following 4 digits are part of the meter code and the digits following contain the serial number. If the text below the largest barcode does NOT start with an E, then the first 4 characters (which may be letters and/or digits) are the meterc ode and the digits following contain the serial number.

## License

This data is made available under the [CC BY 4.0](./LICENSE.md) by the [Research group Energy Transition, Windesheim University of Applied Sciences](https://windesheim.nl/energietransitie) 

## Credits

Data collection was a joint effort of:

* Henri ter Hofte · [@henriterhofte](https://github.com/henriterhofte) · Twitter [@HeNRGi](https://twitter.com/HeNRGi)
* \<place future contributors here\> 
 
We gratefully acknowlegde the efforts of the composers of the following smart meter resources:

* [Netbeheer Nederland dossier slimme meter: documenten ](https://www.netbeheernederland.nl/dossiers/slimme-meter-15/documenten)
* [P1 poort slimme meter (hardware) on domoticx.com](https://domoticx.com/p1-poort-slimme-meter-hardware/)
* [Enexis smart meter manuals](https://www.enexis.nl/meter/handleiding-slimme-meter)
* [Liander smart meter manuals](https://www.liander.nl/mkb/meters/handleidingen/?field_meter_type_value[0]=2&field_smart_meter_value=1)
 
