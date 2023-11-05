# twomes-dataset-template
TO DO: Replace this text with a very short description of the dataset. 

## Table of contents
* [General info](#general-info)
* [Subject Recruitment](#recruitment)
* [Inclusion criteria](#inclusion-criteria)
* [Data](#data) 
* [Status](#status)
* [License](#license)
* [Credits](#credits)

## General info

TO DO: Replace this text by general info about the dataset, e.g. generic description of subjects and when the data was collected. 

**Note**: [Git LFS](https://git-lfs.github.com/) is required to clone big CSV files

## Recruitment 

Replace this text that desribes how subjects were recruited, possibly including links to recruitment material used. 

## Inclusion criteria

Inclusion criteria were:
* replace with inclusion criterion 1;
* replace with inclusion criterion 2;
* etc.

## Data management

TO DO: Replace this text with (links to) data management plan, privacy policy and (if applicable), DPIA.

## Data

In the sections below, the data pre-processing and data formats used in the data files will be described.

### Subjects 

TODO: describe

### Measurement Devices 

We used the following measurement device types to collect data. Some devices consisted of a main device and one or two satellite devices. 

TO DO: Change the markdown table below as needed.

| Device type name             | Category                                                | Main device repo                                                                                           | Sattelite device 2 repo                                                                          | Sattelite device 2 repo                                                                              |
| ---------------------------- | ------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------- |
| `OpenTherm-Monitor`          | comfort + installation + occupancy                      | [twomes-opentherm-monitor-firmware](https://github.com/energietransitie/twomes-opentherm-monitor-firmware) |                                                                                                  |                                                                                                      |
| `DSMR-P1-gateway`            | energy                                                  | [twomes-p1-gateway-firmware](https://github.com/energietransitie/twomes-p1-gateway-firmware)               |                                                                                                  |                                                                                                      |
| `DSMR-P1-gateway-Tin`        | energy + comfort                                        | [twomes-p1-gateway-firmware](https://github.com/energietransitie/twomes-p1-gateway-firmware)               | [twomes-room-monitor-firmware](https://github.com/energietransitie/twomes-room-monitor-firmware) |                                                                                                      |
| `DSMR-P1-gateway-TinTsTr`    | energy + comfort + installation                         | [twomes-p1-gateway-firmware](https://github.com/energietransitie/twomes-p1-gateway-firmware)               | [twomes-room-monitor-firmware](https://github.com/energietransitie/twomes-room-monitor-firmware) | [twomes-boiler-monitor-firmware](https://github.com/energietransitie/twomes-boiler-monitor-firmware) |
| `DSMR-P1-gateway-TinTsTrCO2` | energy + comfort + installation + occupancy/ventilation | [twomes-p1-gateway-firmware](https://github.com/energietransitie/twomes-p1-gateway-firmware)               | [twomes-room-monitor-firmware](https://github.com/energietransitie/twomes-room-monitor-firmware) | [twomes-boiler-monitor-firmware](https://github.com/energietransitie/twomes-boiler-monitor-firmware) |

### Date and time information

All timestamps were measured in [Unix time](https://en.wikipedia.org/wiki/Unix_time) format, using device clocks regularly synchronized via NTP with the correct UTC time. Setting the local device clock to the proper UTC time via NTP was one of the first steps performed by the measurement devices after they were connected to the internet via the home Wi-Fi network of a subject. Each measurement device synchronized its device clock via NTP every 6 hours. Uploads of measurement data (which could contain more than one measurement) were timestamped both by the measurement device according to the local device clock and by the server. We did not yet check for deviations between the last device timestamp of a measurement upload and the upload timestamp at the server.

Timestamps were converted to a timezone-aware `pandas.Timestamp` value, in the [Europe/Amsterdam](https://en.wikipedia.org/wiki/Time_in_the_Netherlands) timezone. In the csv files we use [ISO 8601 format with time offset](https://en.wikipedia.org/wiki/ISO_8601): `YYYY-MM-DDThh:mm:ss±hhmm`.

### Raw measurements 
 Raw masurements will be available in the folder [/raw-measurements/](/raw-measurements/) in three formats:

 - [twomes_raw_measurements.parquet](/raw-measurements/twomes_raw_measurements.parquet): a single [parquet](https://parquet.apache.org/) file with data for all subject ids;
 - nnnnnn_raw_measurements.parquet: [parquet](https://parquet.apache.org/) files, one for each subject id;
 - nnnnnn_raw_measurements.zip: [zip](https://en.wikipedia.org/wiki/ZIP_(file_format))ped [csv](https://en.wikipedia.org/wiki/Comma-separated_values) files, one for each subject id;

All measurement data is structured according to the table below. By importing the parquet variant using [pandas.read_parquet()](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.read_parquet.html), you automatically get a DataFrame wih the recommended indices and data types. 

Alternatively, you can also read the zipped csv files, but this typically takes much longer. You can use the code below to endup with a DataFrame with the recommended indices and data types:

```
TODO: insert pandas.read_csv() code here
```

| **Index/Column** | **Name** | **Type**     | **Description**                                                                                                                                       |
| ---------- | --------------- | ------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------- |
| index       | `id`            | `category`   | unique code of the home                                                                                                                               |
| index       | `device_name`   | `category`   | unique name of the measurement device                                                                                                                 |
| index       | `source`        | `category`   | [device type name](###measurement-devices) of the measurement device                                                                                  |
| index        | `timestamp`     | `Timestamp` | start of the interval (timezone aware) |
| index       | `property`      | `category`   | property name of the measurement                                                                                                                      |
| column      | `value`         | `object`     | value of the measurement                                                                                                                              |
| column      | `unit`          | `category`   | unit of the measurement value                                                                                                                         |

### Raw propertes 
 In the folder [/raw-properties/](/raw-properties/) we will make various measured properties available in an 'unstacked' format with each property in its own column and an appropriate datatype. Similar to measurements, we will make data available in three formats:

 - [twomes_raw_properties.parquet](/raw-properties/twomes_raw_measurements.parquet): a single [parquet](https://parquet.apache.org/) file with data for all subject ids;
 - nnnnnn_raw_properties.parquet: [parquet](https://parquet.apache.org/) files, one for each subject id;
 - nnnnnn_raw_properties.zip: 23 [zip](https://en.wikipedia.org/wiki/ZIP_(file_format))ped [csv](https://en.wikipedia.org/wiki/Comma-separated_values) files, one for each subject id;

All property data is structured according to the table below. By importing the parquet variant using [pandas.read_parquet()](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.read_parquet.html), you automatically get a DataFrame wih the recommended indices and data types. 

Alternatively, you can also read the zipped csv files, but this typically takes much longer. You can use the code below to endup with a DataFrame with the recommended indices and data types:

```
TODO: insert pandas.read_csv() code here
```

| **Index/Column** | **Name**                             | **Type**    | **Description**                                              |
| ---------------- | ------------------------------------ | ----------- | ------------------------------------------------------------ |
| index            | `id`                                 | `category`  | unique code of the home                                      |
| index            | `source`                             | `category`  | [device type name](###measurement-devices) of the measurement device |
| index            | `timestamp`                          | `Timestamp` | start of the interval (timezone aware)                       |
| column           | property_1; see property table below | data_type_1 | measured value of this property                              |
| column           | property2                            | data_type_2 | measured value of this property                              |
| ...              | ...                                  | ...         | ...                                                          |
| column           | property_n                           | data_type_n | measured value of this property                              |

### Measured Properties 

Below is a table that lists all properties that were measured, the data type in the [raw-properties](#raw-poperties) DataFrame, the measurement unit, the measurement interval, the source device and sensor that measured it, as well as the the property name and value format as retrieved from the Twomes database.

TO DO: Change the markdown table below as needed.

| Property   | Type      | Unit | Measurement interval \[h:mm:ss\] | Description       | Source                       | Sensor                                                 | Database property  | [Database format](https://en.wikipedia.org/wiki/Printf_format_string) |
| ---------- | --------- | ---- | -------------------------------- | ----------------- | ---------------------------- | ------------------------------------------------------ | ------------------ | ------------------------------------------------------------ |
| `co2__ppm` | `float32` | ppm  | 0:05:00                          | CO₂ concentration | `DSMR-P1-gateway-TinTsTrCO2` | [SCD41](https://sensirion.com/products/catalog/SCD41/) | `CO2concentration` | %d                                                           |

Weather data was collected and geospatially interpolated using [HourlyHistoricWeather](https://github.com/stephanpcpeters/HourlyHistoricWeather) from the Royal Netherlands Meteorological Institute ([KNMI](https://www.knmi.nl/over-het-knmi/about)), based on average hourly values. 

TO DO: change the 
For all subject ids, we used the same location for geospatial interpolation of weather data:
[`lat, lon = 52.xxxxx, 6.yyyyy`](https://www.openstreetmap.org/?mlat=52.xxxxx&mlon=6.yyyyy#map=17/52.xxxxx/6.yyyyy). Average values were converted from the source units to the units as indicated in the table below. 


| Index/Column | Property         | Type        | Unit            | Measurement interval \[h:mm:ss\] | Description                       | Source | [Source property](https://www.daggegevens.knmi.nl/klimatologie/uurgegevens) | [Source value format](https://en.wikipedia.org/wiki/Printf_format_string) | Source unit                                        |
| ------------ | ---------------- | ----------- | --------------- | -------------------------------- | --------------------------------- | ------ | ------------------------------------------------------------ | ------------------------------------------------------------ | -------------------------------------------------- |
| index        | `timestamp`      | `Timestamp` |                 |                                  | start of the measurement interval | KNMI   | `YYYMMDD`, `H`                                               |                                                              | H=1: 0:00:00 - 0:59:59; H=24: 23:00:00 - 23:59:59; |
| column       | `temp_out__degC` | `float32`   | °C              | 1:00:00                          | outdoor temperature               | KNMI   | ` T`                                                         | %d                                                           | 0.1&nbsp;°C                                        |
| column       | `wind__m_s_1`    | `float32`   | m/s             | 1:00:00                          | wind speed                        | KNMI   | ` FH`                                                        | %d                                                           | 0.1&nbsp;m/s                                       |
| column       | `ghi__W_m_2`     | `float32`   | W/m<sup>2</sup> | 1:00:00                          | global horizontal irradiance      | KNMI   | ` Q`                                                         | %d                                                           | J/(h·cm<sup>2</sup>)                               |


### Preprocessed data 

TO DO: change preprocessing description below.

Preprocessing of measurements from the measurement database was done using [get_preprocessed_homes_data()](https://github.com/energietransitie/twomes-twutility-inverse-grey-box-analysis/blob/main/data/extractor.py). Preprocessing steps include:
- removal of duplicate measurements;
- calculation of derived properties as a combination of other properties, as indicated in the column `Calculation` in the table below;
- removal of absolute outliers, i.e measurement values smaller than the value in the column `Min` or larger than the value in the column `Max` in the table below;
- removal of statistic outliers, i.e. measuremnt values with an absolute [z-score](https://en.wikipedia.org/wiki/Standard_score) higer than the value indicated in the `Sigma` column in he table below;
- interpolation of measurements to intervals of 15 minutes (no interpolation between measurements that were 60 minutes apart or more);
- All column values represent the average during the interval that starts at the timestamp indicated. 

TO DO: Change the markdown table below.

| **Index/  Column** | **Name**      | **Type**    | **Unit**        | **Description**                                     | **Calculation** |    Min |    Max | Sigma |
| ------------------ | ------------- | ----------- | --------------- | --------------------------------------------------- | --------------- | -----: | -----: | ----: |
| index              | `id`          | `Int16`     |                 | unique code of the home                             |                 | 000000 | 999999 |       |
| index              | `timestamp`   | `Timestamp` |                 | start of the interpolated interval (timezone aware) |                 |        |        |       |
| column             | `T_out__degC` | `float32`   | °C              | outdoor temperature                                 |                 |    -28 |     40 |       |
| column             | `wind__m_s_1` | `float32`   | m/s             | wind speed                                          |                 |      0 |     35 |       |
| column             | `ghi__W_m_2`  | `Int16`     | W/m<sup>2</sup> | global horizontal irradiance                        |                 |      0 |   1000 |       |
| column             | `T_in__degC`  | `float32`   | °C              | indoor temperature                                  |                 |      0 |     40 |     3 |

## Status
Dataset is: _collected_, _anonimization-in-progress_

## License
This data is made available under the [CC BY 4.0](./LICENSE.md) by the [Research group Energy Transition, Windesheim University of Applied Sciences](https://windesheim.nl/energietransitie) 

## Credits

Data collection was a joint effort of:
* <contributor name 1> · [@Github_handle_1](https://github.com/<github_handle_1>) · Twitter [@Twitter_handle_1](https://twitter.com/<twitter_handle_1>)
* <contributor name 2> · [@Github_handle_2](https://github.com/<github_handle_2>) · Twitter [@Twitter_handle_2](https://twitter.com/<twitter_handle_2>)
* <contributor name 3> · [@Github_handle_3](https://github.com/<github_handle_3>) · Twitter [@Twitter_handle_3](https://twitter.com/<twitter_handle_3>)
* etc. 
 
Thanks go to those who are the ultimate source of this dataset:
* all anonymous subjects who volunteered to make their measurement data available

We use and gratefully aknowlegde the efforts of the makers of the following source code and libraries:
* [HourlyHistoricWeather](https://github.com/stephanpcpeters/HourlyHistoricWeather), by [@stephanpcpeters](https://github.com/stephanpcpeters), licensed under [an MIT-style licence](https://raw.githubusercontent.com/stephanpcpeters/HourlyHistoricWeather/master/historicdutchweather/LICENSE)
