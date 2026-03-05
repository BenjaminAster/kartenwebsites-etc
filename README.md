
# Kartenwebsites etc.

Eine Liste mit Websites & Apps/Programmen in Bezug auf Karten, öffentlichen Verkehr, Bahninfrastruktur, GIS, etc. Vieles hier ist Österreich- bzw. Graz-spezifisch

- [Karten & OpenStreetMap](#karten--openstreetmap)
- [Öffentlicher Personenverkehr](#öffentlicher-personenverkehr)
- [GIS & regionspezifische Sachen](#gis--regionspezifische-sachen)
- [Foren etc.](#foren-etc)
- [Apps](#apps)

## Karten & OpenStreetMap
- [OpenStreetMap](https://www.openstreetmap.org/): freies Projekt zur Sammlung von Geodaten. Man beachte die verschiedenen zur Auswahl stehenden Map Layers
- [OpenRailwayMap.app](https://openrailwaymap.app/)/[OpenRailwayMap.org](https://openrailwaymap.org/) (.app hat mehr Features, .org ist oft schneller): Karte aller Bahngleise mit etlichen Darstellungstypen (inkl. Zeitreise) und Einstellungen. Bei .app kan kann die Hintergrundkarte spezifizieren (es empfiehlt sich, die Sättigung und Opacity zu erhöhen), z.B.:
	- Basemap Orthofoto (nur Österreich):
		```
		https://mapsneu.wien.gv.at/basemap/bmaporthofoto30cm/normal/google3857/{z}/{y}/{x}.jpeg
		```
	- Google Maps (`lyrs`: Kartentyp (`y` = Satellit mit Labels, `s` = Satellit ohne Labels, `m` = Standard, `p` = Terrain), `hl`: Sprache):
		```
		https://mt1.google.com/vt/?x={x}&y={y}&z={z}&hl=en&lyrs=y
		```
	- ArcGis Satellit (nur bis zur vorletzten Zoomstufe):
		```
		https://server.arcgisonline.com/ArcGIS/rest/services/World_Imagery/MapServer/tile/{z}/{y}/{x}
		```
	- OpenStreetMap:
		```
		https://tile.openstreetmap.org/{z}/{x}/{y}.png
		```
	- etliche weitere siehe [OSM Wiki](https://wiki.openstreetmap.org/wiki/Raster_tile_providers)
- [Flightradar24](https://www.flightradar24.com/): Flugzeuge live tracken
- [MarineTraffic](https://www.marinetraffic.com/), [VesselFinder](https://www.vesselfinder.com/): Schiffe live tracken
- [OpenStreetBrowser](https://www.openstreetbrowser.org/): Visualisieren von verschiedenen OSM-Daten, z.B.:
	- [Höchstgeschwindigkeiten auf Straßen](https://www.openstreetbrowser.org/#categories=car_maxspeed)
- [OpenLevelUp](https://openlevelup.net/): Gebäude-Innenpläne anschauen, sofern in OSM eingetragen
- [WaterwayMap](https://waterwaymap.org/): Karte aller Flüsse, farblich sortiert nach wo sie im Meer münden
- [Arcanum Maps](https://maps.arcanum.com/): verschiedene hunderte Jahre alte Karten
- [OpenHistorialMap](https://www.openhistoricalmap.org/): wie OpenStreetMap, aber für historische Daten
- [OpenTopoMap](https://opentopomap.org/): topografische Karte mit OSM-Daten
- [World topographic map](https://en-gb.topographic-map.com/world/): Karte mit Höhenmetern farblich gekennzeichnet
- [Overpass Turbo](https://overpass-turbo.eu/): Website, um ganz spezifische OpenStreetMap-Datenabfragen zu [programmieren](https://wiki.openstreetmap.org/wiki/Overpass_API/Overpass_QL). Ein KI-Chatbot kann dabei hilfreich (allerdings auch unzuverlässig) sein. z.B.:
	- [öffentliche Toiletten in 100m Radius von Straßenbahnhaltestellen in Graz](https://overpass-turbo.eu/?Q=%0A%2F%2F%20speichere%20die%20Region%20Graz%20in%20der%20Variable%20%22graz%22%0A%7B%7BgeocodeArea%3AGraz%7D%7D-%3E.graz%3B%0A%0A%2F%2F%20suche%20alle%20Stra%C3%9Fenbahnhaltestellen%20in%20Graz%20und%20speichere%20sie%20in%20der%20Variable%20%22tramStops%22%0Anwr(area.graz)%5B%22railway%22%3D%22tram_stop%22%5D-%3E.tramStops%3B%0A%0A%2F%2F%20suche%20alle%20Toiletten%2C%20die%20h%C3%B6chstens%20100%20Meter%20von%20einer%20Stra%C3%9Fenbahnhaltestelle%20entfernt%20sind%0Anwr(around.tramStops%3A100)%5B%22amenity%22%3D%22toilets%22%5D%3B%0A%0A%2F%2F%20outputte%20die%20Geometrie%20der%20gefundenen%20Toiletten%0Aout%20geom%3B%0A&C=47.07%3B15.44%3B14)
	- [Liste aller Buslinien, die über die ~Augartenbrücke~ _Alfred-Stingl-Brücke_ in Graz fahren](https://overpass-turbo.eu/?Q=%0A%2F%2F%20speichere%20die%20Region%20Graz%20in%20der%20Variable%20%22graz%22%0A%7B%7BgeocodeArea%3AGraz%7D%7D-%3E.graz%3B%0A%0A%2F%2F%20suche%20nach%20der%20Alfred-Stingl-Br%C3%BCcke%20in%20Graz%20und%20speichere%20sie%20in%20der%20Variable%20%22bridge%22%0Away(area.graz)%5B%22bridge%22%3D%22yes%22%5D%5B%22name%22%3D%22Alfred-Stingl-Br%C3%BCcke%22%5D-%3E.bridge%3B%0A%0A%2F%2F%20suche%20alle%20Busrouten%2C%20von%20denen%20die%20Alfred-Stingl-Br%C3%BCcke%20ein%20Teil%20ist%20(das%20%22bw%22%20steht%20f%C3%BCr%20%22backward%20from%20ways%22%2C%20weil%20man%20von%20einem%20Way%20(der%20Br%C3%BCcke)%20alle%20Busrouten-Relationen%20sucht%2C%20die%20den%20Way%20enthalten)%0Arel(bw.bridge)%5B%22route%22%3D%22bus%22%5D%3B%0A%0A%2F%2F%20outputte%20nur%20die%20Metadaten%20der%20Busrouten%20ohne%20jegliche%20Geometrie%0Aout%20tags%3B%0A)
- [Submarine Cable Map](https://www.submarinecablemap.com/): Karte mit allen Internet-Kabeln

## Öffentlicher Personenverkehr
- [TRAVIC](https://travic.app/): ÖV (Busse, Straßenbahnen, Züge) "tracken" (nicht live, sondern geplante Fahrten laut Fahrplan)
- [AnachB](https://anachb.vor.at/): Österreichischer ÖV-Routenplaner. Bei der Karte kann man Live-ÖV anzeigen, ähnlich wie bei TRAVIC (Position der Busse/Straßenbahnen/Züge nicht nach echter GPS-Position, aber anhand der aktuellen Verspätung reverse-engineered)
- [ÖBB Zug Livemap](https://fahrplan.oebb.at/webapp/?showLivemap=true): Züge live tracken (ähnlich wie AnachB aber speziell für Züge)
- [Zugfinder](https://www.zugfinder.net/en/livemap-europa-2000-1800): Noch eine Züge-live-tracken-Website, aber mit schematischem Netzplan
- [ÖPNVKarte](https://xn--pnvkarte-m4a.de/#14;48;7): Karte mit allen ÖV-Linien, ähnlich wie der [OSM Transport Layer](https://www.openstreetmap.org/#layers=T)
- [Gleisplanweb](https://gleisplanweb.eu/plaene.php): Gleispläne etlicher Straßenbahn/U-Bahn-Netze
- Netzpläne:
	- Europa: [Schienennetz](https://www.interrail.eu/content/dam/_new-structure/visual/maps/interrail_map_2026.pdf)
	- Österreich: [Schienennetzkarten](https://infrastruktur.oebb.at/de/geschaeftspartner/schienennetz/dokumente-und-daten/netzkarten), [Streckennetz](https://www.oebb.at/de/dam/jcr:7fc18e86-1c23-4cf0-b9e0-94eb05d32c3e/bahnnetz-oebb.pdf)
	- Burgenland: [Netzplan](https://www.b-mobil.info/fileadmin/user_upload/Downloads/Gesamtnetz_Burgenland.pdf)
	- Kärnten: [S-Bahn Netzplan](https://www.oebb.at/de/regionale-angebote/kaernten/s-bahn-kaernten), [Klagenfurt Netzpläne](https://www.klagenfurtmobil.at/fahrplaene/fahrplaene-linien-standplaetze/)
	- Niederösterreich: [St. Pölten Fahrplanheft mit Liniennetzplan](https://www.st-poelten.at/gv-buergerservice/verkehr-mobilitaet-und-reisen/lup)
	- Oberösterreich: [Linz Netzplan](https://www.linzag.at/media/dokumente/linien_1/infomaterial_1/linien-linienfahrplan.pdf), [S-Bahn Netzplan](https://www.land-oberoesterreich.gv.at/Mediendateien/LK/S-Bahn_OOe-Netzplan.pdf)
	- Ost-Region (Wien+Niederösterreich+Burgenland): Netzpläne [vom VOR](https://www.vor.at/befoerderung/downloads)/[von der ÖBB](https://www.oebb.at/de/regionale-angebote/wien)
	- Salzburg: [Netzpläne](https://salzburg-verkehr.at/service/download/liniennetz-und-umgebungsplaene/)
	- Steiermark: [Netzpläne und Haltestellenübersichten](https://www.verbundlinie.at/de/verbindungen/fahrplandownloads/netzplaene-haltestellenuebersichten?tag_id=all), [RegioBus-Netz](https://www.verbundlinie.at/images/service/pdfs/regiobus_hauptnetz.pdf)
	- Tirol: [Netzpläne](https://www.vvt.at/allgemeines/downloads)
	- Vorarlberg: [Netzpläne](https://www.vmobil.at/de/bus-bahn/das-vvv-liniennetz), [S-Bahn Netzplan](https://www.oebb.at/de/regionale-angebote/vorarlberg/s-bahn-vorarlberg), [Bregenz Netzplan](https://www.stadtwerke-bregenz.at/stadtbus/fahrplaene-liniennetz)
	- Wien: [Netzpläne](https://www.wienerlinien.at/fahrplaene#portlet_com_liferay_asset_publisher_web_portlet_AssetPublisherPortlet_INSTANCE_I93YWfWsDdVt)
- [ÖBB Streckeninformation](https://fahrplan.oebb.at/bin/help.exe/dn?tpl=showmap_external): Karte mit aktuellen Baustellen und Störungen der ÖBB
- [ÖBB Info-To-Go](https://infotogo.oebb.at/~8103172~): Live Abfahrts- & Ankunftsmonitore aller Bahnhöfe

## GIS & regionspezifische Sachen:
- [Geoland](https://geoland.at/): Übersicht mit Links zu GIS-Websites der österreichischen Bundesländer
- [Geoland Österreich-Karte](https://www.geoland.at/webgisviewer/geoland/map/Geoland_Viewer/Geoland): Basic Web-GIS für ganz Österreich
- [Karte des österreichischen Bundesamts für Eich- und Vermessungswesen](https://maps.bev.gv.at/). Enthält auch einige historische Karten
- [Steiermark-GIS](https://gis.stmk.gv.at/wgportal/atlasmobile/map/Basiskarten/Basiskarte). Unter "Abfragen" > "Koordinaten / Höhe" kann man Höhenmeter von Grund ("Gelände-DGM") und Höhe eines Gebäudes/Baums ("Objekthöhe") erfahren. Bei "Dienste suchen/hinzufügen" gibt es etliche Karten, z.B.:
	- [Geologie](https://gis.stmk.gv.at/wgportal/atlasmobile/map/Basiskarten/Basiskarte?append-services=geologie&presentation=dvg_geologische_karte/dv_geologie_geologie_1_50_000): Untergrundkarte
	- [Stadtbezirke Graz](https://gis.stmk.gv.at/wgportal/atlasmobile/map/Basiskarten/Basiskarte?append-services=grenzen&presentation=dvg_grenzen_mit_gemeindebezug/bezgraz) (hier empfiehlt es sich, die Deckkraft der Hintergrundkarte zu verringern)
	- [Franziszeischer Kataster](https://gis.stmk.gv.at/wgportal/atlasmobile/map/Basiskarten/Basiskarte?append-services=franziskataster&presentation=dvg_franziszeischer_kataster_(1820_–_1825)/dv_ogd_rdata-franziszeischerkataster): Karte aus 1820
	- [Hochspannungsleitungen](https://gis.stmk.gv.at/wgportal/atlasmobile/map/Basiskarten/Basiskarte?append-services=energie__infrastruktur&presentation=dvg_hochspannungsleitung), [Gaspipelines](https://gis.stmk.gv.at/wgportal/atlasmobile/map/Basiskarten/Basiskarte?append-services=energie__infrastruktur&presentation=dvg_gaspipeline), [Rohölpipelines](https://gis.stmk.gv.at/wgportal/atlasmobile/map/Basiskarten/Basiskarte?append-services=energie__infrastruktur&presentation=dvg_rohölpipeline)
	- [Baumverteilung](https://gis.stmk.gv.at/wgportal/atlasmobile/map/Basiskarten/Basiskarte?append-services=waldatlas&presentation=dvg_forstliche_parameter/Baumartenverteilung): Wälder, farblich gekennzeichnet nach Laubwald/Mischwald/Nadelwald
	- [Digitales Geländemodell (DGM)](https://gis.stmk.gv.at/wgportal/atlasmobile/map/Basiskarten/Basiskarte?append-services=als&presentation=dvg_geländeschummerung_50cm_-_gebäude_und_boden), [Digitales Oberflächenmodell (DOM)](https://gis.stmk.gv.at/wgportal/atlasmobile/map/Basiskarten/Basiskarte?append-services=als&presentation=dvg_oberflächenschummerung_2017-2021)
	- [Normiertes DOM (Objekthöhe)](https://gis.stmk.gv.at/wgportal/atlasmobile/map/Basiskarten/Basiskarte?append-services=objekthoehen_verlauf__normiertes_dom&presentation=dvg_objekthöhe_aktuell/dv_ogd_hoehen-als_hoehen_aktuell_dom_utm33n_32633): Höhe von Gebäuden und Bäumen
	- [Hangrichtung Farbe](https://gis.stmk.gv.at/wgportal/atlasmobile/map/Basiskarten/Basiskarte?append-services=hangrichtung_farbe_exposition&presentation=dvg_geländeinformation_aktuell/dv_ogd_hoehen-als_hoehen_aktuell_dgm_utm33n_32633): Berghänge nach richtung farblich gekennzeichnet
	- [Durchschnittliche Jahrestemperatur](https://gis.stmk.gv.at/wgportal/atlasmobile/map/Basiskarten/Basiskarte?append-services=kla_temp&presentation=ds_jahrestemp)
	- [Straßenlärm](https://gis.stmk.gv.at/wgportal/atlasmobile/map/Basiskarten/Basiskarte?append-services=laerm&presentation=dvg_2022_eu_umgebungslärm_-_rl/dv_2022_eu_umebungslaermrl_strasse_lden__dayeveningnight__strasse_laermzonen__lden___eu_ul-rl_2022_)
	- [Flächenwidmungsplan](https://gis.stmk.gv.at/wgportal/atlasmobile/map/Basiskarten/Basiskarte?append-services=oertlraumpl&presentation=dvg_stammplan/widm,dvg_stammplan/kat)
	- [Grundstücke](https://gis.stmk.gv.at/wgportal/atlasmobile/map/Basiskarten/Basiskarte?presentation=voll)
	- [Kanalkataster](https://gis.stmk.gv.at/wgportal/atlasmobile/map/Basiskarten/Basiskarte?append-services=kanal_trinkw_gdi&presentation=dvg_kanalkataster): Abwasser/Regenwasser-Kanäle und Kanaldeckel. Folgt man den Kanälen in Fließrichtung, landet man in einer Kläranlage oder einem Fluss
- [Graz Stadtplan](https://geodaten.graz.at/Stadtkarte/synserver?project=GRAZ_Stadtplan)
- [Graz-GIS Karten-Übersicht](https://geodaten.graz.at/WebOffice/). z.B.:
	- [Flächenwidmungsplan](https://geodaten.graz.at/WebOffice/synserver?project=STEK-FWP-RLB&client=flex) ([Legende](https://geodaten.graz.at/WebOffice/pub/Graz/legenden/FWP-STEK-RLB/Legende_FWPL4_aktuell1.jpg))
	- [Stadtentwicklungskonzept](https://geodaten.graz.at/WebOffice/synserver?project=STEK-FWP-RLB&client=flex&view=4_0_STEK) ([Legende](https://geodaten.graz.at/WebOffice/pub/Graz/legenden/FWP-STEK-RLB/Stek_4_Legweb_aktuell.jpg))
	- [Räumliches Leitbild](https://geodaten.graz.at/WebOffice/synserver?project=STEK-FWP-RLB&client=flex&view=1_0_RLB) ([Legende](https://geodaten.graz.at/WebOffice/pub/Graz/legenden/FWP-STEK-RLB/RLB.jpg))
	- [Baumkataster](https://geodaten.graz.at/WebOffice/synserver?project=baumkataster&client=flex): Karte mit allen Holding-Graz-gemanageten Bäumen inkl. Information wie Stammumfang, Baumart, etc.
	- [Verkehrslärmkataster](https://geodaten.graz.at/WebOffice/synserver?project=verkehrslaerm&client=flex) ([Legende](https://geodaten.graz.at/WebOffice/pub/Graz/legenden/VLK_2011_Tag.jpg))
	- [Personenbezogene Straßen](https://geodaten.graz.at/WebOffice/synserver?project=PersonenbezogeneStrassen&client=flex): Karte mit Straßen, die nach Personen benannt wurden, inkl. jeweiliger Biografie als PDF
	- [Baustelleninformation](https://geodaten.graz.at/WebOffice/synserver?project=baustelleninformation&client=flex): Karte mit allen Baustellen & jeweiliger Information
	- [Fließpfadkarte](https://geodaten.graz.at/WebOffice/synserver?project=FL_PFAD&client=flex): Wie das Wasser bei Starkregen abfließt
- [Einsatzübersichtskarte der Feuerwehren Steiermark](https://einsatzuebersicht.lfv.steiermark.at/lfvasp/einsatzkarte/karte_app_public.html)
- [Steiermark Erlebnisregionen](https://www.steiermark.com/de/Regionen) Maps: offizielle Karten des Landes Steiermark mit Wanderwegen, Sehenswürdigkeiten, etc.: [Ausseerland](https://maps.ausseerland.at/), [Schladming-Dachstein](https://maps.schladming-dachstein.at/), [Gesäuse](https://maps.gesaeuse.at/), [Thermen- & Vulkanland](https://maps.thermen-vulkanland.at/), [Oststeiermark](https://maps.oststeiermark.com/), [Hochsteiermark](https://maps.hochsteiermark.at/), [Graz](https://maps.regiongraz.at/), [Südsteiermark](https://maps.suedsteiermark.com/), [Erzberg-Leoben](https://maps.erzberg-leoben.at/), [Murau](https://maps.regionmurau.at/), [Murtal](https://maps.murtal.at/)

## Foren etc.
- [Project Mapping](https://projectmapping.co.uk/rail_maps_diagrams.html): Sammlung von tausenden (zum Teil von der Community erstellten) Netzplänen
- [public-transport.at](https://www.public-transport.at/): Website eines Grazer Nerds mit random Infos zum ÖV in Österreich (teilweise veraltet)
- [Straßenbahnjournal](https://www.strassenbahnjournal.at/) inkl. [Wiki](https://www.strassenbahnjournal.at/wiki/index.php?title=Hauptseite): Website mit random Infos, Fotos etc. im Bezug auf Straßenbahnen
- [Styria-Mobile](https://www.styria-mobile.at/) inkl. [Forum](https://www.styria-mobile.at/home/smf/index.php): Straßenbahnen & Züge in der Steiermark
- [Tramwayforum.at](https://www.tramwayforum.at/): österreichisches Straßenbahn-Forum

## Apps
- [Organic Maps](https://organicmaps.app/): OSM-basierte Navigationsapp für Android+iOS

## Sonstiges
- [OSM Apps Catalog](https://osm-apps.org/), [List of OSM-based services](https://wiki.openstreetmap.org/wiki/List_of_OSM-based_services), [Awesome OpenStreetMap](https://github.com/osmlab/awesome-openstreetmap): Listen etlicher Websites/Apps mit Bezug zu OpenStreetMap
