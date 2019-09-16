# How to query DIEMO

## Available services

All services of [api3.geo.admin.ch](http://api3.geo.admin.ch/services/sdiservices.html) are available. To query the National Data Infrastructure For Electromobility, two services are of special interest:
* [Identify](http://api3.geo.admin.ch/services/sdiservices.html#identify-features): This service can be used to discover features at a specific location. Additionally, attributes can be searched. Use the layerDefs-funcionality to query specific attributes.
* [Find](http://api3.geo.admin.ch/services/sdiservices.html#find): This service is used to search the attributes of features. The specific location of features is not taken into account. Use the layerDefs-funcionality to query specific attributes.

## General remarks for layerDefs functionality

* [List of available queryable attributes](https://mf-chsdi3.int.bgdi.ch/diemo/rest/services/all/MapServer/ch.bfe.ladestellen-elektromobilitaet?lang=de)
* There is no **OR** funcionality
* String search is not case sensistive
* layerDefs is adapted from [ESRI](https://developers.arcgis.com/rest/services-reference/identify-map-service-.htm)


| Data type    | Operators | Examples |
| --------------- | --------- |--------- |
| varchar | =, +=, like, ilike, not like, not ilike, is null, is not null | toto ='3455 Kloten', toto ilike '%SH%', toto is null, toto ilike 'SH%' |
| number |  =, <, >, >=, <=, != | tutu >= 2.4, tutu < 5 |
| boolean | is (true\|false), is not (true\|false) | tata is not false |


## Identify example (discover features at a specific location)

### Example 1

[Stations within a distance of 300 m from coordinate 2'600'000 / 1'200'000](https://mf-chsdi3.int.bgdi.ch/diemo/rest/services/all/MapServer/identify?geometry=2600000,1200000&mapExtent=0,0,100,100&imageDisplay=100,100,100&geometryFormat=geojson&geometryType=esriGeometryPoint&lang=fr&layers=all:ch.bfe.ladestellen-elektromobilitaet&returnGeometry=true&tolerance=300&sr=2056)

```
https://mf-chsdi3.int.bgdi.ch/diemo/rest/services/all/MapServer/identify?
geometry=2600000,1200000&
mapExtent=0,0,100,100&
imageDisplay=100,100,100&
geometryFormat=geojson&
geometryType=esriGeometryPoint&
lang=de&
layers=all:ch.bfe.ladestellen-elektromobilitaet&
returnGeometry=true&
tolerance=300&
sr=2056
```

Additionally, [IsOpen24Hours is true](https://mf-chsdi3.int.bgdi.ch/diemo/rest/services/all/MapServer/identify?geometry=2600000,1200000&mapExtent=0,0,100,100&imageDisplay=100,100,100&geometryFormat=geojson&geometryType=esriGeometryPoint&lang=fr&layers=all:ch.bfe.ladestellen-elektromobilitaet&returnGeometry=true&tolerance=300&sr=2056&layerDefs={%22ch.bfe.ladestellen-elektromobilitaet%22:%22IsOpen24Hours%20is%20true%22})

```
&layerDefs={"ch.bfe.ladestellen-elektromobilitaet": "IsOpen24Hours is true"}
```
Additionally, [Authentication with NFC](https://mf-chsdi3.int.bgdi.ch/diemo/rest/services/all/MapServer/identify?geometry=2600000,1200000&mapExtent=0,0,100,100&imageDisplay=100,100,100&geometryFormat=geojson&geometryType=esriGeometryPoint&lang=fr&layers=all:ch.bfe.ladestellen-elektromobilitaet&returnGeometry=true&tolerance=300&sr=2056&layerDefs={%22ch.bfe.ladestellen-elektromobilitaet%22:%20%22IsOpen24Hours%20is%20true%22,%20%22ch.bfe.ladestellen-elektromobilitaet%22:%22QueryAuthenticationModes%20ilike%20%27%nfc%%27%22})

```
&layerDefs={
"ch.bfe.ladestellen-elektromobilitaet": "IsOpen24Hours is true", 
"ch.bfe.ladestellen-elektromobilitaet": "QueryAuthenticationModes ilike '%nfc%'"}
```

Additionally, [Longitude > 7.43842](https://mf-chsdi3.int.bgdi.ch/diemo/rest/services/all/MapServer/identify?geometry=2600000,1200000&mapExtent=0,0,100,100&imageDisplay=100,100,100&geometryFormat=geojson&geometryType=esriGeometryPoint&lang=fr&layers=all:ch.bfe.ladestellen-elektromobilitaet&returnGeometry=true&tolerance=300&sr=2056&layerDefs={%22ch.bfe.ladestellen-elektromobilitaet%22:%20%22IsOpen24Hours%20is%20true%22,%20%22ch.bfe.ladestellen-elektromobilitaet%22:%22QueryAuthenticationModes%20ilike%20%27%nfc%%27%22,%20%22ch.bfe.ladestellen-elektromobilitaet%22:%22Longitude%20%3E%207.43842%22})

```
&layerDefs={
"ch.bfe.ladestellen-elektromobilitaet": "IsOpen24Hours is true", 
"ch.bfe.ladestellen-elektromobilitaet": "QueryAuthenticationModes ilike '%nfc%'", 
"ch.bfe.ladestellen-elektromobilitaet": "Longitude > 7.43842"}
```
## Find example (search the attributes of features)

### Example 1

[Search for “ich” in the field “City” (infix match)](https://mf-chsdi3.int.bgdi.ch/diemo/rest/services/all/MapServer/find?layer=ch.bfe.ladestellen-elektromobilitaet&searchText=ich&searchField=City&returnGeometry=false)

```
https://mf-chsdi3.int.bgdi.ch/diemo/rest/services/all/MapServer/find?
layer=ch.bfe.ladestellen-elektromobilitaet&
searchText=ich&
searchField=City&
returnGeometry=false
```

Additionally, [IsOpen24Hours is true](https://mf-chsdi3.int.bgdi.ch/diemo/rest/services/all/MapServer/find?layer=ch.bfe.ladestellen-elektromobilitaet&searchText=ich&searchField=City&returnGeometry=false&layerDefs={%22ch.bfe.ladestellen-elektromobilitaet%22:%20%22IsOpen24Hours%20is%20true%22})

```
&layerDefs={"ch.bfe.ladestellen-elektromobilitaet": "IsOpen24Hours is true"}
```
