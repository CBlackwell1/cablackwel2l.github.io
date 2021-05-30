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
        <h1>Our locations</h1>
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
                        "Name": "Childrens Hospital (Chenega)",
                        "Address": "111 Michigan Ave NW, Washington, DC 20310",
                        "Service": "Custodial",
                        "Contract": "MVLE"
                      },
                      "geometry": {
                        "coordinates": [
                          -77.014773,
                          38.926439
                        ],
                        "type": "Point"
                      },
                      "id": "000e1325462ee57a92128c4a96e507c4"
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
                      "id": "019a09824954f69f39191d4910d35885"
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
                      "id": "02b68dcaec17e32d51638e835239ba3e"
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
                      "id": "03624c86ea8aea635576bac6016b0f64"
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
                      "id": "037382dca99ec88d15cb77acb652a227"
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
                      "id": "0616d7ec532a6c38a3986159cb244a9f"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Atlantic County Facility Mgmt",
                        "Address": "101 SOUTH SHORE RD, NORTHFIELD NJ 08232",
                        "Service": "Supported Employment",
                        "Contract": "ACCESS NJ"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.536821,
                          39.377363
                        ],
                        "type": "Point"
                      },
                      "id": "08725647aea5a98c4696e7578459547b"
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
                      "id": "09c55679e72a349f2b523fd7108bcb31"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Christopher Brown Law Offices",
                        "Address": "3123 Atlantic Ave, Atlantic City, NJ 08401",
                        "Service": " Payroll Dept",
                        "Contract": "Commercial"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.449081,
                          39.35368
                        ],
                        "type": "Point"
                      },
                      "id": "09d3ddb47c3efba113f78d200e991fa4"
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
                      "id": "0a0c9171b5484250b0f6885af6f75616"
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
                      "id": "0aac3322bbc38424d4877cd99717af55"
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
                      "id": "0ad8c6f3a85eb1a92a59c782ba3064f1"
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
                      "id": "0d8c400f4eb95422650150ac44af99f2"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Alexandria Twp. Board of Education",
                        "Address": "Lester Wilson Elementary School 525 Rte. 513, Pittstown , NJ 08867",
                        "Service": "Supported Employment",
                        "Contract": "ACCESS NJ"
                      },
                      "geometry": {
                        "coordinates": [
                          -75.025673,
                          40.566918
                        ],
                        "type": "Point"
                      },
                      "id": "0e400aa9a775b62503e426872f7829d4"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Atlantic County Facility Mgmt",
                        "Address": "201 SOUTH SHORE RD, NORTHFIELD NJ 08232",
                        "Service": "Supported Employment",
                        "Contract": "ACCESS NJ"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.537534,
                          39.376787
                        ],
                        "type": "Point"
                      },
                      "id": "0ed1e5abbcd6ea63149ccee6b0da2635"
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
                      "id": "1086564cdeab62607a4aec4f2ca6e9d6"
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
                      "id": "11a21c1a1be9e8901ea4d69c936c3009"
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
                      "id": "11e4762dd35fc8e861984089ac8efbc5"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Asbury Park Office Building",
                        "Address": "630 Bangs Ave, Asbury Park, NJ ",
                        "Service": "Supported Employment",
                        "Contract": "ACCESS NJ"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.010639,
                          40.216865
                        ],
                        "type": "Point"
                      },
                      "id": "123ed780a7b87eb2a49bf0b3c89cf14b"
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
                      "id": "163c778ab37775b5bb0d8f1c791dec9a"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Atlantic County Facility Mgmt",
                        "Address": "2 SOUTH MAIN STREET, PLEASANTVILLE NJ 08232",
                        "Service": "Supported Employment",
                        "Contract": "ACCESS NJ"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.52241,
                          39.391713
                        ],
                        "type": "Point"
                      },
                      "id": "171966889390d6690e919029a399a885"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Atlantic County Facility Mgmt",
                        "Address": "1201 BACARACH BLVD ATLANTIC CITY NJ 08401 ",
                        "Service": "Supported Employment",
                        "Contract": "CWS"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.451082,
                          39.377297
                        ],
                        "type": "Point"
                      },
                      "id": "1742fff565b481200213cd6fd1dcd58e"
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
                      "id": "177377cde860490719e0569b1aa0eab3"
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
                      "id": "181d34eb783d3bb99b3849a3c79a8f2c"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Armory Men's shelter (DHS)",
                        "Address": "1322 Bedford Ave, Brooklyn, NY 11216",
                        "Service": "Rehabilitation, Clinical Support",
                        "Contract": "Wildcat"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.953727,
                          40.67839
                        ],
                        "type": "Point"
                      },
                      "id": "185226ea5b39e2341a1486c427d2a24c"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Five Below TX",
                        "Address": "950 conroe park west drive, Conroe, TX 77303",
                        "Service": "Supported Employment",
                        "Contract": "Commercial"
                      },
                      "geometry": {
                        "coordinates": [
                          -95.455403,
                          30.373029
                        ],
                        "type": "Point"
                      },
                      "id": "18d31cf9a4f81fb0d543d65124918922"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Emma Bowan Community Service Center",
                        "Address": "1727 Amsterdam Ave, New York, NY 10031",
                        "Service": "Rehabilitation, Clinical Support",
                        "Contract": "CWS"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.946957,
                          40.82545
                        ],
                        "type": "Point"
                      },
                      "id": "1a6abc46a4327c0110b75229e74993c9"
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
                      "id": "1aa113b694dc3fe8929cd304545bc604"
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
                      "id": "1caf5f11a68b3da42616ed4c1de0c2a4"
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
                      "id": "22625e9b43f3af014ae2bcbd17e6dd22"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "DelDOT Talley ",
                        "Address": "1300 Talley Road, Wilmington, DE 19803",
                        "Service": "Supported Employment",
                        "Contract": "Delaware"
                      },
                      "geometry": {
                        "coordinates": [
                          -75.52822,
                          39.77661
                        ],
                        "type": "Point"
                      },
                      "id": "22e78c097dd89ede472a7f5bff5e9a91"
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
                      "id": "25a7dbebce57e2965d976201b6afc777"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Five Below NJ",
                        "Address": " 5 Gateway Boulevard Pedricktown, NJ 08067",
                        "Service": "Supported Employment",
                        "Contract": "Commercial"
                      },
                      "geometry": {
                        "coordinates": [
                          -75.413314,
                          39.740436
                        ],
                        "type": "Point"
                      },
                      "id": "26577db573e56d7a5e095025ac3deda6"
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
                      "id": "27331d4a62b416355af29b7e156f11e0"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Warriors in Transition Unit (WTU)",
                        "Address": "9500 Pohick Rd, Fort Belvoir, VA 22060",
                        "Service": "Custodial",
                        "Contract": "MVLE"
                      },
                      "geometry": {
                        "coordinates": [
                          -77.145074,
                          38.702024
                        ],
                        "type": "Point"
                      },
                      "id": "281561e12f8b737a65ce403b0361cc58"
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
                      "id": "2a9cd584da6e78927c271d0b23b2dbe5"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Catherine st. (DHS)",
                        "Address": "78 Catherine St, New York, NY 10038",
                        "Service": "Rehabilitation, Clinical Support",
                        "Contract": "Wildcat"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.997508,
                          40.710603
                        ],
                        "type": "Point"
                      },
                      "id": "2bed3f33c7c9563cdd6e38362ef8b83f"
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
                      "id": "2d9b6211409dbfb43980c8838b32ad8a"
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
                      "id": "30df0fc2cb01e1c84d1036fdce5432ad"
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
                      "id": "31102caf8ececcef3c541763b17e786b"
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
                      "id": "33df82e6438adf788ca0b6249fe2883a"
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
                      "id": "34292cf13f0f2b9dc9adbe6b3d8a5827"
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
                      "id": "3503ee4565adbcc19fb7d334c6fb2268"
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
                      "id": "3599dd2e1837c0accd77e00b7a78f644"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Five Below GA",
                        "Address": "270 logistics center parkway, Juliette, GA 31046",
                        "Service": "Supported Employment",
                        "Contract": "Commercial"
                      },
                      "geometry": {
                        "coordinates": [
                          -83.848038,
                          32.988406
                        ],
                        "type": "Point"
                      },
                      "id": "36095f6b83e62bba58623930ecc6c295"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Flatlands (DHS)",
                        "Address": "108-75 Avenue D, Brooklyn, NY 11236",
                        "Service": "Rehabilitation, Clinical Support",
                        "Contract": "Wildcat"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.899387,
                          40.656476
                        ],
                        "type": "Point"
                      },
                      "id": "360c658bbe38d4aea5da9ac98bcb13dd"
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
                      "id": "379613d69d50cb261a83a1d4d593d82b"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Freehold Office Building",
                        "Address": "100 Daniels Way, Freehold, NJ",
                        "Service": "Supported Employment",
                        "Contract": "ACCESS NJ"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.274728,
                          40.245441
                        ],
                        "type": "Point"
                      },
                      "id": "3e2817b9412dacce725d543b1e49182c"
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
                      "id": "3f450366359b7ab02b95a33451724aac"
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
                      "id": "3f4db0fbefd63bd060ab465a3ee87792"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Public Archives Building ",
                        "Address": "121 MLK Jr. Blvd, N Dover, DE 19901",
                        "Service": "Supported Employment",
                        "Contract": "Delaware"
                      },
                      "geometry": {
                        "coordinates": [
                          -75.52037,
                          39.15844
                        ],
                        "type": "Point"
                      },
                      "id": "3f9befd20999436bdf97625fcda68b94"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Bureau of Land Management",
                        "Address": "20 M St SE, Washington, DC 20003",
                        "Service": "Custodial",
                        "Contract": "MVLE"
                      },
                      "geometry": {
                        "coordinates": [
                          -77.007955,
                          38.876707
                        ],
                        "type": "Point"
                      },
                      "id": "42d2b28a63abf2d09666b94782c875ef"
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
                      "id": "439e61ce85195485cb42dadd5719f52d"
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
                      "id": "457d6c247ba2efab17037ef972e00c74"
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
                      "id": "45b7e241600b30a262f8a3f3a79552e7"
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
                      "id": "45eef0dbecfa4660199fe1b0478c02e9"
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
                      "id": "45f04e54a5d490cf33caf4d64dd7b856"
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
                      "id": "4730732c57169c59a96ca4f0bfffa878"
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
                      "id": "49438a3a9a011dff0cb7265e586596c9"
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
                      "id": "499eb1bec10cd906633563fbcc22ce19"
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
                      "id": "49b039403e1968aae53f73b98a464373"
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
                      "id": "4dbe52584f61706bb68097e5a489693b"
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
                      "id": "4eb8ff6974ccb9ae91675ff092f23d3d"
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
                      "id": "4efea5e04063be777c442e8ed2bd84a8"
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
                      "id": "50d39b8ba4d89e9c46d08dc7899a0a87"
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
                      "id": "51477b51af1f06d5d928a509aa98b1cd"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Battery Park",
                        "Address": "Battery Park, Manhattan, New York, New York, United States of America",
                        "Service": "",
                        "Contract": "Source America"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.015824,
                          40.703011
                        ],
                        "type": "Point"
                      },
                      "id": "51e030150247aa8a8c0d3c66096239eb"
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
                      "id": "52b17fc80c3761a45b88f2b3004431c1"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Acacia (DHS)",
                        "Address": "148 W 124th St, New York, NY 10027",
                        "Service": "Rehabilitation, Clinical Support",
                        "Contract": "Wildcat"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.947991,
                          40.807653
                        ],
                        "type": "Point"
                      },
                      "id": "53c31d7d2e6f22edc112d93d51c472a3"
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
                      "id": "5c5e89f1c064e8d274687960977aee70"
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
                      "id": "5c873ab907b7086dad7fbe0076821fc0"
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
                      "id": "5db65b4550c229dc5ae2d9f79743ee7b"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Atlantic County Animal Shelter",
                        "Address": "240 OLD TURNPIKE RD PLEASANTVILLE NJ 08232",
                        "Service": "Supported Employment",
                        "Contract": "ACCESS NJ"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.519992,
                          39.392675
                        ],
                        "type": "Point"
                      },
                      "id": "6141e9779e5d98e908168d724f8fb904"
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
                      "id": "6203a3831979c1502d510f0c96be0288"
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
                      "id": "64347986a17e1ab6c153d4e8a5bc417f"
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
                      "id": "64d9d1068aa29980badec50e3f585e37"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "NJSP Museum & Log Cabin",
                        "Address": "1020 River Rd, Ewing, NJ 08628",
                        "Service": "Supported Employment",
                        "Contract": "ACCESS NJ"
                      },
                      "geometry": {
                        "coordinates": [
                          -75.02453,
                          39.239308
                        ],
                        "type": "Point"
                      },
                      "id": "67c1b1c8216c113c97a4c2d61f845667"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Bostetter Courthouse",
                        "Address": "200 S. Washington Street, Alexandria, VA",
                        "Service": " Custodial",
                        "Contract": "MVLE"
                      },
                      "geometry": {
                        "coordinates": [
                          -77.046641,
                          38.803617
                        ],
                        "type": "Point"
                      },
                      "id": "67db261ea1581316dea84732204f9989"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Humphreys Engineering Center",
                        "Address": "7701 Telegraph Rd, Alexandria, VA 22315",
                        "Service": "Custodial",
                        "Contract": "MVLE"
                      },
                      "geometry": {
                        "coordinates": [
                          -77.141962,
                          38.74276
                        ],
                        "type": "Point"
                      },
                      "id": "69558843efae6d95e351cc796b07f5c5"
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
                      "id": "6960df1418d13b8d20cb3e8500e7fa15"
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
                      "id": "6a3101b0e94d894c7bb9d9cc6815257b"
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
                      "id": "6a9a7570f312a23387ba5748bb437210"
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
                      "id": "6c2746c7683fcdce59279ce4627eb87a"
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
                      "id": "6c3958690f36d354e2db8a522605c810"
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
                      "id": "6ecac688bf9fe61400c84f971a381cd9"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Atlantic County Facility Mgmt",
                        "Address": "1333 ATLANTIC AVE, ATLANTIC CITY NJ 08401",
                        "Service": "Supported Employment",
                        "Contract": "ACCESS NJ"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.427335,
                          39.362569
                        ],
                        "type": "Point"
                      },
                      "id": "6f464d1cd9038f1c4416eafb7dce71f0"
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
                      "id": "6f553a86aa3b198cc6d0b67586cc3ef9"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Five Below AZ",
                        "Address": "2150 S. Miller Road Buckeye, AZ 85326",
                        "Service": "Supported Employment",
                        "Contract": "Commercial"
                      },
                      "geometry": {
                        "coordinates": [
                          -112.590777,
                          33.355316
                        ],
                        "type": "Point"
                      },
                      "id": "7232d35bde4ecfabfc3d82696fc5bf08"
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
                      "id": "72834c11993f15d79b5fec9b06aa7a3c"
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
                      "id": "73c74cd11c3180deef5eb55c4bdc793f"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Trenton Office Complex",
                        "Address": "225 East State Street, Trenton, NJ 08666\n",
                        "Service": "Supported Employment",
                        "Contract": "ACCESS NJ"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.75908,
                          40.218714
                        ],
                        "type": "Point"
                      },
                      "id": "7456b0a851a91621cbe89e116efc60eb"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Atlantic County Facility Mgmt",
                        "Address": "235 DOLPHIN AVE, NORTHFIELD NJ 08232",
                        "Service": "Supported Employment",
                        "Contract": "ACCESS NJ"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.543997,
                          39.379538
                        ],
                        "type": "Point"
                      },
                      "id": "7492cd4098663895a74a0ad408be342f"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "NJSPB Eggerts Crossing is AKA NY NJ RFTF, Regional Fugitive Task Force\n",
                        "Address": "141 Eggert's Crossing Rd, Lawrenceville, NJ 08648",
                        "Service": "Supported Employment",
                        "Contract": "ACCESS NJ"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.743236,
                          40.27229
                        ],
                        "type": "Point"
                      },
                      "id": "79e6a413c7f4f151264da6586dd0d7ef"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Wilburtha NJSP Welcome Center",
                        "Address": "1020 River Rd., Ewing, NJ 08628",
                        "Service": "Supported Employment",
                        "Contract": "ACCESS NJ"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.847201,
                          40.265604
                        ],
                        "type": "Point"
                      },
                      "id": "7bafa0c0ca401c418e7312e67341ed9f"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Linden (DHS)",
                        "Address": "501 New Lots Ave, Brooklyn, NY 11207",
                        "Service": "Rehabilitation, Clinical Support",
                        "Contract": "Wildcat"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.889478,
                          40.663639
                        ],
                        "type": "Point"
                      },
                      "id": "7f57f7ede89754b1b526df9e154e7248"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Jamaica (DHS)",
                        "Address": "175-10 88th Ave, Jamaica, NY 11432",
                        "Service": "Rehabilitation, Clinical Support",
                        "Contract": "Wildcat"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.786369,
                          40.711118
                        ],
                        "type": "Point"
                      },
                      "id": "83743d0763f7d8bdf543e5dfb666103f"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Deptcor",
                        "Address": "163 N Olden Ave. Trenton, NJ",
                        "Service": "Supported Employment",
                        "Contract": "ACCESS NJ"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.741944,
                          40.228797
                        ],
                        "type": "Point"
                      },
                      "id": "86da73226c44c0d7eaf89ad072bf820b"
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
                      "id": "876a920d9f6d9e7275f2eaef916d1727"
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
                      "id": "88521b936ee8666183d285b9dd3be258"
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
                      "id": "8895d773349800f5b0f3af23b39d1597"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Barbara Klienmen (DHS)",
                        "Address": "300 Skillman Ave, Brooklyn, NY 11211",
                        "Service": "Rehabilitation, Clinical Support",
                        "Contract": "Wildcat"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.938413,
                          40.71653
                        ],
                        "type": "Point"
                      },
                      "id": "8a91f1b1657c98a8dcc5c4e408ac8412"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Source America HQ",
                        "Address": " 8401 Old Courthouse Road Vienna, VA",
                        "Service": "Custodial",
                        "Contract": "MVLE"
                      },
                      "geometry": {
                        "coordinates": [
                          -77.235755,
                          38.914845
                        ],
                        "type": "Point"
                      },
                      "id": "8acf6dba159f23ff659bc10b695b8385"
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
                      "id": "8bdfeebf49571729686b00943ee0f73e"
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
                      "id": "8dfdc0d4b4c089ff2fa6010b02edc792"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Defense Acquisition University",
                        "Address": "9820 Belvoir Rd #5565, Fort Belvoir, VA 22060",
                        "Service": "Custodial",
                        "Contract": "MVLE"
                      },
                      "geometry": {
                        "coordinates": [
                          -77.136696,
                          38.696423
                        ],
                        "type": "Point"
                      },
                      "id": "8fc98bed8c99f8ca39ddc6147267376d"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "IRS",
                        "Address": "625 Fulton St, Brooklyn, NY 11201",
                        "Service": "Supported Employment, Document Management",
                        "Contract": "Source America"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.980031,
                          40.688694
                        ],
                        "type": "Point"
                      },
                      "id": "915e1037c795615cfcdbd26c46701580"
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
                      "id": "9270d3e10ff5a56b47f8e6d7e63d0796"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": " Bass River Municipal Building",
                        "Address": "3 North Maple Avenue, New Gretna, Bass River Township, NJ 08224",
                        "Service": "Supported Employment",
                        "Contract": "ACCESS NJ"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.451529,
                          39.592847
                        ],
                        "type": "Point"
                      },
                      "id": "9440ed93dcd1b358a9cef658c20006f9"
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
                      "id": "95cc9a010f3e5782ddfcbb51ed55a5ce"
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
                      "id": "97ac3578dd6075fdb6ddbd38bd5c8e2e"
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
                      "id": "99405826343ac893dce5ffa7785e9735"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Fort Belvoir 1809/1840",
                        "Address": " 800 Belvoir Road. Fort Belvoir, VA, United States. 22060.",
                        "Service": "Custodial",
                        "Contract": "MVLE"
                      },
                      "geometry": {
                        "coordinates": [
                          -77.134205,
                          38.687957
                        ],
                        "type": "Point"
                      },
                      "id": "9b98059839c40a6b74a26a1a764d0b6f"
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
                      "id": "9c4b6ad7aea1101f435926b7a3afb06f"
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
                      "id": "9f978bc024ad1965b9c048e1d07b54a5"
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
                      "id": "9fea8dfc2fdcd52d8665b40d17cc313c"
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
                      "id": "a1d399d0ed9210d1c63ce867e3b57f38"
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
                      "id": "a2f77158cd9611b12746a759baae1063"
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
                      "id": "a3953e5a917287dc392401cc86bdc0e2"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "PAX River",
                        "Address": " 47123 Buse Rd #540, Patuxent River, MD 20670",
                        "Service": " Custodial",
                        "Contract": "MVLE"
                      },
                      "geometry": {
                        "coordinates": [
                          -76.432219,
                          38.272133
                        ],
                        "type": "Point"
                      },
                      "id": "a4515ae0ae8a784ad9be57bfb044de49"
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
                      "id": "a4b7af11b25330486029063e2c4fa0cf"
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
                      "id": "a542bd9e3b916e7d42353934edf3ca81"
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
                      "id": "a783e7a8f7947f0ad3ed627cbf8e77b1"
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
                      "id": "a8451b8a422e00fa033c3043d6e049b6"
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
                      "id": "a8e8da0df48057d751fa68040535f437"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Atlantic County Drexel Ave M B",
                        "Address": "1227 DREXEL AVE, ATLANTIC CITY NJ 08401",
                        "Service": "Supported Employment",
                        "Contract": "ACCESS NJ"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.429438,
                          39.367432
                        ],
                        "type": "Point"
                      },
                      "id": "a9396af3da2d34e16588ecb4bb22a0c7"
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
                      "id": "acd461e3007961fd081298bd24922e92"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "NYC Transit Authority",
                        "Address": "1/2/3/4/5/6 Train Subway Station",
                        "Service": "COVID Disinfecting Services",
                        "Contract": "NYSID"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.95309,
                          40.810975
                        ],
                        "type": "Point"
                      },
                      "id": "adf7ab34ea3cd06274f557c480dc449e"
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
                      "id": "ae842d0218f6edfca5f578810a0579ea"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "National Museum of Health",
                        "Address": "2500 Linden Lane, Silver Spring, Maryland",
                        "Service": "Custodial",
                        "Contract": "MVLE"
                      },
                      "geometry": {
                        "coordinates": [
                          -77.053118,
                          39.008683
                        ],
                        "type": "Point"
                      },
                      "id": "af9e23c7b76c3f8138d1772fe51ce00e"
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
                      "id": "afd3176e0bf226500f4728ab06be66de"
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
                      "id": "b0a5ad81d4725f60b6a6d97a834234c1"
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
                      "id": "b1684ff926ea701a5e5487027473f138"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Bivalve - Ogdon Ave",
                        "Address": "2669 Ogdon Ave, Port Norris, NJ",
                        "Service": "Supported Employment",
                        "Contract": "ACCESS NJ"
                      },
                      "geometry": {
                        "coordinates": [
                          -75.02453,
                          39.239308
                        ],
                        "type": "Point"
                      },
                      "id": "b1cd30fdd403a9f50feb7ae0bfc09d60"
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
                      "id": "b207f70569b02724fb47ddd147a45950"
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
                      "id": "b4be99202a3f49f2c279bd6978931673"
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
                      "id": "b4e666168fedc23957c3bae26a9ede33"
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
                      "id": "b620896ebbb17e0555b04d02613a816c"
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
                      "id": "b684c479baf042c73d3a3f5c6163325e"
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
                      "id": "b7f7d6747275500148d05faa417af06a"
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
                      "id": "bb4d2bb5beec7f35ef0c34563ae93bd5"
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
                      "id": "bc783acbfd7d6208767f0f42077aec81"
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
                      "id": "be1f107fad60af38409d489131eb3c91"
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
                      "id": "bf9acb095234f7614864e9e6c66b6593"
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
                      "id": "c0ee45c507de10a3a094a67c60f4080d"
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
                      "id": "c28a008bfba49c507a8cbd091fdc9676"
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
                      "id": "c4872f2b8dd8fd819c3299c282fb74e9"
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
                      "id": "c68c112405e234c13de77638ac21d5de"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Auburn (DHS)",
                        "Address": "39 Auburn Pl, Brooklyn, NY 11205",
                        "Service": "Rehabilitation, Clinical Support",
                        "Contract": "Wildcat"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.976422,
                          40.69477
                        ],
                        "type": "Point"
                      },
                      "id": "c761cdef1a230c4a12ebaee6e1225578"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Bridgeton",
                        "Address": "1 Landis Ave Bridgeton, NJ",
                        "Service": "Supported Employment",
                        "Contract": "ACCESS NJ"
                      },
                      "geometry": {
                        "coordinates": [
                          -75.207314,
                          39.461313
                        ],
                        "type": "Point"
                      },
                      "id": "c7e70b7f1fde11723bb3128c900ca535"
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
                      "id": "c7eda226136138f2682e9bcd199dffd9"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "271 Cadman Plaza",
                        "Address": "271 Cadman Plaza E, Brooklyn, NY 11202",
                        "Service": "Nursing, GSA COVID-19 Screening, Mechanical & Elevator Maintenance",
                        "Contract": "Source America"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.989979,
                          40.695907
                        ],
                        "type": "Point"
                      },
                      "id": "c89e342ed6489ccb5c4830e1e0c65518"
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
                      "id": "caa9f484a297d204c0aa0135b0e955e6"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "NASA Headquarters",
                        "Address": "300 E St SW, Washington, DC 20546",
                        "Service": "Custodial",
                        "Contract": "MVLE"
                      },
                      "geometry": {
                        "coordinates": [
                          -77.016278,
                          38.883064
                        ],
                        "type": "Point"
                      },
                      "id": "cb0368c4d86a3282ea87f4cca007e9b2"
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
                      "id": "cb7701d04a8a931942d8bdadd9c29849"
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
                      "id": "cce73822870faf81aa07c347a7fdf62b"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Hagerstown Goodwill-Fort Detrick Garrison",
                        "Address": "151 N Burhans Blvd #4638, Hagerstown, MD 21740",
                        "Service": "Custodial",
                        "Contract": "MVLE"
                      },
                      "geometry": {
                        "coordinates": [
                          -77.725491,
                          39.647429
                        ],
                        "type": "Point"
                      },
                      "id": "cdec8cef869e8052ed388d8285601d7b"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Alexandria Middle School",
                        "Address": "557 Rte. 513, Pittstown , NJ 08867",
                        "Service": "Supported Employment",
                        "Contract": "ACCESS NJ"
                      },
                      "geometry": {
                        "coordinates": [
                          -75.015167,
                          40.570443
                        ],
                        "type": "Point"
                      },
                      "id": "ce9509743f1ac2dd95fc4e8bbd630f16"
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
                      "id": "ceb37febf13f102d0cdb865ec47228d6"
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
                      "id": "d0eb03e8bd2ab40225011927b10b3586"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Atlantic City Jail",
                        "Address": "5060 ATLANTIC AVE, MAYS LANDING NJ 08330",
                        "Service": "Supported Employment",
                        "Contract": "ACCESS NJ"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.712373,
                          39.447802
                        ],
                        "type": "Point"
                      },
                      "id": "d1fbc82bdb85cefee2bf8a7dd3bbb9bd"
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
                      "id": "d47bb9ea82db21c1f99b8b198cbfe73e"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "PATH (DHS)",
                        "Address": "E 151st St, Bronx, NY",
                        "Service": "Rehabilitation, Clinical Support",
                        "Contract": "Wildcat"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.92388,
                          40.819256
                        ],
                        "type": "Point"
                      },
                      "id": "d52c36075ad93c264d0b519d1b48c180"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "DelDOT Kiamensi ",
                        "Address": "822 Kiamensi Road, Wilmington, DE 19804",
                        "Service": "Supported Employment",
                        "Contract": "Delaware"
                      },
                      "geometry": {
                        "coordinates": [
                          -75.63301,
                          39.72468
                        ],
                        "type": "Point"
                      },
                      "id": "d7c8ae5d16a0daf51728d909a941b47e"
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
                      "id": "d839d5537377015d94eab34a51eadb29"
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
                      "id": "d8c74b3b119584c33ae383483ea86ee2"
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
                      "id": "d9d4542d6213a2823c800e4a7e472e4e"
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
                      "id": "e03e5f841af221ed560c9eaf6daa9b74"
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
                      "id": "e30e7c3ac64353881be5d1a10dd42802"
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
                      "id": "e3bd84342e8da06ad6ec45e2f9f43289"
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
                      "id": "e4b6f23a412bed8403a0dce07a2b52b3"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "NJ Training School for Boys-JJC",
                        "Address": "1 State Home Rd., Monroe Township, NJ 08831-0500",
                        "Service": "Supported Employment",
                        "Contract": "ACCESS NJ"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.420999,
                          40.341471
                        ],
                        "type": "Point"
                      },
                      "id": "e5698d03ced9fc605c1d60d697018e19"
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
                      "id": "e9d59b537779954116a3626f9ceb8f28"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Robert A. Roe Federal Building",
                        "Address": "200 Federal Plaza, Paterson, NJ 07505",
                        "Service": " Grounds Maintenance",
                        "Contract": "Source America"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.168498,
                          40.914722
                        ],
                        "type": "Point"
                      },
                      "id": "ebada993023fa18cf963780154ca362e"
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
                      "id": "ec68ff2ec53741b656f155d32cc67714"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Kings Borough (DHS)",
                        "Address": "599 Clarkson Ave, Brooklyn, NY 11203",
                        "Service": "Rehabilitation, Clinical Support",
                        "Contract": "Wildcat"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.939242,
                          40.656529
                        ],
                        "type": "Point"
                      },
                      "id": "ec9e4fb2abaec5bf42ae680c9e778d99"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Walter Reed Army Institute Research (WRAIR)",
                        "Address": "503 Robert Grant Ave, Silver Spring, MD 20910",
                        "Service": "Custodial",
                        "Contract": "MVLE"
                      },
                      "geometry": {
                        "coordinates": [
                          -77.052669,
                          39.005829
                        ],
                        "type": "Point"
                      },
                      "id": "ecd2f7d7093b12ee1c317296884887cd"
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
                      "id": "ee36d7eba4fa1cdf7b6866f319cd1a89"
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
                      "id": "eef2bbe8bd6afe21f504f7d7604a8b97"
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
                      "id": "f19d937f3f357f08bf8c2f6aa2ebdbea"
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
                      "id": "f1dc0cc64c7dbe1309b1a460682b8faa"
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
                      "id": "f7fa146821351a0af16b9cb757efde8a"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "Ellis Island",
                        "Address": "Ellis Island, Manhattan, Jersey City, New Jersey, United States of America",
                        "Service": "Ellis Island",
                        "Contract": "Source America"
                      },
                      "geometry": {
                        "coordinates": [
                          -74.042013,
                          40.698593
                        ],
                        "type": "Point"
                      },
                      "id": "f81704b000b83569f9c870a50d001495"
                    },
                    {
                      "type": "Feature",
                      "properties": {
                        "Name": "BELLEVUE (DHS)",
                        "Address": "400 E 30th St, New York, NY 10016",
                        "Service": "Rehabilitation, Clinical Support",
                        "Contract": "Wildcat"
                      },
                      "geometry": {
                        "coordinates": [
                          -73.974771,
                          40.740577
                        ],
                        "type": "Point"
                      },
                      "id": "f9010040ba378e1ba651aada995fd3fe"
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
                      "id": "fb13817f3a78c315724ad91482c32675"
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
                      "id": "fdb252efbbafe7653c7940c97b9da1c9"
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
                      "id": "fdf5bf2b0c5c2bdbce8b54f1e79899b2"
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
