---
layout: page
title: "Västtrafik"
description: "How to integrate Västtrafik in Home Assistant"
date: 2016-10-05 18:04
sidebar: true
comments: false
sharing: true
footer: true
logo: vasttrafik.png
ha_category: Transport
ha_iot_class: "Cloud Polling"
ha_release: 0.29
---


The `västtrafik` sensor will give you departure information from a given location for the public transportation system in Västra Götaland, Sweden. 

You must create an application [here](https://developer.vasttrafik.se) to obtain a key and a secret.  

To enable this sensor, add the following lines to your `configuration.yaml` file:

```yaml
# Example configuration.yaml entry
sensor:
  - platform: vasttrafik
    key: XYZ
    secret: XYZ
    departures:
      - name: To work
        from: Vågmästareplatsen
        heading: Gropegårdsgatan
```

Configuration variables:

- **key** (*Required*): A key obtained from [developer.vasttrafik.se](https://developer.vasttrafik.se) after creating an application.
- **secret** (*Required*): A secret obtained from [developer.vasttrafik.se](https://developer.vasttrafik.se) after creating an application.
- **departures** array (*Optional*): The array contains a list of departures to monitor.
  - **name** (*Required*): Name of the sensor.
  - **from** (*Required*): Name of departure stop.
  - **heading** (*Optional*): Name of heading stop to filter on departures in a specified direction.
  - **delay** (*Optional*): Number of minutes to add to current time when querying upcomming departures.

A full configuration entry could look like the sample below: 

```yaml
# Example configuration.yaml entry
sensor:
  - platform: vasttrafik
    key: XYZ
    secret: XYZ
    departures:
      - name: To work
        from: Vågmästareplatsen
        heading: Gropegårdsgatan
        delay: 10
      - name: To City
        from: Vågmästareplatsen
        heading: Brunnsparken
        delay: 10
```
