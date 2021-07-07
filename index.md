<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <title>Demo: Build a store locator using Mapbox GL JS</title>
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <script src="https://api.tiles.mapbox.com/mapbox-gl-js/v2.2.0/mapbox-gl.js"></script>
    <link
      href="https://api.tiles.mapbox.com/mapbox-gl-js/v2.2.0/mapbox-gl.css"
      rel="stylesheet"
    />
    <style>
    body {
color: #404040;
font: 400 15px/22px 'Source Sans Pro', 'Helvetica Neue', Sans-serif;
margin: 0;
padding: 0;
-webkit-font-smoothing: antialiased;
}

* {
-webkit-box-sizing: border-box;
-moz-box-sizing: border-box;
box-sizing: border-box;
}

.sidebar {
position: absolute;
width: 33.3333%;
height: 100%;
top: 0;
left: 0;
overflow: hidden;
border-right: 1px solid rgba(0, 0, 0, 0.25);
}

.map {
position: absolute;
left: 33.3333%;
width: 66.6666%;
top: 0;
bottom: 0;
}

h1 {
font-size: 22px;
margin: 0;
font-weight: 400;
line-height: 20px;
padding: 20px 2px;
}

a {
color: #404040;
text-decoration: none;
}

a:hover {
color: #101010;
}

.heading {
background: #fff;
border-bottom: 1px solid #eee;
min-height: 60px;
line-height: 60px;
padding: 0 10px;
background-color: #00853e;
color: #fff;
}

.listings {
height: 100%;
overflow: auto;
padding-bottom: 60px;
}

.listings .item {
display: block;
border-bottom: 1px solid #eee;
padding: 10px;
text-decoration: none;
}

.listings .item:last-child {
border-bottom: none;
}
.listings .item .title {
display: block;
color: #00853e;
font-weight: 700;
}

.listings .item .title small {
font-weight: 400;
}
.listings .item.active .title,
.listings .item .title:hover {
color: #8cc63f;
}
.listings .item.active {
background-color: #f8f8f8;
}
::-webkit-scrollbar {
width: 3px;
height: 3px;
border-left: 0;
background: rgba(0, 0, 0, 0.1);
}
::-webkit-scrollbar-track {
background: none;
}
::-webkit-scrollbar-thumb {
background: #00853e;
border-radius: 0;
}

.marker {
border: none;
cursor: pointer;
height: 56px;
width: 56px;
background-image: url(marker.png);
background-color: rgba(0, 0, 0, 0);
}

.clearfix {
display: block;
}
.clearfix:after {
content: '.';
display: block;
height: 0;
clear: both;
visibility: hidden;
}

/* Marker tweaks */
.mapboxgl-popup {
    max-width: 600px;
    font: 12px/20px 'Helvetica Neue', Arial, Helvetica, sans-serif;
}

.mapboxgl-popup-close-button {
display: ;
}
.mapboxgl-popup-content {
font: 400 15px/22px 'Source Sans Pro', 'Helvetica Neue', Sans-serif;
padding: 0;
width: 180px;
}
.mapboxgl-popup-content-wrapper {
padding: 1%;
}
.mapboxgl-popup-content h3 {
background: #91c949;
color: #fff;
margin: 0;
display: block;
padding: 10px;
border-radius: 3px 3px 0 0;
font-weight: 700;
margin-top: -15px;
}

.mapboxgl-popup-content h4 {
margin: 0;
display: block;
padding: 10px 10px 10px 10px;
font-weight: 400;
}

.mapboxgl-popup-content div {
padding: 10px;
}

.mapboxgl-container .leaflet-marker-icon {
cursor: pointer;
}

.mapboxgl-popup-anchor-top > .mapboxgl-popup-content {
margin-top: 15px;
}

.mapboxgl-popup-anchor-top > .mapboxgl-popup-tip {
border-bottom-color: #91c949;
}
</style>
  </head>
  <body>
    <div class="sidebar">
      <div class="heading">
        <h1>Our 203 locations</h1>
      </div>
      <div id="listings" class="listings"></div>
    </div>
    <div id="map" class="map"></div>
<script>
      /* This will let you use the .remove() function later on */
  if (!('remove' in Element.prototype)) {
        Element.prototype.remove = function () {
          if (this.parentNode) {
            this.parentNode.removeChild(this);
                        }
                      };
                    }

mapboxgl.accessToken = 'pk.eyJ1IjoiY2FibGFja3dlbGwiLCJhIjoiY2tvYm5nbDU4MDB4YTJucWE4NDR5cWN5eCJ9.gP8HwLo3YCdhIFMVSLM2HA';


var map = new mapboxgl.Map({
    container: 'map',
    style: 'mapbox://styles/cablackwell/ckon4qsq73jiw18mukn41lna7',
    center: [-73.9712, 40.731],
    zoom: 10,
    scrollZoom: true
      });

