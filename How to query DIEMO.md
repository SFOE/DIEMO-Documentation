# How to query DIEMO

## Available services

All services of [api3.geo.admin.ch](http://mf-chsdi3.int.bgdi.ch/diemo/services/sdiservices.html) are available. Of special interest are:
* [Identify](http://mf-chsdi3.int.bgdi.ch/diemo/services/sdiservices.html#identify-features): This service can be used to discover features at a specific location. Additionally, attributes can be searched.
* [Find](http://mf-chsdi3.int.bgdi.ch/diemo/services/sdiservices.html#find): This service is used to search the attributes of features. The specific location of features is not taken into account.

## General remarks

* [List of available queryable attributes for the layer ](https://mf-chsdi3.int.bgdi.ch/diemo/rest/services/all/MapServer/ch.bfe.ladestellen-elektromobilitaet?lang=de)
* For the identify service, use the layerDefs-funcionality to query specific attributes. layerDefs is adapted from [ESRI](https://developers.arcgis.com/rest/services-reference/identify-map-service-.htm)
* [chsdi3-code](https://github.com/geoadmin/mf-chsdi3/pull/3185)
* There is no **OR** funcionality
* String search is not case sensistive

## Identify example

[Stations within a distance of 3'500 m from coordinate 2'600'000 / 1'200'000](https://mf-chsdi3.int.bgdi.ch/diemo/rest/services/all/MapServer/identify?geometry=2600000,1200000&mapExtent=0,0,100,100&imageDisplay=100,100,100&geometryFormat=geojson&geometryType=esriGeometryPoint&lang=fr&layers=all:ch.bfe.ladestellen-elektromobilitaet&returnGeometry=true&tolerance=3500&sr=2056)

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
tolerance=3500&
sr=2056
```

Additionally, [IsOpen24Hours = true](https://mf-chsdi3.int.bgdi.ch/diemo/rest/services/all/MapServer/identify?geometry=2600000,1200000&mapExtent=0,0,100,100&imageDisplay=100,100,100&geometryFormat=geojson&geometryType=esriGeometryPoint&lang=fr&layers=all:ch.bfe.ladestellen-elektromobilitaet&returnGeometry=true&tolerance=3500&sr=2056&layerDefs={%22ch.bfe.ladestellen-elektromobilitaet%22:%22IsOpen24Hours%20=%20true%22})

```
&layerDefs={"ch.bfe.ladestellen-elektromobilitaet": "IsOpen24Hours = true"}
```
Additionally, [Authentication with NFC](https://mf-chsdi3.int.bgdi.ch/diemo/rest/services/all/MapServer/identify?geometry=2600000,1200000&mapExtent=0,0,100,100&imageDisplay=100,100,100&geometryFormat=geojson&geometryType=esriGeometryPoint&lang=fr&layers=all:ch.bfe.ladestellen-elektromobilitaet&returnGeometry=true&tolerance=3500&sr=2056&layerDefs={%22ch.bfe.ladestellen-elektromobilitaet%22:%20%22IsOpen24Hours%20=%20true%22,%20%22ch.bfe.ladestellen-elektromobilitaet%22:%22QueryAuthenticationModes%20ilike%20%27%nfc%%27%22})

```
&layerDefs={
"ch.bfe.ladestellen-elektromobilitaet": "IsOpen24Hours = true", 
"ch.bfe.ladestellen-elektromobilitaet": "QueryAuthenticationModes ilike '%nfc%'"}
```

Additionally, [Longitude > 7.476](https://mf-chsdi3.int.bgdi.ch/diemo/rest/services/all/MapServer/identify?geometry=2600000,1200000&mapExtent=0,0,100,100&imageDisplay=100,100,100&geometryFormat=geojson&geometryType=esriGeometryPoint&lang=fr&layers=all:ch.bfe.ladestellen-elektromobilitaet&returnGeometry=true&tolerance=3500&sr=2056&layerDefs={%22ch.bfe.ladestellen-elektromobilitaet%22:%20%22IsOpen24Hours%20=%20true%22,%20%22ch.bfe.ladestellen-elektromobilitaet%22:%22QueryAuthenticationModes%20ilike%20%27%nfc%%27%22,%20%22ch.bfe.ladestellen-elektromobilitaet%22:%22Longitude%20%3E%207.476%22})

```
&layerDefs={
"ch.bfe.ladestellen-elektromobilitaet": "IsOpen24Hours = true", 
"ch.bfe.ladestellen-elektromobilitaet": "QueryAuthenticationModes ilike '%nfc%'", 
"ch.bfe.ladestellen-elektromobilitaet": "Longitude > 7.476"}
```
## Find example

[Search for “ich” in the field “City” (infix match)](https://mf-chsdi3.int.bgdi.ch/diemo/rest/services/all/MapServer/find?layer=ch.bfe.ladestellen-elektromobilitaet&searchText=ich&searchField=City&returnGeometry=false)

```
https://mf-chsdi3.int.bgdi.ch/diemo/rest/services/all/MapServer/find?
layer=ch.bfe.ladestellen-elektromobilitaet&
searchText=ich&
searchField=City&
returnGeometry=false
```


## Open Questions
* How to query "ilike not"?

