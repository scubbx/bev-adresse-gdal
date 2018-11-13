# BEV Adressdaten mit GDAL

## Beschreibung

Dies ist ein Versuch, mittels GDAL VRT Definitionen die in drei verschiedenen Koordinatensystemen vorliegenden Relationalen Stichtagsdaten der Adressen, abgegeben durch das BEV (Bundesamt für Eich- und Vermessungswesen), in ein einheitliches Koordinatensystem zu transformieren.

Quelldaten des BEV: http://www.bev.gv.at/pls/portal/docs/PAGE/BEV_PORTAL_CONTENT_ALLGEMEIN/0200_PRODUKTE/UNENTGELTLICHE_PRODUKTE_DES_BEV/Adresse_Relationale_Tabellen-Stichtagsdaten.zip

Das Ziel war, möglichst ohne Skript oder ausführbaren Dateien die Original BEV Daten weiterverarbeiten zu können.

## Verwendung

### On-The-Fly

Die beiden Dateien ''ADRESSE.vrt'' und ''GEBAEUDE.vrt'' müssen in das gleiche Verzeichnis wie die beiden zugehörigen CSV Dateien des BEV kopiert werden. Die VRT Dateien lassen sich von den meisten GIS Programmen, welche den GDAL Treiber benutzen öffnen.

### Konvertierung

Mit dem in GDAL inkudierten Programm ''ogr2ogr'' lässt sich der Datensatz konvertieren.
Dazu sind folgende beiden Befehle abzusetzen:

''ogr2ogr -f CSV -lco GEOMETRY=AS_XY -t_srs EPSG:4326 ADRESSE_4326.csv ADRESSE.vrt''

''ogr2ogr -f CSV -lco GEOMETRY=AS_XY -t_srs EPSG:4326 GEBAEUDE_4326.csv GEBAEUDE.vrt''