var stores = {
                  'type': 'FeatureCollection',
                  'features': [
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Princess Road Warehouse",
                        "Address": "2 Princess Rd, Lawrenceville, NJ 08648",
                        "Service": "Janitorial Services",
                        "Contract": "ACCESS NJ"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.989308,
                          40.741895
                        ],
                        "type": "Point"
                      },
                      "id": "00c20f600b144681363cb761e97698bd"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Bostetter Courthouse",
                        "Address": "200 S. Washington Street, Alexandria, VA",
                        "Service": "Janitorial Services",
                        "Contract": "MVLE"
                      },
                      "geometry": {
                        "coordinates": [
                          -77.046641,
                          38.803617
                        ],
                        "type": "Point"
                      },
                      "id": "01e0c4ff3774a114a15641d0652f5b19"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "NYS Department of Labor Church St",
                        "Address": "99 Church StNew York, NY 10007",
                        "Service": "Office Services: Messenger, mail sort, delivery",
                        "Contract": "NYSID"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.006762,
                          40.716229
                        ],
                        "type": "Point"
                      },
                      "id": "0236a4e2d8bd3578b0ab9bd9320d750f"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Ft. Hamilton Funded thru May 2021",
                        "Address": "Fort Hamilton, Brooklyn, NY",
                        "Service": "Janitorial Services",
                        "Contract": "Source America"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.028543,
                          40.6094
                        ],
                        "type": "Point"
                      },
                      "id": "023dabf4c02f410958f0c39a5695f9d0"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "NJ Training School for Boys-JJC",
                        "Address": "1 State Home Rd., Monroe Township, NJ 08831-0500",
                        "Service": "Janitorial Services",
                        "Contract": "ACCESS NJ"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.420999,
                          40.341471
                        ],
                        "type": "Point"
                      },
                      "id": "05ea178373814368aed87ff2a5d397ab"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Manhattan Medical Clinic",
                        "Address": "344 West 51st Street, New York, NY 10019",
                        "Service": "Medical Clinic",
                        "Contract": "Fedcap WeCare"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.987564,
                          40.763587
                        ],
                        "type": "Point"
                      },
                      "id": "06a440f480a87a7af2c794ff59f33271"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Bank Street Garage",
                        "Address": "28 Bank St, Trenton, NJ 08618",
                        "Service": "Janitorial Services",
                        "Contract": "ACCESS NJ"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.7669,
                          40.22306
                        ],
                        "type": "Point"
                      },
                      "id": "0776ee55e187ff2a43d36084b2f51f12"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "LIRR Janitorial",
                        "Address": "Pennsylvania Station, New York, NY 10119",
                        "Service": "Janitorial Services",
                        "Contract": "NYSID"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.99347,
                          40.750562
                        ],
                        "type": "Point"
                      },
                      "id": "07885306b1a1758452f4fb6cab90d04a"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Chelton Loft",
                        "Address": "104-106 East 126th Street, New York, NY 10035",
                        "Service": "Occupational Health Services",
                        "Contract": "Fedcap NY"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.937982,
                          40.805377
                        ],
                        "type": "Point"
                      },
                      "id": "07f808f761924631573d1f211d7559ab"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "IRS",
                        "Address": "290 Broadway, NY, NY",
                        "Service": "Mailroom",
                        "Contract": "Source America"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.005182,
                          40.714739
                        ],
                        "type": "Point"
                      },
                      "id": "0a8404e309b54e3a09c2314a8b2c38a2"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Jamesburg Home for Boys- New Jersey Training School ",
                        "Address": "Grace Hill Rd, Monroe Township, NJ 08831",
                        "Service": "Janitorial Services",
                        "Contract": "ACCESS NJ"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.408201,
                          40.342839
                        ],
                        "type": "Point"
                      },
                      "id": "0b6c9b9c8cf14becf2dafbf158f6bca0"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Freehold MVC ",
                        "Address": "811 Okerson Rd, Freehold Township, NJ 07728",
                        "Service": "Janitorial Services",
                        "Contract": "ACCESS NJ"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.239411,
                          40.238241
                        ],
                        "type": "Point"
                      },
                      "id": "0e1ae63c83ce7cc5f40350efe6d18b40"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Auburn (DHS)",
                        "Address": "39 Auburn Pl, Brooklyn, NY 11205",
                        "Service": "Janitorial Services",
                        "Contract": "Wildcat"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.976422,
                          40.69477
                        ],
                        "type": "Point"
                      },
                      "id": "0e3f3ce7b3b9a6353a3ec48e9e6aeb1a"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "MA Commonwealth: Employment for Disabled Young Adults",
                        "Address": "2 Oliver St, Boston, MA 02110",
                        "Service": "Supported Employment",
                        "Contract": "CWS"
                      },
                      "geometry": {
                        "coordinates": [
                          -71.053978,
                          42.357283
                        ],
                        "type": "Point"
                      },
                      "id": "0e889763ca0bdadc1ddb0571659900b4"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "271 Cadman Plaza",
                        "Address": "271 Cadman Plaza E, Brooklyn, NY 11202",
                        "Service": "GSA COVID-19 Screening, Mechanical & Elevator Maintenance",
                        "Contract": "Source America"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.989979,
                          40.695907
                        ],
                        "type": "Point"
                      },
                      "id": "0ea474f29ee2aa7f6c966d3c1fcca5d8"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "NYC Dept of Sanitation",
                        "Address": "All Locations",
                        "Service": "Janitorial Services",
                        "Contract": "NYSID"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.383351,
                          40.4239
                        ],
                        "type": "Point"
                      },
                      "id": "0ef4778efe4451e8528e590182aefe3e"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "NarcoFreedom Bushwick Clinic",
                        "Address": "1420 Bushwick Avenue,. Brooklyn, NY 11207",
                        "Service": "Medical Clinic",
                        "Contract": "Fedcap WeCare"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.909234,
                          40.68412
                        ],
                        "type": "Point"
                      },
                      "id": "0f70404d69349928d784be6e381d3def"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "NYC Transit Authority",
                        "Address": " 34th Street Manhattan Subway Stations",
                        "Service": "COVID Disinfecting Services",
                        "Contract": "NYSID"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.988127,
                          40.750086
                        ],
                        "type": "Point"
                      },
                      "id": "104320fa6e2902d62f465bc2ffb06c58"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Hope Forward",
                        "Address": "Blaustein Building, 1 N Charles St #1102B, Baltimore, MD 21202",
                        "Service": "Counseling, Coaching",
                        "Contract": "Fedcap US"
                      },
                      "geometry": {
                        "coordinates": [
                          -76.614825,
                          39.290112
                        ],
                        "type": "Point"
                      },
                      "id": "10e7a7dc4458a671090ed43c6716dddd"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "MVC Flemington ",
                        "Address": "181 Routes 31 & 202 B, Flemington, NJ 08822",
                        "Service": "Janitorial Services",
                        "Contract": "ACCESS NJ"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.86393,
                          40.483123
                        ],
                        "type": "Point"
                      },
                      "id": "11c01973e8b875bc3d0e9ba5f89364be"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "DOC Probation and Parole - Dover",
                        "Address": "511 Maple Parkway, Dover, DE 19901",
                        "Service": "Janitorial Services",
                        "Contract": "Delaware"
                      },
                      "geometry": {
                        "coordinates": [
                          -75.518116,
                          39.165099
                        ],
                        "type": "Point"
                      },
                      "id": "12a4f00a9b29417c2c7eec7820254264"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Acacia (DHS)",
                        "Address": "148 W 124th St, New York, NY 10027",
                        "Service": "Janitorial Services",
                        "Contract": "Wildcat"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.947991,
                          40.807653
                        ],
                        "type": "Point"
                      },
                      "id": "141f2d6ff55c7827e0c83341c5af15f0"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Christopher Brown Law Offices",
                        "Address": "3123 Atlantic Ave, Atlantic City, NJ 08401",
                        "Service": "Janitorial Services",
                        "Contract": "Commercial"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.449081,
                          39.35368
                        ],
                        "type": "Point"
                      },
                      "id": "145655dafc587753c8c0b302009b617d"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "500 Pearl Street",
                        "Address": "500 Pearl St, New York, NY 10007",
                        "Service": "Janitorial Services",
                        "Contract": "Source America"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.000869,
                          40.713662
                        ],
                        "type": "Point"
                      },
                      "id": "1469238cba29b3c2137e87e400c048f7"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "US ARC (Army Resere Ctr)",
                        "Address": "356 Battery Rd, Staten Island, NY 10305",
                        "Service": "Janitorial Services",
                        "Contract": "Source America"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.058,
                          40.600741
                        ],
                        "type": "Point"
                      },
                      "id": "14a0c66740a80c1d777b5ec83fdb46fc"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Broadway House (Berkshire-Newsbury)",
                        "Address": "Broadway House, 4-8 The Broadway, Newbury RG14 1BA, UK",
                        "Service": "Behavioral Health Services, Vocactional Rehabilitation",
                        "Contract": "Fedcap UK"
                      },
                      "geometry": {
                        "coordinates": [
                          -1.324514,
                          51.405327
                        ],
                        "type": "Point"
                      },
                      "id": "14fd8e551bfed1318feff06594b9ac0d"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Atlantic County Facility Mgmt",
                        "Address": "201 SOUTH SHORE RD, NORTHFIELD NJ 08232",
                        "Service": "Janitorial Services",
                        "Contract": "ACCESS NJ"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.537535,
                          39.376787
                        ],
                        "type": "Point"
                      },
                      "id": "1543fef27eff4e5b706ac9574ae38cf5"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Jamaica (DHS)",
                        "Address": "175-10 88th Ave, Jamaica, NY 11432",
                        "Service": "Janitorial Services",
                        "Contract": "Wildcat"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.786369,
                          40.711118
                        ],
                        "type": "Point"
                      },
                      "id": "15f2d0dfd3730415d1388fe8581d3c85"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "DelDOT Talley",
                        "Address": "1300 Talley Rd, Wilmington, DE 19809",
                        "Service": "Janitorial Services",
                        "Contract": "Delaware"
                      },
                      "geometry": {
                        "coordinates": [
                          -75.52836,
                          39.776683
                        ],
                        "type": "Point"
                      },
                      "id": "186213810c1250a57e2b40f414a93406"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Linden (DHS)",
                        "Address": "501 New Lots Ave, Brooklyn, NY 11207",
                        "Service": "Janitorial Services",
                        "Contract": "Wildcat"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.889478,
                          40.663639
                        ],
                        "type": "Point"
                      },
                      "id": "2058db6bb4923037e13ebbd73aaa4abc"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Congresswoman Yvette Clark",
                        "Address": "222 Lenox Rd Suite 2, Brooklyn, NY 11226",
                        "Service": "Janitorial Services",
                        "Contract": "Commercial"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.951677,
                          40.653588
                        ],
                        "type": "Point"
                      },
                      "id": "20a13ea8f962837f2c2377988872ac20"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Liberty Island",
                        "Address": "Liberty Island, Manhattan, New York, New York, United States of America",
                        "Service": "Janitorial Services",
                        "Contract": "Source America"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.045139,
                          40.689813
                        ],
                        "type": "Point"
                      },
                      "id": "2234953ffe7a23eae1e0bef0b31bfde8"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Public Archives Building",
                        "Address": "121 M.L.K. Jr Blvd N, Dover, DE 19901",
                        "Service": "Janitorial Services",
                        "Contract": "Delaware"
                      },
                      "geometry": {
                        "coordinates": [
                          -75.602763,
                          39.170001
                        ],
                        "type": "Point"
                      },
                      "id": "23160edb88a981f00ba5f9e770ee122c"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "201 Varick Street",
                        "Address": "201 Varick St, New York, NY 10014",
                        "Service": "Janitorial Services",
                        "Contract": "Source America"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.005561,
                          40.728325
                        ],
                        "type": "Point"
                      },
                      "id": "2603c633474d700bac1617a35bd26eed"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Bureau of Land Management",
                        "Address": "20 M St SE, Washington, DC 20003",
                        "Service": "Janitorial Services",
                        "Contract": "MVLE"
                      },
                      "geometry": {
                        "coordinates": [
                          -77.007955,
                          38.876707
                        ],
                        "type": "Point"
                      },
                      "id": "2668c52aa03e530fdd513f7b08034822"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "NJSP Bridgeton",
                        "Address": "1 Landis Ave Bridgeton, NJ",
                        "Service": "Janitorial Services",
                        "Contract": "ACCESS NJ"
                      },
                      "geometry": {
                        "coordinates": [
                          -75.207314,
                          39.461313
                        ],
                        "type": "Point"
                      },
                      "id": "2730aeb6983bb7094a0e2cafbd34fb2a"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Atlantic County Facility Mgmt",
                        "Address": "2 SOUTH MAIN STREET, PLEASANTVILLE NJ 08232",
                        "Service": "Janitorial Services",
                        "Contract": "ACCESS NJ"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.52241,
                          39.391713
                        ],
                        "type": "Point"
                      },
                      "id": "280fe1b57fe6e165cb26e06172713f49"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "FAA Teterboro",
                        "Address": "225 Fred Wehran Dr, Teterboro, NJ 07608",
                        "Service": "Janitorial Services, Grounds Maintenance",
                        "Contract": "Source America"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.055123,
                          40.852783
                        ],
                        "type": "Point"
                      },
                      "id": "2972aa401091fd6fc95ba9bb40419a0a"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Executive Headquarters",
                        "Address": "501 Madison Ave, 12A New York, NY 10022",
                        "Service": "Executive Headquarters",
                        "Contract": "Fedcap NY"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.97421,
                          40.759741
                        ],
                        "type": "Point"
                      },
                      "id": "29d9e70508a434cf829f0bc4f3ca61bc"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "DelDOT Kiamensi",
                        "Address": "39 Regal Blvd, Newark, DE 19713",
                        "Service": "Janitorial Services",
                        "Contract": "Delaware"
                      },
                      "geometry": {
                        "coordinates": [
                          -75.690211,
                          39.668384
                        ],
                        "type": "Point"
                      },
                      "id": "2cf2f80eaecb9d930ef4635fe80f1f0f"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Public Archives Building ",
                        "Address": "121 MLK Jr. Blvd, N Dover, DE 19901",
                        "Service": "Janitorial Services",
                        "Contract": "Delaware"
                      },
                      "geometry": {
                        "coordinates": [
                          -75.52037,
                          39.15844
                        ],
                        "type": "Point"
                      },
                      "id": "2ed7b3251a3522da4ffd2b29dc3abbcc"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Atlantic County Facility Mgmt",
                        "Address": "101 SOUTH SHORE RD, NORTHFIELD NJ 08232",
                        "Service": "Janitorial Services",
                        "Contract": "ACCESS NJ"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.536821,
                          39.377363
                        ],
                        "type": "Point"
                      },
                      "id": "2f544514e950990824401899171de2d1"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Granite Pathways Headquarters",
                        "Address": "10 Ferry St STE 308, Concord, NH 0330",
                        "Service": "Behavioral Health Services, Vocactional Rehabilitation",
                        "Contract": "Fedcap Group"
                      },
                      "geometry": {
                        "coordinates": [
                          -71.538173,
                          43.21275
                        ],
                        "type": "Point"
                      },
                      "id": "30ad0f493641f84648706a971d42b9ef"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "26 Federal Plaza",
                        "Address": "26 Federal PlazaNew York, NY 10278",
                        "Service": "Janitorial Services",
                        "Contract": "Source America"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.004464,
                          40.715035
                        ],
                        "type": "Point"
                      },
                      "id": "321123a2f95461140f7ec9550267c309"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Justice of Peace 3-17",
                        "Address": "23731 Shortly Rd, Georgetown, DE 19947",
                        "Service": "Janitorial Services",
                        "Contract": "Delaware"
                      },
                      "geometry": {
                        "coordinates": [
                          -75.379864,
                          38.660388
                        ],
                        "type": "Point"
                      },
                      "id": "37dc276fe0f719e1431dc313a81fcb03"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Thomas Collins Building",
                        "Address": " 540 S. Dupont Hwy, Dover, DE 19904",
                        "Service": "Janitorial Services",
                        "Contract": "Delaware"
                      },
                      "geometry": {
                        "coordinates": [
                          -75.513967,
                          39.154067
                        ],
                        "type": "Point"
                      },
                      "id": "3870f9d121c83bfb7c564dc79cbbe770"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "NASA Headquarters",
                        "Address": "300 E St SW, Washington, DC 20546",
                        "Service": "Janitorial Services",
                        "Contract": "MVLE"
                      },
                      "geometry": {
                        "coordinates": [
                          -77.016278,
                          38.883064
                        ],
                        "type": "Point"
                      },
                      "id": "3aa10e1a2f811e66a2a6606a786cf739"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Armory Men's shelter (DHS)",
                        "Address": "1322 Bedford Ave, Brooklyn, NY 11216",
                        "Service": "Janitorial Services",
                        "Contract": "Wildcat"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.953727,
                          40.67839
                        ],
                        "type": "Point"
                      },
                      "id": "3b3960947277c9f1ff86cea6fe74d2f9"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Battery Park",
                        "Address": "Battery Park, Manhattan, New York, New York, United States of America",
                        "Service": "Janitorial Services",
                        "Contract": "Source America"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.015824,
                          40.703011
                        ],
                        "type": "Point"
                      },
                      "id": "3cb3bf6a63edb96cf389da36220a518e"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "USCG Sea Isle City Grounds Services April-Oct Only",
                        "Address": "8101 Landis AveSea Isle City, NJ 08243",
                        "Service": " Grounds Maintenance",
                        "Contract": "Source America"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.709244,
                          39.128418
                        ],
                        "type": "Point"
                      },
                      "id": "3cea330d484002e8ee8e2efd7e337983"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Memorial Sloan Kettering",
                        "Address": "163 W 25th Street, NYC (ACP Office Bldg)",
                        "Service": "Janitorial Services",
                        "Contract": "Commercial"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.994123,
                          40.745359
                        ],
                        "type": "Point"
                      },
                      "id": "3cff94e7a55cdced7df0b5ee6d465f1b"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "FAA Morristown",
                        "Address": "8 Airport Rd, Morristown, NJ 07960",
                        "Service": "Janitorial Services",
                        "Contract": "Source America"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.423985,
                          40.792506
                        ],
                        "type": "Point"
                      },
                      "id": "3e6dbee7854a76206f733e23de063be7"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "NYC OATH, NYC Council & Health Department, Housing Trust Fund, LIRR, HPD, NYS Orange County, Light Marker",
                        "Address": "1231 Lafayette Ave, Bronx, NY 10474",
                        "Service": " Document Management, Office Mail Services, Custodial, Manufacturing",
                        "Contract": "Commercial"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.890603,
                          40.816759
                        ],
                        "type": "Point"
                      },
                      "id": "40f0c6e740efc0dfb46217b32e9bc58f"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Career Design School",
                        "Address": "210 East 43rd Street, New York, NY 10017",
                        "Service": "Employment Support",
                        "Contract": "Fedcap NY"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.973312,
                          40.751039
                        ],
                        "type": "Point"
                      },
                      "id": "416af7e9dc4a3a4935f4bb2960d568fe"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "National Museum of Health",
                        "Address": "2500 Linden Lane, Silver Spring, Maryland",
                        "Service": "Janitorial Services",
                        "Contract": "MVLE"
                      },
                      "geometry": {
                        "coordinates": [
                          -77.053118,
                          39.008683
                        ],
                        "type": "Point"
                      },
                      "id": "42aa46ccafdc8e75927e9dc622f2bb17"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "NYC HRA Downtown - 60 Lafayette St",
                        "Address": "60 Lafayette St, New York, NY 10013",
                        "Service": "Janitorial Services",
                        "Contract": "NYSID"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.002589,
                          40.71661
                        ],
                        "type": "Point"
                      },
                      "id": "432ea99341cccff86174084213937bbf"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Alexandria Twp. Board of Education",
                        "Address": "Lester Wilson Elementary School 525 Rte. 513, Pittstown , NJ 08867",
                        "Service": "Janitorial Services",
                        "Contract": "ACCESS NJ"
                      },
                      "geometry": {
                        "coordinates": [
                          -75.025673,
                          40.566918
                        ],
                        "type": "Point"
                      },
                      "id": "4373714e89de70f166ad0ea8d9680c5e"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "CWS - Rhode Island",
                        "Address": "20 Marblehead Ave, North Providence, RI 02904",
                        "Service": "Affiliate Organization",
                        "Contract": "CWS"
                      },
                      "geometry": {
                        "coordinates": [
                          -71.456883,
                          41.861142
                        ],
                        "type": "Point"
                      },
                      "id": "4378354be92f3aba031d9b2997141839"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "FAIRFAX CSB",
                        "Address": "8221 Willow Oaks Corporate Dr, Fairfax, VA 22031",
                        "Service": "Supported Employment",
                        "Contract": "MVLE"
                      },
                      "geometry": {
                        "coordinates": [
                          -77.233959,
                          38.863724
                        ],
                        "type": "Point"
                      },
                      "id": "4444dca1f49be8328000bc2440bddf37"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "GSA Manhattan",
                        "Address": "201 Varick St #102, New York, NY 10014",
                        "Service": "Janitorial Services & COVID-19 Disinfecting Services",
                        "Contract": "Source America"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.012906,
                          40.71321
                        ],
                        "type": "Point"
                      },
                      "id": "49bd4dfe3ccca9699fb715c40fabcfff"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Atlantic County Facility Mgmt",
                        "Address": "235 DOLPHIN AVE, NORTHFIELD NJ 08232",
                        "Service": "Janitorial Services",
                        "Contract": "ACCESS NJ"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.543998,
                          39.379539
                        ],
                        "type": "Point"
                      },
                      "id": "4a467b1a62227de4120c7837bb1d69d1"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "DelDOT Talley ",
                        "Address": "1300 Talley Road, Wilmington, DE 19803",
                        "Service": "Janitorial Services",
                        "Contract": "Delaware"
                      },
                      "geometry": {
                        "coordinates": [
                          -75.52822,
                          39.77661
                        ],
                        "type": "Point"
                      },
                      "id": "4aeb1ae7b0e9d64bf5416593b1ed18a3"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "NYS Department of Labor Church St",
                        "Address": "199 Church St, New York, NY 10007",
                        "Service": "Office Services: Messenger, mail sort, delivery",
                        "Contract": "NYSID"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.006762,
                          40.716229
                        ],
                        "type": "Point"
                      },
                      "id": "4beeea3e4e21c7c469a3e225be37891e"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Ellis Island",
                        "Address": "Ellis Island, Manhattan, Jersey City, New Jersey, United States of America",
                        "Service": "Janitorial Services",
                        "Contract": "Source America"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.042013,
                          40.698593
                        ],
                        "type": "Point"
                      },
                      "id": "4c7f990d1fd6f69e7424966d2d0c0fe5"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "ICE Courier",
                        "Address": "290 Broadway, New York, NY 10007",
                        "Service": "Courier Services",
                        "Contract": "Source America"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.989308,
                          40.741895
                        ],
                        "type": "Point"
                      },
                      "id": "4e3f2b1d27c776bfe90491ab89f6b224"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "NYC Transit Authority",
                        "Address": " 130 Livingston Street, Brooklyn, NY",
                        "Service": "Janitorial Services",
                        "Contract": "NYSID"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.988746,
                          40.690388
                        ],
                        "type": "Point"
                      },
                      "id": "4e8f55a417e4a22e0f663729d1be4294"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Tatnall Building",
                        "Address": " 150 William Penn St. Dover, DE 19901",
                        "Service": "Janitorial Services",
                        "Contract": "Delaware"
                      },
                      "geometry": {
                        "coordinates": [
                          -75.519617,
                          39.156333
                        ],
                        "type": "Point"
                      },
                      "id": "4ef957dad3353b823e736499e05d84ec"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "NYC Transit Authority",
                        "Address": "46-25 Metropolitan Ave, Queens, NY 11385",
                        "Service": "Janitorial Services",
                        "Contract": "NYSID"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.923202,
                          40.714756
                        ],
                        "type": "Point"
                      },
                      "id": "4fa915e310eac225120ab057dcdcabe2"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "1 St Andrews",
                        "Address": "1 Saint Andrews PlazaNew York, NY 10007",
                        "Service": "Janitorial Services",
                        "Contract": "Source America"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.002678,
                          40.712912
                        ],
                        "type": "Point"
                      },
                      "id": "4ff77a3d511185c244938245007226e4"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "US Coast Guard (USCG)",
                        "Address": "Coast Guard Dr, Staten Island, NY 10305",
                        "Service": " Mess Attendant (Food Services)",
                        "Contract": "Source America"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.062713,
                          40.604567
                        ],
                        "type": "Point"
                      },
                      "id": "5008c6be278151456660c1092aa9459b"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "NJN",
                        "Address": "25 S Stockton St, Trenton, NJ 08608",
                        "Service": "Janitorial Services",
                        "Contract": "ACCESS NJ"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.76001,
                          40.21945
                        ],
                        "type": "Point"
                      },
                      "id": "50436ac4ece9ebaf05fcf96a9a488b54"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "NYS DMV",
                        "Address": "159 E 125th StNew York, NY 10035",
                        "Service": "COVID Disinfecting Services",
                        "Contract": "NYSID"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.936586,
                          40.804231
                        ],
                        "type": "Point"
                      },
                      "id": "51589a0938d280f1673826a84ea34581"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Alexandria Middle School",
                        "Address": "557 Rte. 513, Pittstown , NJ 08867",
                        "Service": "Janitorial Services",
                        "Contract": "ACCESS NJ"
                      },
                      "geometry": {
                        "coordinates": [
                          -75.015167,
                          40.570443
                        ],
                        "type": "Point"
                      },
                      "id": "515f44d063cd287930c9572fcc5fec91"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Brookyln Service Site",
                        "Address": "200 Montague Street, Brooklyn, NY 11201",
                        "Service": "Clinic Support Services",
                        "Contract": "Fedcap WeCare"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.991221,
                          40.693747
                        ],
                        "type": "Point"
                      },
                      "id": "51a85f4173f70f4fcae5ef9ecd458eee"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Dover Toll Plaza",
                        "Address": " 200 Plaza Drive, Dover DE 19904",
                        "Service": "Janitorial Services",
                        "Contract": "Delaware"
                      },
                      "geometry": {
                        "coordinates": [
                          -75.521244,
                          39.188702
                        ],
                        "type": "Point"
                      },
                      "id": "53563fee1a7c2ce7dc38821eaf92a8d8"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Rodino Building: Rodino USCIS",
                        "Address": "970 Broad St, Newark, NJ 07102",
                        "Service": "anitorial Services/ Mech Maintenance",
                        "Contract": "Source America"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.172373,
                          40.730233
                        ],
                        "type": "Point"
                      },
                      "id": "541f5b3bd7676e43b827580d7828415a"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Kings Borough (DHS)",
                        "Address": "599 Clarkson Ave, Brooklyn, NY 11203",
                        "Service": "Janitorial Services",
                        "Contract": "Wildcat"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.939242,
                          40.656529
                        ],
                        "type": "Point"
                      },
                      "id": "553e6854c74ad29ce44f20b567e2efe2"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Wilburtha NJSP Welcome Center",
                        "Address": "1020 River Rd., Ewing, NJ 08628",
                        "Service": "Janitorial Services",
                        "Contract": "ACCESS NJ"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.847202,
                          40.265604
                        ],
                        "type": "Point"
                      },
                      "id": "55c45bd258c1b13d9dc67b8672575da2"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Back to Work Bronx/ Employment Works",
                        "Address": "369 East 148th Street, Bronx, NY 10455",
                        "Service": "Employment Support",
                        "Contract": "Fedcap NY"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.919035,
                          40.815922
                        ],
                        "type": "Point"
                      },
                      "id": "55f53f16366ddf3a50828cb7c832906d"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "First Ave Warehouse ",
                        "Address": "1st Ave, Trenton, NJ, United States of America",
                        "Service": "Janitorial Services",
                        "Contract": "ACCESS NJ"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.731057,
                          40.241874
                        ],
                        "type": "Point"
                      },
                      "id": "56d946f7b3b7b8f4de6b5e56bab9679a"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Hudson River Park Trust",
                        "Address": "353 West St, New York, NY 10011",
                        "Service": "Janitorial Services",
                        "Contract": "NYSID"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.011028,
                          40.733069
                        ],
                        "type": "Point"
                      },
                      "id": "5987454aed3c49468be9a4fb5a87b9a8"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Margaret O'Neill Building",
                        "Address": "410 Federal Street, Dover, DE 19901",
                        "Service": "Janitorial Services",
                        "Contract": "Delaware"
                      },
                      "geometry": {
                        "coordinates": [
                          -75.522347,
                          39.156439
                        ],
                        "type": "Point"
                      },
                      "id": "5b0a614d6fd0259ef1dd1d74b989c88a"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Manhattan Service Site",
                        "Address": "80 Vandam Street, New York, NY 10013",
                        "Service": "Clinic Support Services",
                        "Contract": "Fedcap WeCare"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.007975,
                          40.726487
                        ],
                        "type": "Point"
                      },
                      "id": "5ff691debd7d531011e887f481233e47"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "DelDOT Survey Office & Construction Trailer",
                        "Address": "39 East Regal Blvd,Newark, DE 19713",
                        "Service": "Janitorial Services",
                        "Contract": "Delaware"
                      },
                      "geometry": {
                        "coordinates": [
                          -75.690669,
                          39.669951
                        ],
                        "type": "Point"
                      },
                      "id": "61543e09deeea8daa097e5375b0ecaa1"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Jesse Cooper",
                        "Address": "417 Federal Street Dover, DE 19901",
                        "Service": "Janitorial Services",
                        "Contract": "Delaware"
                      },
                      "geometry": {
                        "coordinates": [
                          -75.521164,
                          39.155732
                        ],
                        "type": "Point"
                      },
                      "id": "619ea69d8faddce6df94eb6f2dcce501"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Atlantic County Drexel Ave M B",
                        "Address": "1227 DREXEL AVE, ATLANTIC CITY NJ 08401",
                        "Service": "Janitorial Services",
                        "Contract": "ACCESS NJ"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.429438,
                          39.367432
                        ],
                        "type": "Point"
                      },
                      "id": "6228e78aff3e24df3977f2ea108b3b5a"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "MVC Turnersville ",
                        "Address": "5200 Rt. 42 North, Turnersville, NJ 08012",
                        "Service": "Janitorial Services",
                        "Contract": "ACCESS NJ"
                      },
                      "geometry": {
                        "coordinates": [
                          -75.0463,
                          39.752587
                        ],
                        "type": "Point"
                      },
                      "id": "63021a0dd0d8ead037db154bff0e5a48"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Delaware Fire and Training School",
                        "Address": "2311 McArthur Dr. New Castle, DE 19720",
                        "Service": "Janitorial Services",
                        "Contract": "Delaware"
                      },
                      "geometry": {
                        "coordinates": [
                          -75.615581,
                          39.690545
                        ],
                        "type": "Point"
                      },
                      "id": "63b5fa0caae7c1398131b0068789eb0d"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Marshal’s Office ",
                        "Address": "151 Eggert Crossing Rd, Lawrenceville, NJ 08648",
                        "Service": "Janitorial Services",
                        "Contract": "ACCESS NJ"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.73819,
                          40.270679
                        ],
                        "type": "Point"
                      },
                      "id": "63f9d5a0e9c8986648714ab9560f2a8c"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "NYS Department of Labor",
                        "Address": "9 Bond St, NYC",
                        "Service": "Office Services: Messenger, mail sort, delivery",
                        "Contract": "NYSID"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.12946,
                          40.63455
                        ],
                        "type": "Point"
                      },
                      "id": "640294e45766c1fbe09484abd2ae4253"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Bronx Medical Site",
                        "Address": "1276 Fulton Avenue, Bronx, NY 10456 ",
                        "Service": "Medical Clinic",
                        "Contract": "Fedcap WeCare"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.902808,
                          40.831375
                        ],
                        "type": "Point"
                      },
                      "id": "640305b8da2af3ca0434d09c86ab311a"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "NSLIJ Rego Park Urgent Care Center",
                        "Address": "95-25 Queens Boulevard,Rego Park, NY 11374",
                        "Service": "Medical Clinic",
                        "Contract": "Fedcap WeCare"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.863132,
                          40.730836
                        ],
                        "type": "Point"
                      },
                      "id": "64948f64307d3911d4c0ad034e8090c8"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Addabbo",
                        "Address": "155-10 Jamaica Ave, Jamaica, NY 11432",
                        "Service": "Janitorial Services",
                        "Contract": "Source America"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.800927,
                          40.702726
                        ],
                        "type": "Point"
                      },
                      "id": "663d383640d28e183ec66f92137dae8a"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "*Potential July1st start* Flemington DCF",
                        "Address": "84 Park Avenue, 1st Floor Flemington, NJ 08822 ",
                        "Service": "Janitorial Services",
                        "Contract": "ACCESS NJ"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.86155,
                          40.514115
                        ],
                        "type": "Point"
                      },
                      "id": "66b69d6fcc1f84342a2054e1d54bd08a"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "NJSPB, Regional Fugitive Task Force\n",
                        "Address": "141 Eggert's Crossing Rd, Lawrenceville, NJ 08648",
                        "Service": "Janitorial Services",
                        "Contract": "ACCESS NJ"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.743236,
                          40.27229
                        ],
                        "type": "Point"
                      },
                      "id": "6887d61a03b5c961558fa6b58d1a6aaa"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Fitzwilliam County",
                        "Address": "Fitzwilliam County, NH",
                        "Service": "Supported Employment",
                        "Contract": "MVLE"
                      },
                      "geometry": {
                        "coordinates": [
                          -72.141667,
                          42.780556
                        ],
                        "type": "Point"
                      },
                      "id": "6bfca0c22336e55752bd7a029a3734dc"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "BELLEVUE (DHS)",
                        "Address": "400 E 30th St, New York, NY 10016",
                        "Service": "Janitorial Services",
                        "Contract": "Wildcat"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.974771,
                          40.740577
                        ],
                        "type": "Point"
                      },
                      "id": "6c32069ed8e8cd104c3943adff16b29e"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "DLA Maritme Portsmouth Naval Yard Packaging Hoodies & Booties",
                        "Address": "Portsmouth, VA 23704",
                        "Service": "Supported Employment",
                        "Contract": "CWS"
                      },
                      "geometry": {
                        "coordinates": [
                          -76.296317,
                          36.823613
                        ],
                        "type": "Point"
                      },
                      "id": "6cf48f49658d64da4edf0a3a834879dc"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "40 Centre St",
                        "Address": "40 Centre St, New York, NY 10007",
                        "Service": "Janitorial Services",
                        "Contract": "Source America"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.002656,
                          40.713749
                        ],
                        "type": "Point"
                      },
                      "id": "6d8c7907d9c70cd3fe403ad928d792dc"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Dayton MVC ",
                        "Address": "2236 US-130, Dayton, NJ 08810",
                        "Service": "Janitorial Services",
                        "Contract": "ACCESS NJ"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.494889,
                          40.372306
                        ],
                        "type": "Point"
                      },
                      "id": "6fe180e22a02d2f5f81969015c7918ba"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Union Central LO ",
                        "Address": "65 Jackson drive suite 300, Cranford NJ",
                        "Service": "",
                        "Contract": "ACCESS NJ"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.28247,
                          40.64704
                        ],
                        "type": "Point"
                      },
                      "id": "7195e50be7b59ecae506d0fda3a06d41"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Five Below GA",
                        "Address": "270 logistics center parkway, Juliette, GA 31046",
                        "Service": "Janitorial Services",
                        "Contract": "Commercial"
                      },
                      "geometry": {
                        "coordinates": [
                          -83.848038,
                          32.988406
                        ],
                        "type": "Point"
                      },
                      "id": "763cc5ae71757d0869181823307bc26a"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "NYS Department of Labor",
                        "Address": "75 Varick St, NYC",
                        "Service": "Office Services: Messenger, mail sort, delivery",
                        "Contract": "NYSID"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.0064,
                          40.72328
                        ],
                        "type": "Point"
                      },
                      "id": "7793b247e596e458b2fe2395f6057d27"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "NYS Insurance Fund",
                        "Address": "44 S Broadway, White Plains, NY 10601",
                        "Service": "COVID Disinfecting Services",
                        "Contract": "NYSID"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.761575,
                          41.030852
                        ],
                        "type": "Point"
                      },
                      "id": "783d539a0f78c5135a65a14a804cd4f2"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "PATH (DHS)",
                        "Address": "E 151st St, Bronx, NY",
                        "Service": "Janitorial Services",
                        "Contract": "Wildcat"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.92388,
                          40.819256
                        ],
                        "type": "Point"
                      },
                      "id": "7c354aefffd52fbede3a227fcbf73075"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Walter Reed Army Institute Research (WRAIR)",
                        "Address": "503 Robert Grant Ave, Silver Spring, MD 20910",
                        "Service": "Janitorial Services",
                        "Contract": "MVLE"
                      },
                      "geometry": {
                        "coordinates": [
                          -77.052669,
                          39.005829
                        ],
                        "type": "Point"
                      },
                      "id": "7cd45e8adcd7faf86677cd25621d320c"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "NYC HRA Uptown: 132 West 125 Street",
                        "Address": "132 W 125th St, New York, NY 10027",
                        "Service": "Janitorial Services",
                        "Contract": "NYSID"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.94724,
                          40.808261
                        ],
                        "type": "Point"
                      },
                      "id": "7da8893def4f9ee3244f7582e5153606"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "IRS",
                        "Address": "625 Fulton St, Brooklyn, NY 11201",
                        "Service": "Mailroom",
                        "Contract": "Source America"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.980031,
                          40.688694
                        ],
                        "type": "Point"
                      },
                      "id": "7ed1af8ca9109b7bd9daae0a0c7eb418"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Corporate Services/ ReServe/ InSynergy",
                        "Address": "633 3rd Avenue  6th Floor, NY, NY 10017",
                        "Service": "Corporate Support",
                        "Contract": "Fedcap NY"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.974782,
                          40.749712
                        ],
                        "type": "Point"
                      },
                      "id": "7f024b14accc49c0a48c7ae5ffb35b34"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "MLK Federal Building and Courthouse",
                        "Address": "50 Walnut St #4015, Newark, NJ 07102",
                        "Service": "anitorial Services/ Mech Maintenance",
                        "Contract": "Source America"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.172373,
                          40.729763
                        ],
                        "type": "Point"
                      },
                      "id": "7f6ae477fe9152094dcf8bc042801631"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "New Edge (Fox Run)",
                        "Address": " 2540 Wrangle Hill Rd, Bear, DE 19701",
                        "Service": "Janitorial Services",
                        "Contract": "Delaware"
                      },
                      "geometry": {
                        "coordinates": [
                          -75.713805,
                          39.603956
                        ],
                        "type": "Point"
                      },
                      "id": "7f8ff9350bbd79a33b271919aeb64e80"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "MG Donohue Building Management UNICOR (Federal Prison Industries) )",
                        "Address": "FPI Central Office, Washington DC",
                        "Service": "Janitorial Services",
                        "Contract": "Commercial"
                      },
                      "geometry": {
                        "coordinates": [
                          -77.01259,
                          38.895062
                        ],
                        "type": "Point"
                      },
                      "id": "7fb7b0affc290faf3a4cf7ac9f24d08a"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "FAA LGA Tower",
                        "Address": "LGA Airport",
                        "Service": "Janitorial Services",
                        "Contract": "Source America"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.873965,
                          40.776927
                        ],
                        "type": "Point"
                      },
                      "id": "804182933234335dfea70ae47850da3a"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Flatlands (DHS)",
                        "Address": "108-75 Avenue D, Brooklyn, NY 11236",
                        "Service": "Janitorial Services",
                        "Contract": "Wildcat"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.899387,
                          40.656476
                        ],
                        "type": "Point"
                      },
                      "id": "805aa61c67dbda455ad24391576fb833"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Safe Harbor Recovery Center - a program of Granite Pathways",
                        "Address": "865 Islington St, Portsmouth, NH 03801",
                        "Service": "Behavioral Health Services, Vocactional Rehabilitation",
                        "Contract": ""
                      },
                      "geometry": {
                        "coordinates": [
                          -70.774054,
                          43.068242
                        ],
                        "type": "Point"
                      },
                      "id": "81c54eebec076753f97ed106e8430ff6"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "290 Broadway",
                        "Address": "290 Broadway, New York, NY 10007",
                        "Service": "Janitorial Services",
                        "Contract": "Source America"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.005182,
                          40.714739
                        ],
                        "type": "Point"
                      },
                      "id": "861a9d0a519914c75cf3dfa101c69b51"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": " Bass River Municipal Building",
                        "Address": "3 North Maple Avenue, New Gretna, Bass River Township, NJ 08224",
                        "Service": "Janitorial Services",
                        "Contract": "ACCESS NJ"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.45153,
                          39.592847
                        ],
                        "type": "Point"
                      },
                      "id": "86f072427020b2fca1c4110cfdf850df"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "DOC Probation and Parole (Cherry Lane)",
                        "Address": "314 Cherry Ln, New Castle, DE 19720",
                        "Service": "Janitorial Services",
                        "Contract": "Delaware"
                      },
                      "geometry": {
                        "coordinates": [
                          -75.545336,
                          39.689725
                        ],
                        "type": "Point"
                      },
                      "id": "879e6e15eb9c1057dedb89258d5903a2"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Regal Court Business Centre",
                        "Address": "Regal Court Business Centre, 42-44 High St, Slough SL1 1EL, UK",
                        "Service": "Behavioral Health Services, Vocactional Rehabilitation",
                        "Contract": "Fedcap UK"
                      },
                      "geometry": {
                        "coordinates": [
                          -0.597544,
                          51.509917
                        ],
                        "type": "Point"
                      },
                      "id": "8918366caddec758a5f391ebb9dc7604"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Employment for TANF Participants",
                        "Address": "801 E Main St, Richmond, VA 23219",
                        "Service": "Supported Employment",
                        "Contract": "MVLE"
                      },
                      "geometry": {
                        "coordinates": [
                          -77.437235,
                          37.53847
                        ],
                        "type": "Point"
                      },
                      "id": "8aee7dd2529e8bb75bc9fcc841b9238b"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Townsend Building",
                        "Address": " 401 Federal Street Dover, DE 19901",
                        "Service": "Janitorial Services",
                        "Contract": "Delaware"
                      },
                      "geometry": {
                        "coordinates": [
                          -75.522119,
                          39.157963
                        ],
                        "type": "Point"
                      },
                      "id": "8b8000e9ca25b062179caead1b6e55f9"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "NYC HRA - 14th St",
                        "Address": "8 W 14th St, New York, NY 10011",
                        "Service": "Janitorial Services",
                        "Contract": "NYSID"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.994673,
                          40.735943
                        ],
                        "type": "Point"
                      },
                      "id": "8d279e0e14e6e57dd04b0d25a97e5160"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Adam Clayton Powell Jr. State Office Building",
                        "Address": "163 W 125th St, New York, NY 10027",
                        "Service": "Janitorial Services",
                        "Contract": "NYSID"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.947325,
                          40.809158
                        ],
                        "type": "Point"
                      },
                      "id": "8d62dbc475d1bc67abebbeb9895fdab8"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "NYC OATH, Department of Financce, Queens Service Site",
                        "Address": "Gertz Plaza Building, 92-31 Union Hall Street. Jamaica, NY 11443",
                        "Service": " Data Entry,  Data Imaging, Scanning & Keying, Document Management",
                        "Contract": "Commercial"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.797068,
                          40.703177
                        ],
                        "type": "Point"
                      },
                      "id": "8d81875c32629a3cd3784dd9dea4c72a"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Vocational Rehabilitation",
                        "Address": "210 East 43rd Street, New York, NY 10017",
                        "Service": "Vocational Rehabilitation",
                        "Contract": "Fedcap NY"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.973312,
                          40.751039
                        ],
                        "type": "Point"
                      },
                      "id": "8d9cf279d7675075e826a9d2e0fec4c6"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "J.P. Court #4",
                        "Address": "408 Stein Hwy, Seaford, DE 19973",
                        "Service": "Janitorial Services",
                        "Contract": "Delaware"
                      },
                      "geometry": {
                        "coordinates": [
                          -75.613693,
                          38.647469
                        ],
                        "type": "Point"
                      },
                      "id": "8efc0b9dd4b7243386a605cfe7a2bef5"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Asbury Park Office Building",
                        "Address": "630 Bangs Ave, Asbury Park, NJ ",
                        "Service": "Janitorial Services",
                        "Contract": "ACCESS NJ"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.010639,
                          40.216866
                        ],
                        "type": "Point"
                      },
                      "id": "921f339a240c32ff65d7d09d37130794"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Berkshire - Reading - 95 London St",
                        "Address": "95 London St, Reading RG1 4QA, UK",
                        "Service": "Behavioral Health Services, Vocactional Rehabilitation",
                        "Contract": "Fedcap UK"
                      },
                      "geometry": {
                        "coordinates": [
                          -0.967375,
                          51.451272
                        ],
                        "type": "Point"
                      },
                      "id": "923232d77014ea4ef4d89a9b5e4de056"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "FAA TRACON Janitorial & Landscaping",
                        "Address": "1515 Stewart Ave,\nWestbury, NY 11590",
                        "Service": "Janitorial Services, Grounds Maintenance",
                        "Contract": "Source America"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.587224,
                          40.73801
                        ],
                        "type": "Point"
                      },
                      "id": "9527ffb211d348ab1f5427fa5d8eb9ce"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Atlantic County Animal Shelter",
                        "Address": "240 OLD TURNPIKE RD PLEASANTVILLE NJ 08232",
                        "Service": "Janitorial Services",
                        "Contract": "ACCESS NJ"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.519992,
                          39.392675
                        ],
                        "type": "Point"
                      },
                      "id": "959c7da03500517e270b1ed26e1aa0b3"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Liberty State Park",
                        "Address": "200 Morris Pesin Dr, Jersey City, NJ 07305",
                        "Service": "Janitorial Services",
                        "Contract": "Source America"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.050345,
                          40.703998
                        ],
                        "type": "Point"
                      },
                      "id": "96341b98f2e74d4726b825bdf085c3b2"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Brooklyn Center",
                        "Address": "25 Elm Place, Brooklyn, NY 11201",
                        "Service": "Clinic Support Services",
                        "Contract": "Fedcap WeCare"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.984028,
                          40.68915
                        ],
                        "type": "Point"
                      },
                      "id": "96a7d9304a1a54b5d856fb75d8332a8f"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Justice of Peace 10&12",
                        "Address": "212 Greenbank Rd, Wilmington, DE 19808",
                        "Service": "Janitorial Services",
                        "Contract": "Delaware"
                      },
                      "geometry": {
                        "coordinates": [
                          -75.628423,
                          39.738883
                        ],
                        "type": "Point"
                      },
                      "id": "973f14532e8d29ba7e0d1d599f3c8f58"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Princeton Pike DCF ",
                        "Address": "3131 Princeton Pike, Lawrence Township NJ 08648",
                        "Service": "Janitorial Services",
                        "Contract": "ACCESS NJ"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.71617,
                          40.283107
                        ],
                        "type": "Point"
                      },
                      "id": "990f5d359a1b3dd388cfd50205ca8ac2"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Source America HQ",
                        "Address": " 8401 Old Courthouse Road Vienna, VA",
                        "Service": "Janitorial Services",
                        "Contract": "MVLE"
                      },
                      "geometry": {
                        "coordinates": [
                          -77.235755,
                          38.914845
                        ],
                        "type": "Point"
                      },
                      "id": "9976b42d65393f81ad0553439c70b00b"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "*Potential July1st start* Cranford DCF",
                        "Address": "65 Jackson Drive Suite 300 Cranford, NJ 07016",
                        "Service": "Janitorial Services",
                        "Contract": "ACCESS NJ"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.283704,
                          40.648004
                        ],
                        "type": "Point"
                      },
                      "id": "9a803bf563c1debfb986dee5194c9076"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Fedcap Delaware Office",
                        "Address": "241 Old Churchmans Rd, New Castle, DE 19720",
                        "Service": "Regional Office",
                        "Contract": "Fedcap US"
                      },
                      "geometry": {
                        "coordinates": [
                          -75.628205,
                          39.681827
                        ],
                        "type": "Point"
                      },
                      "id": "9ad29085cab9709cb007c1bd6f542e3e"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Deptcor",
                        "Address": "163 N Olden Ave. Trenton, NJ",
                        "Service": "Janitorial Services",
                        "Contract": "ACCESS NJ"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.741944,
                          40.228797
                        ],
                        "type": "Point"
                      },
                      "id": "9b194462dd27094f38977558a060b66f"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "NYS DOH EMS",
                        "Address": "433 River St, Troy, NY 12180",
                        "Service": "Office Services - Data Entry",
                        "Contract": "NYSID"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.686919,
                          42.737901
                        ],
                        "type": "Point"
                      },
                      "id": "9b326acb7a543f2c7dabc1037f1fb054"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Atlantic County Facility Mgmt",
                        "Address": "1333 ATLANTIC AVE, ATLANTIC CITY NJ 08401",
                        "Service": "Janitorial Services",
                        "Contract": "ACCESS NJ"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.427336,
                          39.362569
                        ],
                        "type": "Point"
                      },
                      "id": "9bf6f9889911d4368756e308cd9e46cc"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Piscataway DCF ",
                        "Address": "53 Knightsbridge Rd, Piscataway, NJ 08854",
                        "Service": "Janitorial Services",
                        "Contract": "ACCESS NJ"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.477512,
                          40.54775
                        ],
                        "type": "Point"
                      },
                      "id": "9ec77e8a0284d02eba90dfb40d6e1cc1"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Defense Acquisition University",
                        "Address": "9820 Belvoir Rd #5565, Fort Belvoir, VA 22060",
                        "Service": "Janitorial Services",
                        "Contract": "MVLE"
                      },
                      "geometry": {
                        "coordinates": [
                          -77.136696,
                          38.696423
                        ],
                        "type": "Point"
                      },
                      "id": "a10d7e629977040f109985852d144744"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Queens Medical Site",
                        "Address": "89-56 162nd Street, Jamaica, NY 11432",
                        "Service": "Medical Clinic",
                        "Contract": "Fedcap WeCare"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.79839,
                          40.705073
                        ],
                        "type": "Point"
                      },
                      "id": "a19120d60283f4dde9660b0d1efa9933"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "225 Cadman Plaza",
                        "Address": "225 Cadman Plaza E, Brooklyn, NY 11201",
                        "Service": "Janitorial Services & COVID-19 Disinfecting Services",
                        "Contract": "Source America"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.989343,
                          40.696772
                        ],
                        "type": "Point"
                      },
                      "id": "a21b4a07255a5453e9f57673e7a38e4c"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "GSA NJ COVID-19",
                        "Address": "GSA NJ Consolidated",
                        "Service": "Janitorial Services",
                        "Contract": "Source America"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.359953,
                          40.512437
                        ],
                        "type": "Point"
                      },
                      "id": "a30fb67142fe91e755e9a21115424b59"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "NYC Dept of Correction: Training Academy",
                        "Address": "66-26 Metropolitan Ave Middle Village, NY 11379",
                        "Service": "Janitorial Services",
                        "Contract": "NYSID"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.89077,
                          40.71117
                        ],
                        "type": "Point"
                      },
                      "id": "a3b7ae2a4a2017d2982683b778476fe6"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Five Below TX",
                        "Address": "950 conroe park west drive, Conroe, TX 77303",
                        "Service": "Janitorial Services",
                        "Contract": "Commercial"
                      },
                      "geometry": {
                        "coordinates": [
                          -95.455403,
                          30.373029
                        ],
                        "type": "Point"
                      },
                      "id": "a4cf417aef6dad409ce048e86de9d92b"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "DHSS Division of Substance Abuse and Mental Health (Fernhook)",
                        "Address": "1901 Dupont Hwy. New Castle, DE 19720",
                        "Service": "Janitorial Services",
                        "Contract": "Delaware"
                      },
                      "geometry": {
                        "coordinates": [
                          -75.576291,
                          39.700676
                        ],
                        "type": "Point"
                      },
                      "id": "a5887cfc063c212de7304433c4afba9e"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "ICE Courier",
                        "Address": "26 Federal Plaza, New York, NY 10278",
                        "Service": "Courier Services ",
                        "Contract": "Source America"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.195704,
                          40.75961
                        ],
                        "type": "Point"
                      },
                      "id": "a8ca4f1bf55cc5be26efc7a1dc22dcb3"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "NYC FDNY Ft Totten",
                        "Address": "418 Weaver Ave Bldg 336 & 415 Bayside, NY 11359",
                        "Service": "Janitorial Services",
                        "Contract": "NYSID"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.775812,
                          40.793402
                        ],
                        "type": "Point"
                      },
                      "id": "a94845b7b28d8486c77af2fc7487fb6d"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Woodside Center",
                        "Address": "941 Walnut Shade Rd, Dover, DE 19901",
                        "Service": "Janitorial Services",
                        "Contract": "Delaware"
                      },
                      "geometry": {
                        "coordinates": [
                          -75.544319,
                          39.0709
                        ],
                        "type": "Point"
                      },
                      "id": "ab5134b384b14b3fc802dff784c08512"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Atlantic County Facility Mgmt",
                        "Address": "1201 BACARACH BLVD ATLANTIC CITY NJ 08401 ",
                        "Service": "Janitorial Services",
                        "Contract": "CWS"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.451082,
                          39.377297
                        ],
                        "type": "Point"
                      },
                      "id": "adbe45edfca1e1b4321608b3e2c2df7c"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Hagerstown Goodwill-Fort Detrick Garrison",
                        "Address": "151 N Burhans Blvd #4638, Hagerstown, MD 21740",
                        "Service": "Janitorial Services",
                        "Contract": "MVLE"
                      },
                      "geometry": {
                        "coordinates": [
                          -77.725491,
                          39.647429
                        ],
                        "type": "Point"
                      },
                      "id": "aee3387c786a096a4c34147c40e5ec5e"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "PAX River",
                        "Address": " 47123 Buse Rd #540, Patuxent River, MD 20670",
                        "Service": "Janitorial Services",
                        "Contract": "MVLE"
                      },
                      "geometry": {
                        "coordinates": [
                          -76.432219,
                          38.272133
                        ],
                        "type": "Point"
                      },
                      "id": "af1cd77df826ac2a0a94926e71841cbf"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Congresswoman Yvette Clark",
                        "Address": "222 Lenox Rd Suite 1, Brooklyn, NY 11226",
                        "Service": "Janitorial Services",
                        "Contract": "Commercial"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.951677,
                          40.653588
                        ],
                        "type": "Point"
                      },
                      "id": "af9d94d2056ca36198b82effb7113791"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "NYC Dept of Correction: Health Mgmt Division",
                        "Address": "59-17 Junction Blvd Queens, NY 11373",
                        "Service": "Janitorial Services",
                        "Contract": "NYSID"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.86436,
                          40.73475
                        ],
                        "type": "Point"
                      },
                      "id": "b134753690aa98033ed0cf07d60d6a8c"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Biggs DTI",
                        "Address": "1901 N. DuPont Hwy, New Castle, DE 19720",
                        "Service": "Janitorial Services",
                        "Contract": "Delaware"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.988127,
                          40.750086
                        ],
                        "type": "Point"
                      },
                      "id": "b184da41574de9914319e671665a4f13"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "NYC HRA Uptown:: 530 West 135 Street",
                        "Address": "530 W 135th St, New York, NY 10031",
                        "Service": "Janitorial Services",
                        "Contract": "NYSID"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.954306,
                          40.819575
                        ],
                        "type": "Point"
                      },
                      "id": "b6bf17b23c1f77de49589940fa9e687f"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Del DOT North District Headquarters",
                        "Address": " 39 East Regal Blvd, Newark, DE",
                        "Service": "Janitorial Services",
                        "Contract": "Delaware"
                      },
                      "geometry": {
                        "coordinates": [
                          -75.690669,
                          39.669951
                        ],
                        "type": "Point"
                      },
                      "id": "b6ef01191abbf92a744b26bdf72962bd"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Humphreys Engineering Center",
                        "Address": "7701 Telegraph Rd, Alexandria, VA 22315",
                        "Service": "Janitorial Services",
                        "Contract": "MVLE"
                      },
                      "geometry": {
                        "coordinates": [
                          -77.141962,
                          38.74276
                        ],
                        "type": "Point"
                      },
                      "id": "b72e2011eeeb1b325b2f1a8ae85f2154"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Warriors in Transition Unit (WTU)",
                        "Address": "9500 Pohick Rd, Fort Belvoir, VA 22060",
                        "Service": "Janitorial Services",
                        "Contract": "MVLE"
                      },
                      "geometry": {
                        "coordinates": [
                          -77.145074,
                          38.702024
                        ],
                        "type": "Point"
                      },
                      "id": "b9dd7a12375c2420aa6d199e944d9761"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "River View 100 & 200",
                        "Address": "100 Riverview Plaza, Trenton NJ 08625",
                        "Service": "Janitorial Services",
                        "Contract": "ACCESS NJ"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.76194,
                          40.2045
                        ],
                        "type": "Point"
                      },
                      "id": "b9df1bed4a5620a64ac671e9c9b278c1"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Arlington CSB , Alexandria CSB, Loudoun County",
                        "Address": "8221 Willow Oaks Corporate Dr, Fairfax, VA 22031",
                        "Service": "Supported Employment",
                        "Contract": "MVLE"
                      },
                      "geometry": {
                        "coordinates": [
                          -77.233959,
                          38.863724
                        ],
                        "type": "Point"
                      },
                      "id": "b9f64eb4bc1a7121adb9f2989425f0c7"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Barbara Klienmen (DHS)",
                        "Address": "300 Skillman Ave, Brooklyn, NY 11211",
                        "Service": "Janitorial Services",
                        "Contract": "Wildcat"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.938413,
                          40.71653
                        ],
                        "type": "Point"
                      },
                      "id": "be36ce1c6aab3d0f5b0c77d9eb6d3cdb"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "US Mission",
                        "Address": "799 United Nations Plaza, New York, NY 10017",
                        "Service": "Janitorial Services",
                        "Contract": "Source America"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.96893,
                          40.750686
                        ],
                        "type": "Point"
                      },
                      "id": "be967b27d5355c6be0b7084ecfb1c618"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "DelDOT Kiamensi ",
                        "Address": "822 Kiamensi Road, Wilmington, DE 19804",
                        "Service": "Janitorial Services",
                        "Contract": "Delaware"
                      },
                      "geometry": {
                        "coordinates": [
                          -75.63301,
                          39.72468
                        ],
                        "type": "Point"
                      },
                      "id": "becd304c932e0f84717f675a951fb76c"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "FAA Essex Cauldwell Air Traffic Control Tower",
                        "Address": "27 Wright Way Building M, Fairfield, NJ 07004",
                        "Service": "Janitorial Services",
                        "Contract": "Source America"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.279844,
                          40.873467
                        ],
                        "type": "Point"
                      },
                      "id": "bf5479c05f8380de0e78d2cb54e41cdc"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "NYC OCME",
                        "Address": "81 39th St, Brooklyn, NY 11232",
                        "Service": "COVID Disinfecting Services",
                        "Contract": "NYSID"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.012546,
                          40.656958
                        ],
                        "type": "Point"
                      },
                      "id": "bfab9118e4d1bdc1c54ce5148b44de08"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Fedcap Mid-Atlantic Office (Education, RFM, ReServe)",
                        "Address": "300 New Jersey Avenue, NW, 9th Floor, Washington, D.C. 20001",
                        "Service": "Regional Office",
                        "Contract": "Fedcap US"
                      },
                      "geometry": {
                        "coordinates": [
                          -77.010988,
                          38.894449
                        ],
                        "type": "Point"
                      },
                      "id": "bff4c2bab8d21a8ee2255442ff37a609"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "NJSP Museum & Log Cabin",
                        "Address": "1020 River Rd, Ewing, NJ 08628",
                        "Service": "Janitorial Services",
                        "Contract": "ACCESS NJ"
                      },
                      "geometry": {
                        "coordinates": [
                          -75.02453,
                          39.239308
                        ],
                        "type": "Point"
                      },
                      "id": "c45a54f491a1b21695ab019db860ce81"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "JP Court #6",
                        "Address": "35 Cams Fortune Way, Harrington, DE 19954",
                        "Service": "Janitorial Services",
                        "Contract": "Delaware"
                      },
                      "geometry": {
                        "coordinates": [
                          -75.511496,
                          38.928028
                        ],
                        "type": "Point"
                      },
                      "id": "c49601136efffc83b8031a32caa3f18f"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "NJ State Troopers Museum & Welcome Center",
                        "Address": "1040 River Rd., Ewing Township NJ 08628",
                        "Service": "Janitorial Services",
                        "Contract": "ACCESS NJ"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.8511,
                          40.27073
                        ],
                        "type": "Point"
                      },
                      "id": "caf0a1400b45f3eacd3e596a1ac56ef8"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Catherine st. (DHS)",
                        "Address": "78 Catherine St, New York, NY 10038",
                        "Service": "Janitorial Services",
                        "Contract": "Wildcat"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.997508,
                          40.710603
                        ],
                        "type": "Point"
                      },
                      "id": "cbc3633195306eca49066f1aafe66321"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Venture House (Berkshire - Bracknell)",
                        "Address": "Venture House, 2 Arlington Square, Bracknell RG12 1WA, UK",
                        "Service": "Behavioral Health Services, Vocactional Rehabilitation",
                        "Contract": "Fedcap UK"
                      },
                      "geometry": {
                        "coordinates": [
                          -0.757708,
                          51.41532
                        ],
                        "type": "Point"
                      },
                      "id": "cc017b54f5bf5e474846684792be1b6b"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "New Castle Fire Marshall",
                        "Address": "2307 MacArthur Drive, New Castle, DE 19720",
                        "Service": "Janitorial Services",
                        "Contract": "Delaware"
                      },
                      "geometry": {
                        "coordinates": [
                          -75.615443,
                          39.690509
                        ],
                        "type": "Point"
                      },
                      "id": "cd5a40eef4e353e7c18ab68474054bfe"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Haslet Armory",
                        "Address": "122 William Penn Dover, DE 19901",
                        "Service": "Janitorial Services",
                        "Contract": "Delaware"
                      },
                      "geometry": {
                        "coordinates": [
                          -75.520482,
                          39.156004
                        ],
                        "type": "Point"
                      },
                      "id": "cf475b826a7ebf3bbc1a30ca46ffb35c"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Port Authority NY/NJ",
                        "Address": "5 boroughs; Jersey City; Newark; Hoboken",
                        "Service": " Messenger Service",
                        "Contract": "NYSID"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.043143,
                          40.717754
                        ],
                        "type": "Point"
                      },
                      "id": "cfc8ca74596f8d9dea11cd8bde2f90f8"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "DelDOT Bear Christiana",
                        "Address": "250 Bear Christiana Rd, Bear, DE 19701",
                        "Service": "Janitorial Services",
                        "Contract": "Delaware"
                      },
                      "geometry": {
                        "coordinates": [
                          -75.658687,
                          39.656837
                        ],
                        "type": "Point"
                      },
                      "id": "d1abbf640b540f676ccd98f35eb6f063"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Del DOT North District Headquarters Floor Care",
                        "Address": "39 East Regal Blvd, Newark, DE",
                        "Service": "Janitorial Services",
                        "Contract": "Delaware"
                      },
                      "geometry": {
                        "coordinates": [
                          -75.690669,
                          39.669951
                        ],
                        "type": "Point"
                      },
                      "id": "d25b94ed5d6e9903f6ec5e1c14b25965"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Prospect House - ( Buckinghamshire - High Wycombe)",
                        "Address": "38 Crendon Street, High Wycombe, Buckinghamshire, HP13 6AL",
                        "Service": "Behavioral Health Services, Vocactional Rehabilitation",
                        "Contract": "Fedcap UK"
                      },
                      "geometry": {
                        "coordinates": [
                          -0.747054,
                          51.629326
                        ],
                        "type": "Point"
                      },
                      "id": "d2fd263619a8b9c400c5bfb96519d191"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Childrens Hospital (Chenega)",
                        "Address": "111 Michigan Ave NW, Washington, DC 20310",
                        "Service": "Janitorial Services",
                        "Contract": "MVLE"
                      },
                      "geometry": {
                        "coordinates": [
                          -77.014773,
                          38.926439
                        ],
                        "type": "Point"
                      },
                      "id": "d31fafd45c2ea33a17402b49a5ccc676"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "USCG Atlantic City Grounds Services @ FAA William J. Hughes Technical Center",
                        "Address": "Atlantic City International Airport, Egg Harbor Township, NJ 08405",
                        "Service": " Grounds Maintenance",
                        "Contract": "Source America"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.563254,
                          39.444308
                        ],
                        "type": "Point"
                      },
                      "id": "d712ef7020fc21129dcb54a167dfbd16"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Five Below AZ",
                        "Address": "2150 S. Miller Road Buckeye, AZ 85326",
                        "Service": "Janitorial Services",
                        "Contract": "Commercial"
                      },
                      "geometry": {
                        "coordinates": [
                          -112.590777,
                          33.355316
                        ],
                        "type": "Point"
                      },
                      "id": "d8e74a78b0b2d739d536f31edfe2dd1e"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "NYC Transit Authority",
                        "Address": "130 Livingston St, Brooklyn, NY 11201",
                        "Service": "Office Services: Messenger, mail sort, delivery",
                        "Contract": "NYSID"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.988544,
                          40.690291
                        ],
                        "type": "Point"
                      },
                      "id": "d91f1c5cff69177852d20360aa7632bf"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Emma Bowan Community Service Center",
                        "Address": "1727 Amsterdam Ave, New York, NY 10031",
                        "Service": "Janitorial Services",
                        "Contract": "CWS"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.946957,
                          40.82545
                        ],
                        "type": "Point"
                      },
                      "id": "dac5f5657affbe5e21767ccd58d7b8fd"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Justice of Peace 10&12",
                        "Address": "210 Greenbank Rd, Wilmington, DE 19808",
                        "Service": "Janitorial Services",
                        "Contract": "Delaware"
                      },
                      "geometry": {
                        "coordinates": [
                          -75.628423,
                          39.738883
                        ],
                        "type": "Point"
                      },
                      "id": "dc4eb283c457a4e580b58b387c2d0216"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Hunterdon LO #668",
                        "Address": "84 Park ave. first floor suite E-111, Flemington NJ",
                        "Service": "",
                        "Contract": "ACCESS NJ"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.86247,
                          40.51407
                        ],
                        "type": "Point"
                      },
                      "id": "dca418fdb97eda8f20d2015361c073f3"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Trenton Office Complex",
                        "Address": "225 East State Street, Trenton, NJ 08666\n",
                        "Service": "Janitorial Services",
                        "Contract": "ACCESS NJ"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.75908,
                          40.218715
                        ],
                        "type": "Point"
                      },
                      "id": "dfae59a4a0e9a325426fcb6d24b5ff06"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "EPA",
                        "Address": "290 Broadway, New York, NY 10007",
                        "Service": "Office Services: Mailroom, Admin Support",
                        "Contract": "Source America"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.005182,
                          40.714739
                        ],
                        "type": "Point"
                      },
                      "id": "e1e5c19354acba88f0359e6a51a1509b"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Fedcap Rehabilitation Services",
                        "Address": "1011 Washington Avenue, Bronx, NY",
                        "Service": "Behavioral Health Services",
                        "Contract": "Fedcap NY"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.909849,
                          40.826405
                        ],
                        "type": "Point"
                      },
                      "id": "e3c365b2afaecc72016b24cc33a8e67d"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Atlantic City Jail",
                        "Address": "5060 ATLANTIC AVE, MAYS LANDING NJ 08330",
                        "Service": "Janitorial Services",
                        "Contract": "ACCESS NJ"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.712373,
                          39.447802
                        ],
                        "type": "Point"
                      },
                      "id": "e8497725ba6a607e52e4390e7a51ca59"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Bronx Service Site",
                        "Address": "2432 Grand Concourse, Bronx, NY 10458",
                        "Service": "Clinic Support Services",
                        "Contract": "Fedcap WeCare"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.897781,
                          40.860621
                        ],
                        "type": "Point"
                      },
                      "id": "e8be2147462a0136d408c76cecca99c7"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Fort Belvoir 1809/1840",
                        "Address": " 800 Belvoir Road. Fort Belvoir, VA, United States. 22060.",
                        "Service": "Janitorial Services",
                        "Contract": "MVLE"
                      },
                      "geometry": {
                        "coordinates": [
                          -77.134205,
                          38.687957
                        ],
                        "type": "Point"
                      },
                      "id": "ea21e633ffcf3eeef921858fb8c17cb4"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Five Below NJ",
                        "Address": " 5 Gateway Boulevard Pedricktown, NJ 08067",
                        "Service": "Janitorial Services",
                        "Contract": "Commercial"
                      },
                      "geometry": {
                        "coordinates": [
                          -75.413314,
                          39.740436
                        ],
                        "type": "Point"
                      },
                      "id": "ebeb34e9c0aecbc59e0ecde6a3b0db54"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "55 Hanson",
                        "Address": "55 Hanson Pl, Brooklyn, NY 11217",
                        "Service": "Janitorial Services",
                        "Contract": "NYSID"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.975748,
                          40.685562
                        ],
                        "type": "Point"
                      },
                      "id": "ec551d1b7883971677086c2d8fc403a8"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "ReServe South Florida",
                        "Address": "700 N Kendall Dr #709, Miami, FL 33156",
                        "Service": "Senior Support, Employment Support, Social Services",
                        "Contract": "ReServe"
                      },
                      "geometry": {
                        "coordinates": [
                          -80.320496,
                          25.687523
                        ],
                        "type": "Point"
                      },
                      "id": "ec603f676b6f95ee23166da08be84bd7"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Ford House Building",
                        "Address": "2nd St SW & D St SW, Washington, DC 20515",
                        "Service": "Janitorial Services",
                        "Contract": "Source America"
                      },
                      "geometry": {
                        "coordinates": [
                          -77.013662,
                          38.885064
                        ],
                        "type": "Point"
                      },
                      "id": "ec62bf06de581d836fad36fbce2ee799"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "VA Newark",
                        "Address": "20 Washington Pl, Newark, NJ 07102",
                        "Service": "anitorial Services/ Mech Maintenance",
                        "Contract": "Source America"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.17048,
                          41.101045
                        ],
                        "type": "Point"
                      },
                      "id": "ef527e6b7eee1a6f4232554129b138d6"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "NYC HRA Uptown:: 165 East 126 Street",
                        "Address": "165 East 126th St, 165 E 126th StNew York, NY 10035",
                        "Service": "Janitorial Services",
                        "Contract": "NYSID"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.935819,
                          40.804798
                        ],
                        "type": "Point"
                      },
                      "id": "f46da6dc43fb0e7ee972cb7bf179f2c6"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "NJSP Port Norris",
                        "Address": "8861 Highland St, Port Norris NJ",
                        "Service": "Janitorial Services",
                        "Contract": "ACCESS NJ"
                      },
                      "geometry": {
                        "coordinates": [
                          -75.013667,
                          39.288958
                        ],
                        "type": "Point"
                      },
                      "id": "f6456073f77f7d056a8c192bb1c30633"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Robert A. Roe Federal Building",
                        "Address": "200 Federal Plaza, Paterson, NJ 07505",
                        "Service": "Janitorial Services",
                        "Contract": "Source America"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.168498,
                          40.914722
                        ],
                        "type": "Point"
                      },
                      "id": "f81ad41d3cd220156ac4f7b6cdee8a60"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "CWS - Boston",
                        "Address": "174 Portland St, Boston, MA 02114",
                        "Service": "Affiliate Organization",
                        "Contract": "CWS"
                      },
                      "geometry": {
                        "coordinates": [
                          -71.061785,
                          42.364134
                        ],
                        "type": "Point"
                      },
                      "id": "fae53ee43ea97917586079d27aedaf90"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Freehold Office Building",
                        "Address": "100 Daniels Way, Freehold, NJ",
                        "Service": "Janitorial Services",
                        "Contract": "ACCESS NJ"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.274728,
                          40.245441
                        ],
                        "type": "Point"
                      },
                      "id": "fed6dd720ae3a1e2f3b46684907c4d30"
                    }
                  ]
              }
            ;

