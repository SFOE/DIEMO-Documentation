# DIEMO-Documentation

* [Doc](http://mf-chsdi3.int.bgdi.ch/diemo/services/sdiservices.html#identify-features)
* [ESRI doc](https://developers.arcgis.com/rest/services-reference/identify-map-service-.htm)
* [Code](https://github.com/geoadmin/mf-chsdi3/pull/3185)

Examples 1:

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
