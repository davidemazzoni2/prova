<!doctype html>
<html lang="en">
    <head>
        <meta charset="utf-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="initial-scale=1,user-scalable=no,maximum-scale=1,width=device-width">
        <meta name="mobile-web-app-capable" content="yes">
        <meta name="apple-mobile-web-app-capable" content="yes">
        <link rel="stylesheet" href="css/leaflet.css">
        <link rel="stylesheet" href="css/qgis2web.css"><link rel="stylesheet" href="css/fontawesome-all.min.css">
        <link rel="stylesheet" href="css/leaflet-control-geocoder.Geocoder.css">
        <link rel="stylesheet" href="css/leaflet-measure.css">
        <style>
        html, body, #map {
            width: 100%;
            height: 100%;
            padding: 0;
            margin: 0;
        }
        </style>
        <title></title>
    </head>
    <body>
        <div id="map">
        </div>
        <script src="js/qgis2web_expressions.js"></script>
        <script src="js/leaflet.js"></script>
        <script src="js/leaflet.rotatedMarker.js"></script>
        <script src="js/leaflet.pattern.js"></script>
        <script src="js/leaflet-hash.js"></script>
        <script src="js/Autolinker.min.js"></script>
        <script src="js/rbush.min.js"></script>
        <script src="js/labelgun.min.js"></script>
        <script src="js/labels.js"></script>
        <script src="js/leaflet-control-geocoder.Geocoder.js"></script>
        <script src="js/leaflet-measure.js"></script>
        <script src="data/132kV_7.js"></script>
        <script src="data/66kV_8.js"></script>
        <script src="data/MT_lines_9.js"></script>
        <script src="data/NIGELECisolatedcenters_10.js"></script>
        <script src="data/grid_Niger_11.js"></script>
        <script src="data/gadm36_BFA_3_12.js"></script>
        <script src="data/gadm36_BFA_2_13.js"></script>
        <script src="data/gadm36_BFA_1_14.js"></script>
        <script src="data/gadm36_BFA_0_15.js"></script>
        <script>
        var highlightLayer;
        function highlightFeature(e) {
            highlightLayer = e.target;

            if (e.target.feature.geometry.type === 'LineString') {
              highlightLayer.setStyle({
                color: '#ffff00',
              });
            } else {
              highlightLayer.setStyle({
                fillColor: '#ffff00',
                fillOpacity: 1
              });
            }
            highlightLayer.openPopup();
        }
        var map = L.map('map', {
            zoomControl:true, maxZoom:28, minZoom:1
        }).fitBounds([[4.858161508471047,-9.076626691042275],[21.98037291028691,8.210663999050459]]);
        var hash = new L.Hash(map);
        map.attributionControl.setPrefix('<a href="https://github.com/tomchadwin/qgis2web" target="_blank">qgis2web</a> &middot; <a href="https://leafletjs.com" title="A JS library for interactive maps">Leaflet</a> &middot; <a href="https://qgis.org">QGIS</a>');
        var autolinker = new Autolinker({truncate: {length: 30, location: 'smart'}});
        var measureControl = new L.Control.Measure({
            position: 'topleft',
            primaryLengthUnit: 'meters',
            secondaryLengthUnit: 'kilometers',
            primaryAreaUnit: 'sqmeters',
            secondaryAreaUnit: 'hectares'
        });
        measureControl.addTo(map);
        document.getElementsByClassName('leaflet-control-measure-toggle')[0]
        .innerHTML = '';
        document.getElementsByClassName('leaflet-control-measure-toggle')[0]
        .className += ' fas fa-ruler';
        var bounds_group = new L.featureGroup([]);
        function setBounds() {
        }
        map.createPane('pane_ESRISatellite_0');
        map.getPane('pane_ESRISatellite_0').style.zIndex = 400;
        var layer_ESRISatellite_0 = L.tileLayer('https://server.arcgisonline.com/ArcGIS/rest/services/World_Imagery/MapServer/tile/{z}/{y}/{x}', {
            pane: 'pane_ESRISatellite_0',
            opacity: 1.0,
            attribution: '',
            minZoom: 1,
            maxZoom: 28,
            minNativeZoom: 0,
            maxNativeZoom: 18
        });
        layer_ESRISatellite_0;
        map.addLayer(layer_ESRISatellite_0);
        map.createPane('pane_GoogleHybrid_1');
        map.getPane('pane_GoogleHybrid_1').style.zIndex = 401;
        var layer_GoogleHybrid_1 = L.tileLayer('https://mt1.google.com/vt/lyrs=y&x={x}&y={y}&z={z}', {
            pane: 'pane_GoogleHybrid_1',
            opacity: 1.0,
            attribution: '',
            minZoom: 1,
            maxZoom: 28,
            minNativeZoom: 0,
            maxNativeZoom: 18
        });
        layer_GoogleHybrid_1;
        map.addLayer(layer_GoogleHybrid_1);
        map.createPane('pane_OpenStreetMap_2');
        map.getPane('pane_OpenStreetMap_2').style.zIndex = 402;
        var layer_OpenStreetMap_2 = L.tileLayer('https://tile.openstreetmap.org/{z}/{x}/{y}.png', {
            pane: 'pane_OpenStreetMap_2',
            opacity: 1.0,
            attribution: '',
            minZoom: 1,
            maxZoom: 28,
            minNativeZoom: 0,
            maxNativeZoom: 19
        });
        layer_OpenStreetMap_2;
        map.addLayer(layer_OpenStreetMap_2);
        map.createPane('pane_OSMHumanitarianDataModel_3');
        map.getPane('pane_OSMHumanitarianDataModel_3').style.zIndex = 403;
        var layer_OSMHumanitarianDataModel_3 = L.tileLayer('http://a.tile.openstreetmap.fr/hot/{z}/{x}/{y}.png', {
            pane: 'pane_OSMHumanitarianDataModel_3',
            opacity: 1.0,
            attribution: '',
            minZoom: 1,
            maxZoom: 28,
            minNativeZoom: 0,
            maxNativeZoom: 18
        });
        layer_OSMHumanitarianDataModel_3;
        map.addLayer(layer_OSMHumanitarianDataModel_3);
        map.createPane('pane_Topo_4');
        map.getPane('pane_Topo_4').style.zIndex = 404;
        var layer_Topo_4 = L.tileLayer('https://api.maptiler.com/maps/topo/256/{z}/{x}/{y}@2x.png?key=QEYDjp409Efjhs5IbYq5', {
            pane: 'pane_Topo_4',
            opacity: 1.0,
            attribution: '<a href=""><a href="https://www.maptiler.com/copyright/" target="_blank">&copy; MapTiler</a> <a href="https://www.openstreetmap.org/copyright" target="_blank">&copy; OpenStreetMap contributors</a></a>',
            minZoom: 1,
            maxZoom: 28,
        });
        layer_Topo_4;
        map.addLayer(layer_Topo_4);
        map.createPane('pane_StamenTonerLight_5');
        map.getPane('pane_StamenTonerLight_5').style.zIndex = 405;
        var layer_StamenTonerLight_5 = L.tileLayer('http://tile.stamen.com/toner-lite/{z}/{x}/{y}.png', {
            pane: 'pane_StamenTonerLight_5',
            opacity: 1.0,
            attribution: '',
            minZoom: 1,
            maxZoom: 28,
            minNativeZoom: 0,
            maxNativeZoom: 20
        });
        layer_StamenTonerLight_5;
        map.addLayer(layer_StamenTonerLight_5);
        map.createPane('pane_GoogleMaps_6');
        map.getPane('pane_GoogleMaps_6').style.zIndex = 406;
        var layer_GoogleMaps_6 = L.tileLayer('https://mt1.google.com/vt/lyrs=m&x={x}&y={y}&z={z}', {
            pane: 'pane_GoogleMaps_6',
            opacity: 1.0,
            attribution: '',
            minZoom: 1,
            maxZoom: 28,
            minNativeZoom: 0,
            maxNativeZoom: 19
        });
        layer_GoogleMaps_6;
        map.addLayer(layer_GoogleMaps_6);
        function pop_132kV_7(feature, layer) {
            layer.on({
                mouseout: function(e) {
                    for (i in e.target._eventParents) {
                        e.target._eventParents[i].resetStyle(e.target);
                    }
                    if (typeof layer.closePopup == 'function') {
                        layer.closePopup();
                    } else {
                        layer.eachLayer(function(feature){
                            feature.closePopup()
                        });
                    }
                },
                mouseover: highlightFeature,
            });
        }

        function style_132kV_7_0() {
            return {
                pane: 'pane_132kV_7',
                opacity: 1,
                color: 'rgba(72,123,182,1.0)',
                dashArray: '',
                lineCap: 'square',
                lineJoin: 'bevel',
                weight: 4.0,
                fillOpacity: 0,
                interactive: true,
            }
        }
        map.createPane('pane_132kV_7');
        map.getPane('pane_132kV_7').style.zIndex = 407;
        map.getPane('pane_132kV_7').style['mix-blend-mode'] = 'normal';
        var layer_132kV_7 = new L.geoJson(json_132kV_7, {
            attribution: '',
            interactive: true,
            dataVar: 'json_132kV_7',
            layerName: 'layer_132kV_7',
            pane: 'pane_132kV_7',
            onEachFeature: pop_132kV_7,
            style: style_132kV_7_0,
        });
        bounds_group.addLayer(layer_132kV_7);
        map.addLayer(layer_132kV_7);
        function pop_66kV_8(feature, layer) {
            layer.on({
                mouseout: function(e) {
                    for (i in e.target._eventParents) {
                        e.target._eventParents[i].resetStyle(e.target);
                    }
                    if (typeof layer.closePopup == 'function') {
                        layer.closePopup();
                    } else {
                        layer.eachLayer(function(feature){
                            feature.closePopup()
                        });
                    }
                },
                mouseover: highlightFeature,
            });
        }

        function style_66kV_8_0() {
            return {
                pane: 'pane_66kV_8',
                opacity: 1,
                color: 'rgba(84,176,74,1.0)',
                dashArray: '',
                lineCap: 'square',
                lineJoin: 'bevel',
                weight: 3.0,
                fillOpacity: 0,
                interactive: true,
            }
        }
        map.createPane('pane_66kV_8');
        map.getPane('pane_66kV_8').style.zIndex = 408;
        map.getPane('pane_66kV_8').style['mix-blend-mode'] = 'normal';
        var layer_66kV_8 = new L.geoJson(json_66kV_8, {
            attribution: '',
            interactive: true,
            dataVar: 'json_66kV_8',
            layerName: 'layer_66kV_8',
            pane: 'pane_66kV_8',
            onEachFeature: pop_66kV_8,
            style: style_66kV_8_0,
        });
        bounds_group.addLayer(layer_66kV_8);
        map.addLayer(layer_66kV_8);
        function pop_MT_lines_9(feature, layer) {
            layer.on({
                mouseout: function(e) {
                    for (i in e.target._eventParents) {
                        e.target._eventParents[i].resetStyle(e.target);
                    }
                    if (typeof layer.closePopup == 'function') {
                        layer.closePopup();
                    } else {
                        layer.eachLayer(function(feature){
                            feature.closePopup()
                        });
                    }
                },
                mouseover: highlightFeature,
            });
        }

        function style_MT_lines_9_0() {
            return {
                pane: 'pane_MT_lines_9',
                opacity: 1,
                color: 'rgba(0,170,0,1.0)',
                dashArray: '',
                lineCap: 'square',
                lineJoin: 'bevel',
                weight: 1.0,
                fillOpacity: 0,
                interactive: true,
            }
        }
        map.createPane('pane_MT_lines_9');
        map.getPane('pane_MT_lines_9').style.zIndex = 409;
        map.getPane('pane_MT_lines_9').style['mix-blend-mode'] = 'normal';
        var layer_MT_lines_9 = new L.geoJson(json_MT_lines_9, {
            attribution: '',
            interactive: true,
            dataVar: 'json_MT_lines_9',
            layerName: 'layer_MT_lines_9',
            pane: 'pane_MT_lines_9',
            onEachFeature: pop_MT_lines_9,
            style: style_MT_lines_9_0,
        });
        bounds_group.addLayer(layer_MT_lines_9);
        map.addLayer(layer_MT_lines_9);
        function pop_NIGELECisolatedcenters_10(feature, layer) {
            layer.on({
                mouseout: function(e) {
                    for (i in e.target._eventParents) {
                        e.target._eventParents[i].resetStyle(e.target);
                    }
                    if (typeof layer.closePopup == 'function') {
                        layer.closePopup();
                    } else {
                        layer.eachLayer(function(feature){
                            feature.closePopup()
                        });
                    }
                },
                mouseover: highlightFeature,
            });
        }

        function style_NIGELECisolatedcenters_10_0() {
            return {
                pane: 'pane_NIGELECisolatedcenters_10',
        rotationAngle: 0.0,
        rotationOrigin: 'center center',
        icon: L.icon({
            iconUrl: 'markers/industry-11.svg',
            iconSize: [11.399999999999999, 11.399999999999999]
        }),
                interactive: true,
            }
        }
        map.createPane('pane_NIGELECisolatedcenters_10');
        map.getPane('pane_NIGELECisolatedcenters_10').style.zIndex = 410;
        map.getPane('pane_NIGELECisolatedcenters_10').style['mix-blend-mode'] = 'normal';
        var layer_NIGELECisolatedcenters_10 = new L.geoJson(json_NIGELECisolatedcenters_10, {
            attribution: '',
            interactive: true,
            dataVar: 'json_NIGELECisolatedcenters_10',
            layerName: 'layer_NIGELECisolatedcenters_10',
            pane: 'pane_NIGELECisolatedcenters_10',
            onEachFeature: pop_NIGELECisolatedcenters_10,
            pointToLayer: function (feature, latlng) {
                var context = {
                    feature: feature,
                    variables: {}
                };
                return L.marker(latlng, style_NIGELECisolatedcenters_10_0(feature));
            },
        });
        bounds_group.addLayer(layer_NIGELECisolatedcenters_10);
        map.addLayer(layer_NIGELECisolatedcenters_10);
        function pop_grid_Niger_11(feature, layer) {
            layer.on({
                mouseout: function(e) {
                    for (i in e.target._eventParents) {
                        e.target._eventParents[i].resetStyle(e.target);
                    }
                    if (typeof layer.closePopup == 'function') {
                        layer.closePopup();
                    } else {
                        layer.eachLayer(function(feature){
                            feature.closePopup()
                        });
                    }
                },
                mouseover: highlightFeature,
            });
        }

        function style_grid_Niger_11_0(feature) {
            switch(String(feature.properties['Statut'])) {
                case 'Existant':
                    return {
                pane: 'pane_grid_Niger_11',
        rotationAngle: 0.0,
        rotationOrigin: 'center center',
        icon: L.icon({
            iconUrl: 'markers/power-plant-svgrepo-com.svg',
            iconSize: [22.799999999999997, 22.799999999999997]
        }),
                interactive: true,
            }
                    break;
                case 'Projet':
                    return {
                pane: 'pane_grid_Niger_11',
        rotationAngle: 0.0,
        rotationOrigin: 'center center',
        icon: L.icon({
            iconUrl: 'markers/power-plant-svgrepo-com.svg',
            iconSize: [22.799999999999997, 22.799999999999997]
        }),
                interactive: true,
            }
                    break;
                default:
                    return {
                pane: 'pane_grid_Niger_11',
                radius: 4.0,
                opacity: 1,
                color: 'rgba(35,35,35,1.0)',
                dashArray: '',
                lineCap: 'butt',
                lineJoin: 'miter',
                weight: 1,
                fill: true,
                fillOpacity: 1,
                fillColor: 'rgba(202,121,107,1.0)',
                interactive: true,
            }
                    break;
            }
        }
        map.createPane('pane_grid_Niger_11');
        map.getPane('pane_grid_Niger_11').style.zIndex = 411;
        map.getPane('pane_grid_Niger_11').style['mix-blend-mode'] = 'normal';
        var layer_grid_Niger_11 = new L.geoJson(json_grid_Niger_11, {
            attribution: '',
            interactive: true,
            dataVar: 'json_grid_Niger_11',
            layerName: 'layer_grid_Niger_11',
            pane: 'pane_grid_Niger_11',
            onEachFeature: pop_grid_Niger_11,
            pointToLayer: function (feature, latlng) {
                var context = {
                    feature: feature,
                    variables: {}
                };
                return L.circleMarker(latlng, style_grid_Niger_11_0(feature));
            },
        });
        bounds_group.addLayer(layer_grid_Niger_11);
        map.addLayer(layer_grid_Niger_11);
        function pop_gadm36_BFA_3_12(feature, layer) {
            layer.on({
                mouseout: function(e) {
                    for (i in e.target._eventParents) {
                        e.target._eventParents[i].resetStyle(e.target);
                    }
                    if (typeof layer.closePopup == 'function') {
                        layer.closePopup();
                    } else {
                        layer.eachLayer(function(feature){
                            feature.closePopup()
                        });
                    }
                },
                mouseover: highlightFeature,
            });
        }

        function style_gadm36_BFA_3_12_0() {
            return {
                pane: 'pane_gadm36_BFA_3_12',
                opacity: 1,
                color: 'rgba(35,35,35,1.0)',
                dashArray: '',
                lineCap: 'butt',
                lineJoin: 'miter',
                weight: 1.0, 
                fill: true,
                fillOpacity: 1,
                fillColor: 'rgba(183,72,75,1.0)',
                interactive: true,
            }
        }
        map.createPane('pane_gadm36_BFA_3_12');
        map.getPane('pane_gadm36_BFA_3_12').style.zIndex = 412;
        map.getPane('pane_gadm36_BFA_3_12').style['mix-blend-mode'] = 'normal';
        var layer_gadm36_BFA_3_12 = new L.geoJson(json_gadm36_BFA_3_12, {
            attribution: '',
            interactive: true,
            dataVar: 'json_gadm36_BFA_3_12',
            layerName: 'layer_gadm36_BFA_3_12',
            pane: 'pane_gadm36_BFA_3_12',
            onEachFeature: pop_gadm36_BFA_3_12,
            style: style_gadm36_BFA_3_12_0,
        });
        bounds_group.addLayer(layer_gadm36_BFA_3_12);
        map.addLayer(layer_gadm36_BFA_3_12);
        function pop_gadm36_BFA_2_13(feature, layer) {
            layer.on({
                mouseout: function(e) {
                    for (i in e.target._eventParents) {
                        e.target._eventParents[i].resetStyle(e.target);
                    }
                    if (typeof layer.closePopup == 'function') {
                        layer.closePopup();
                    } else {
                        layer.eachLayer(function(feature){
                            feature.closePopup()
                        });
                    }
                },
                mouseover: highlightFeature,
            });
        }

        function style_gadm36_BFA_2_13_0() {
            return {
                pane: 'pane_gadm36_BFA_2_13',
                opacity: 1,
                color: 'rgba(35,35,35,1.0)',
                dashArray: '',
                lineCap: 'butt',
                lineJoin: 'miter',
                weight: 1.0, 
                fill: true,
                fillOpacity: 1,
                fillColor: 'rgba(231,113,72,1.0)',
                interactive: true,
            }
        }
        map.createPane('pane_gadm36_BFA_2_13');
        map.getPane('pane_gadm36_BFA_2_13').style.zIndex = 413;
        map.getPane('pane_gadm36_BFA_2_13').style['mix-blend-mode'] = 'normal';
        var layer_gadm36_BFA_2_13 = new L.geoJson(json_gadm36_BFA_2_13, {
            attribution: '',
            interactive: true,
            dataVar: 'json_gadm36_BFA_2_13',
            layerName: 'layer_gadm36_BFA_2_13',
            pane: 'pane_gadm36_BFA_2_13',
            onEachFeature: pop_gadm36_BFA_2_13,
            style: style_gadm36_BFA_2_13_0,
        });
        bounds_group.addLayer(layer_gadm36_BFA_2_13);
        map.addLayer(layer_gadm36_BFA_2_13);
        function pop_gadm36_BFA_1_14(feature, layer) {
            layer.on({
                mouseout: function(e) {
                    for (i in e.target._eventParents) {
                        e.target._eventParents[i].resetStyle(e.target);
                    }
                    if (typeof layer.closePopup == 'function') {
                        layer.closePopup();
                    } else {
                        layer.eachLayer(function(feature){
                            feature.closePopup()
                        });
                    }
                },
                mouseover: highlightFeature,
            });
        }

        function style_gadm36_BFA_1_14_0() {
            return {
                pane: 'pane_gadm36_BFA_1_14',
                opacity: 1,
                color: 'rgba(50,50,50,1.0)',
                dashArray: '',
                lineCap: 'butt',
                lineJoin: 'miter',
                weight: 1.0, 
                fill: true,
                fillOpacity: 1,
                fillColor: 'rgba(190,178,151,0.0)',
                interactive: true,
            }
        }
        map.createPane('pane_gadm36_BFA_1_14');
        map.getPane('pane_gadm36_BFA_1_14').style.zIndex = 414;
        map.getPane('pane_gadm36_BFA_1_14').style['mix-blend-mode'] = 'normal';
        var layer_gadm36_BFA_1_14 = new L.geoJson(json_gadm36_BFA_1_14, {
            attribution: '',
            interactive: true,
            dataVar: 'json_gadm36_BFA_1_14',
            layerName: 'layer_gadm36_BFA_1_14',
            pane: 'pane_gadm36_BFA_1_14',
            onEachFeature: pop_gadm36_BFA_1_14,
            style: style_gadm36_BFA_1_14_0,
        });
        bounds_group.addLayer(layer_gadm36_BFA_1_14);
        map.addLayer(layer_gadm36_BFA_1_14);
        function pop_gadm36_BFA_0_15(feature, layer) {
            layer.on({
                mouseout: function(e) {
                    for (i in e.target._eventParents) {
                        e.target._eventParents[i].resetStyle(e.target);
                    }
                    if (typeof layer.closePopup == 'function') {
                        layer.closePopup();
                    } else {
                        layer.eachLayer(function(feature){
                            feature.closePopup()
                        });
                    }
                },
                mouseover: highlightFeature,
            });
        }

        function style_gadm36_BFA_0_15_0() {
            return {
                pane: 'pane_gadm36_BFA_0_15',
                opacity: 1,
                color: 'rgba(35,35,35,1.0)',
                dashArray: '',
                lineCap: 'butt',
                lineJoin: 'miter',
                weight: 1.0, 
                fill: true,
                fillOpacity: 1,
                fillColor: 'rgba(190,207,80,1.0)',
                interactive: true,
            }
        }
        map.createPane('pane_gadm36_BFA_0_15');
        map.getPane('pane_gadm36_BFA_0_15').style.zIndex = 415;
        map.getPane('pane_gadm36_BFA_0_15').style['mix-blend-mode'] = 'normal';
        var layer_gadm36_BFA_0_15 = new L.geoJson(json_gadm36_BFA_0_15, {
            attribution: '',
            interactive: true,
            dataVar: 'json_gadm36_BFA_0_15',
            layerName: 'layer_gadm36_BFA_0_15',
            pane: 'pane_gadm36_BFA_0_15',
            onEachFeature: pop_gadm36_BFA_0_15,
            style: style_gadm36_BFA_0_15_0,
        });
        bounds_group.addLayer(layer_gadm36_BFA_0_15);
        map.addLayer(layer_gadm36_BFA_0_15);
        var osmGeocoder = new L.Control.Geocoder({
            collapsed: true,
            position: 'topleft',
            text: 'Search',
            title: 'Testing'
        }).addTo(map);
        document.getElementsByClassName('leaflet-control-geocoder-icon')[0]
        .className += ' fa fa-search';
        document.getElementsByClassName('leaflet-control-geocoder-icon')[0]
        .title += 'Search for a place';
        var baseMaps = {};
        L.control.layers(baseMaps,{'<img src="legend/gadm36_BFA_0_15.png" /> gadm36_BFA_0': layer_gadm36_BFA_0_15,'<img src="legend/gadm36_BFA_1_14.png" /> gadm36_BFA_1': layer_gadm36_BFA_1_14,'<img src="legend/gadm36_BFA_2_13.png" /> gadm36_BFA_2': layer_gadm36_BFA_2_13,'<img src="legend/gadm36_BFA_3_12.png" /> gadm36_BFA_3': layer_gadm36_BFA_3_12,'grid_Niger<br /><table><tr><td style="text-align: center;"><img src="legend/grid_Niger_11_Existant0.png" /></td><td>Existant</td></tr><tr><td style="text-align: center;"><img src="legend/grid_Niger_11_Projet1.png" /></td><td>Projet</td></tr><tr><td style="text-align: center;"><img src="legend/grid_Niger_11_2.png" /></td><td></td></tr></table>': layer_grid_Niger_11,'<img src="legend/NIGELECisolatedcenters_10.png" /> NIGELEC isolated centers': layer_NIGELECisolatedcenters_10,'<img src="legend/MT_lines_9.png" /> MT_lines': layer_MT_lines_9,'<img src="legend/66kV_8.png" /> 66kV': layer_66kV_8,'<img src="legend/132kV_7.png" /> 132kV': layer_132kV_7,"Google Maps": layer_GoogleMaps_6,"Stamen Toner Light": layer_StamenTonerLight_5,"Topo": layer_Topo_4,"OSM Humanitarian Data Model": layer_OSMHumanitarianDataModel_3,"OpenStreetMap": layer_OpenStreetMap_2,"Google Hybrid": layer_GoogleHybrid_1,"ESRI Satellite": layer_ESRISatellite_0,},{collapsed:false}).addTo(map);
        setBounds();
        var i = 0;
        layer_gadm36_BFA_1_14.eachLayer(function(layer) {
            var context = {
                feature: layer.feature,
                variables: {}
            };
            layer.bindTooltip((layer.feature.properties['NAME_1'] !== null?String('<div style="color: #626262; font-size: 10pt; font-weight: bold; font-family: \'Tahoma\', sans-serif;">' + layer.feature.properties['NAME_1']) + '</div>':''), {permanent: true, offset: [-0, -16], className: 'css_gadm36_BFA_1_14'});
            labels.push(layer);
            totalMarkers += 1;
              layer.added = true;
              addLabel(layer, i);
              i++;
        });
        resetLabels([layer_gadm36_BFA_1_14]);
        map.on("zoomend", function(){
            resetLabels([layer_gadm36_BFA_1_14]);
        });
        map.on("layeradd", function(){
            resetLabels([layer_gadm36_BFA_1_14]);
        });
        map.on("layerremove", function(){
            resetLabels([layer_gadm36_BFA_1_14]);
        });
        </script>
    </body>
</html>