stores.features.forEach(function (store, i) {
      store.properties.id_1 = i;
      });

map.on('load', function (e) {

  // map.addLayer({
  //   "id": "locations",
  //   "type": "circle",
  //   /* Add a GeoJSON source containing place coordinates and information. */
  //   "source": {
  //     "type": "geojson",
  //     "data": stores
  //   }
  // });
  map.addSource('places', {
    'type': 'geojson',
    'data': stores})
    .addLayer({
        'id': 'points',
        'type': 'circle',
        'source': 'places',
        'paint': {
            'circle-color': '#2c99a6',
            'circle-radius': 7,
            'circle-stroke-width': .5,
            'circle-stroke-color': '#838383'
        }
    });

buildLocationList(stores);
addMarkers();
});

function addMarkers() {
  stores.features.forEach(function (marker) {
    var el = document.createElement('div');
    el.id = 'marker-' + marker.properties.id_1;
    el.className = 'marker';

    new mapboxgl.Marker(el, { offset: [0, -23] })
      .setLngLat(marker.geometry.coordinates)
      .addTo(map);

    el.addEventListener('click', function (e) {
      flyToStore(marker);
      createPopUp(marker);
      var activeItem = document.getElementsByClassName('active');
      e.stopPropagation();
      if (activeItem[0]) {
          activeItem[0].classList.remove('active');
      }
      var listing = document.getElementById(
        'listing-' + marker.properties.id_1
      );
      listing.classList.add('active');
  });
});
}

function buildLocationList(data) {
    data.features.forEach(function (store, i) {
      var prop = store.properties;
      var listings = document.getElementById('listings');
      var listing = listings.appendChild(document.createElement('div'));
      listing.id = 'listing-' + prop.id_1;
      listing.className = 'item';

    var link = listing.appendChild(document.createElement('a'));
      link.href = '#';
      link.className = 'title';
      link.id = 'link-' + prop.id_1;
      link.innerHTML = prop.Address;

    var details = listing.appendChild(document.createElement('div'));
    details.innerHTML = prop.Contract;
    if (prop.Name) {
      details.innerHTML += ' &middot; ' + prop.Service;
      }

    link.addEventListener('click', function (e) {
      for (var i = 0; i < data.features.length; i++) {
          if (this.id === 'link-' + data.features[i].properties.id_1) {
                  var clickedListing = data.features[i];
                  flyToStore(clickedListing);
                  createPopUp(clickedListing);
                            }
                            }
        var activeItem = document.getElementsByClassName('active');
      if (activeItem[0])
        { activeItem[0].classList.remove('active'); }
        this.parentNode.classList.add('active');
        });


    })};

    function flyToStore(currentFeature) {
      map.flyTo({
        center: currentFeature.geometry.coordinates,
        zoom: 15
      });
      }


  function createPopUp(currentFeature) {
      var popUps = document.getElementsByClassName('mapboxgl-popup');
      if (popUps[0]) popUps[0].remove();
      var popup = new mapboxgl.Popup({ closeOnClick: true, closeButton:true })
          .setLngLat(currentFeature.geometry.coordinates)
          .setHTML('<p style="text-align:left;">'
          +'<b>' + currentFeature.properties.Name +':'+ '</b>' +'<br>' + '<em>' + currentFeature.properties.Address + '</em>' +'<p style="text-align:left;"><b>Services:</b>'+
          '<br>'+ currentFeature.properties.Service
          )
          .addTo(map)};



        // Create a popup, but don't add it to the map yet.
        var popup = new mapboxgl.Popup({
            closeButton: true,
            closeOnClick: false,
        });

        map.on('mousemove', 'points', function (e) {
            // Change the cursor style as a UI indicator.
            map.getCanvas().style.cursor = 'default';

            var coordinates = e.features[0].geometry.coordinates.slice();
            var Name = e.features[0].properties.Name;
            var Service = e.features[0].properties.Service;
            var Address = e.features[0].properties.Address;

            // Ensure that if the map is zoomed out such that multiple
            // copies of the feature are visible, the popup appears
            // over the copy being pointed to.
            while (Math.abs(e.lngLat.lng - coordinates[0]) > 180) {
                coordinates[0] += e.lngLat.lng > coordinates[0] ? 360 : -360;
            }

            // Populate the popup and set its coordinates
            // based on the feature found. Makes some shit idk even know if is legitimate code or sim sus.
            if (Name != null) {
              popup.setLngLat(coordinates).setHTML('<p style="text-align:left;">'
              +'<b>' + Name +':'+ '</b>' +'<br>' + '<em>' + Address + '</em>' +'<p style="text-align:left;"><b>Services:</b>'+
              '<br>'+ Service).addTo(map)}

           else{popup.setLngLat(coordinates).setHTML('There are multiple locations at this marker. <br> Please zoom in further for more information').addTo(map)

           }

           ;
        });

    map.on('mouseleave', 'points', function () {
                map.getCanvas().style.cursor = 'crosshair';
                popup.remove();
            });

    </script>
    </body>
    </html>

