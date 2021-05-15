<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>Display a popup c1 {cursor: crosshair;}
on hover</title>
<meta name="viewport" content="initial-scale=1,maximum-scale=1,user-scalable=no">
<link href="https://api.mapbox.com/mapbox-gl-js/v2.2.0/mapbox-gl.css" rel="stylesheet">
<script src="https://api.mapbox.com/mapbox-gl-js/v2.2.0/mapbox-gl.js"></script>
<style>
body { margin: 0; padding: 0; }
#map { position: absolute; top: 0; bottom: 0; width: 100%; }
</style>
</head>
<body>
<style>
    .mapboxgl-popup {
        max-width: 600px;
        font: 12px/20px 'Helvetica Neue', Arial, Helvetica, sans-serif;
    }
</style>
<div id="map"></div>
<script>
	mapboxgl.accessToken = 'pk.eyJ1IjoiY2FibGFja3dlbGwiLCJhIjoiY2tvYm5nbDU4MDB4YTJucWE4NDR5cWN5eCJ9.gP8HwLo3YCdhIFMVSLM2HA';
    var map = new mapboxgl.Map({
        container: 'map',
        style: 'mapbox://styles/cablackwell/ckon4qsq73jiw18mukn41lna7',
        center: [-73.9712, 40.7831],
        zoom: 10,
    });

map.getCanvas().style.cursor = 'crosshair';


    map.on('load', function () {
        map.addSource('Places', {
            'type': 'geojson',
            'data': {
                'type': 'FeatureCollection',
                'features': [
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
                    "id": "008a287f5843ef51916bff77b428cd53"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "Gertz Plaza Building",
                      "Address": "92-31 Union Hall Street. Jamaica, NY 11443",
                      "Service": "Document Management",
                      "Contract": "Fedcap NY"
                    },
                    "geometry": {
                      "coordinates": [
                        -73.797149,
                        40.70362
                      ],
                      "type": "Point"
                    },
                    "id": "0145a69ec94e8f683d768d6dea139d29"
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
                    "id": "0235a692727c78d529cf492856cdd2d0"
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
                    "id": "0326c6ab46eaec9fe9c0a744ad0c3e9f"
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
                    "id": "0752f3c06354bd6bbc19e8ef1efb5dbe"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "Banknote: Light Marker",
                      "Address": "1231 Lafayette Ave, Bronx, NY 10474",
                      "Service": "Industrial Manufacturing Light Marker",
                      "Contract": "Source America"
                    },
                    "geometry": {
                      "coordinates": [
                        -73.890603,
                        40.816759
                      ],
                      "type": "Point"
                    },
                    "id": "0794bd42691948f59aad7d36b5e16e1c"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "Regal Court Business Centre",
                      "Address": "Regal Court Business Centre, 42-44 High St, Slough SL1 1EL, UK",
                      "Service": "",
                      "Contract": "Fedcap UK"
                    },
                    "geometry": {
                      "coordinates": [
                        -0.597544,
                        51.509917
                      ],
                      "type": "Point"
                    },
                    "id": "0940d03c0c954d9124294213c751c25d"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "DLA Maritme Portsmouth Naval Yard Packaging Hoodies & Booties",
                      "Address": "Portsmouth, VA 23704",
                      "Service": "",
                      "Contract": "CWS"
                    },
                    "geometry": {
                      "coordinates": [
                        -76.296317,
                        36.823613
                      ],
                      "type": "Point"
                    },
                    "id": "0997283e805e099fa27a3d6cccaecb2c"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "VA Newark",
                      "Address": "20 Washington Pl, Newark, NJ 07102",
                      "Service": "Janitorial Services/ Mech Maintenance",
                      "Contract": "Source America"
                    },
                    "geometry": {
                      "coordinates": [
                        -74.17048,
                        41.101045
                      ],
                      "type": "Point"
                    },
                    "id": "09d752dfb2dc89ec1bb194fc884c4049"
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
                    "id": "0a1fb846da79e1c000163f5c23ada080"
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
                    "id": "0a2f6db0eddf952bf950e1a1bf40e82e"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "Atlantic County Facility Mgmt",
                      "Address": "101 SOUTH SHORE RD, NORTHFIELD NJ 08232",
                      "Service": "",
                      "Contract": "ACCESS NJ"
                    },
                    "geometry": {
                      "coordinates": [
                        -74.536821,
                        39.377363
                      ],
                      "type": "Point"
                    },
                    "id": "0c22baf1f6cfe3e81093a6772cff9efa"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "Public Archives Building ",
                      "Address": "121 MLK Jr. Blvd, N Dover, DE 19901",
                      "Service": "",
                      "Contract": "Delaware"
                    },
                    "geometry": {
                      "coordinates": [
                        -75.52037,
                        39.15844
                      ],
                      "type": "Point"
                    },
                    "id": "0e53b3a9ba7a40f74ffe54322e6ff08e"
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
                    "id": "0ebe59c38cb14ebe63c1cc3bb95cb913"
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
                    "id": "0fe12db8bba719624210029d1bb9e16e"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "Safe Harbor Recovery Center",
                      "Address": "865 Islington St, Portsmouth, NH 03801",
                      "Service": "Employment Support, Vocational and Substance Abuse Rehabilitation",
                      "Contract": ""
                    },
                    "geometry": {
                      "coordinates": [
                        -70.774054,
                        43.068242
                      ],
                      "type": "Point"
                    },
                    "id": "1060d3756c92df21a91d9258206c0c2d"
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
                    "id": "1101a9f08b539a71c433413eaa56a7ae"
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
                    "id": "112a529852303b183b61050cc923f3a6"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "Auburn (DHS)",
                      "Address": "39 Auburn Pl, Brooklyn, NY 11205",
                      "Service": "",
                      "Contract": "Wildcat"
                    },
                    "geometry": {
                      "coordinates": [
                        -73.976422,
                        40.69477
                      ],
                      "type": "Point"
                    },
                    "id": "17537138f9a3fb2d851352e0cfa7cf4f"
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
                    "id": "1919cb1c669bce9d773d2648486b776a"
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
                    "id": "19c7e5f1a88114dc818effb8dd0150c2"
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
                    "id": "1c219500574513aa3dd62086fe7102ec"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "Flatlands (DHS)",
                      "Address": "108-75 Avenue D, Brooklyn, NY 11236",
                      "Service": "",
                      "Contract": "Wildcat"
                    },
                    "geometry": {
                      "coordinates": [
                        -73.899387,
                        40.656476
                      ],
                      "type": "Point"
                    },
                    "id": "1e54be6e3979b27f0cd6acd262fc0eb4"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "Banknote: NYS Orange County",
                      "Address": "1231 Lafayette Ave, Bronx, NY 10474",
                      "Service": "Office Services Mail Services",
                      "Contract": "NYSID"
                    },
                    "geometry": {
                      "coordinates": [
                        -73.890603,
                        40.816759
                      ],
                      "type": "Point"
                    },
                    "id": "217e55a477a8ecb78958dbcf77938978"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "CWS - Rhode Island",
                      "Address": "20 Marblehead Ave, North Providence, RI 02904",
                      "Service": "",
                      "Contract": "CWS"
                    },
                    "geometry": {
                      "coordinates": [
                        -71.456883,
                        41.861142
                      ],
                      "type": "Point"
                    },
                    "id": "218007446419e6063ff2f53b22f45e17"
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
                    "id": "2229b623297072aa3e62ddcb42d92e8f"
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
                    "id": "224ae41bc73db147102966638788ece0"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "Prospect House - ( Buckinghamshire - High Wycombe)",
                      "Address": "38 Crendon Street, High Wycombe, Buckinghamshire, HP13 6AL",
                      "Service": "",
                      "Contract": "Fedcap UK"
                    },
                    "geometry": {
                      "coordinates": [
                        -0.747054,
                        51.629326
                      ],
                      "type": "Point"
                    },
                    "id": "224ef793bf367b2b5f3af109519d12f2"
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
                    "id": "22df4d59e0f1c504f10e2f126ab8a9db"
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
                    "id": "262d9a1091bee52173db27be3b7341b8"
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
                    "id": "2685863c38a6534275d096cd5b0cb1a2"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "NYC OATH Print & Mail",
                      "Address": "1231 Lafayette Ave, Bronx, NY 10474",
                      "Service": " Print & Mail",
                      "Contract": "Commercial"
                    },
                    "geometry": {
                      "coordinates": [
                        -73.890603,
                        40.816759
                      ],
                      "type": "Point"
                    },
                    "id": "277d84f0fe1088ec86e5fedc4cc6b211"
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
                    "id": "278181509c41223658c2ac189e5fb35b"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "Jamaica (DHS)",
                      "Address": "175-10 88th Ave, Jamaica, NY 11432",
                      "Service": "",
                      "Contract": "Wildcat"
                    },
                    "geometry": {
                      "coordinates": [
                        -73.786369,
                        40.711118
                      ],
                      "type": "Point"
                    },
                    "id": "27b7c0c11a543ba84b8065914aeb89d2"
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
                    "id": "2a0c6a554b45c39b8a5f83b9c0506388"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "",
                      "Address": "625 Fulton St, Brooklyn, NY 11201",
                      "Service": "",
                      "Contract": "Source America"
                    },
                    "geometry": {
                      "coordinates": [
                        -73.980031,
                        40.688694
                      ],
                      "type": "Point"
                    },
                    "id": "2a4c361a8ed37c47445f4cfe15873fe0"
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
                    "id": "2d44e7a8d7104570c1832b561c224d58"
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
                    "id": "2f0270b056eb1ab818f5e190372cea06"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "Linden (DHS)",
                      "Address": "501 New Lots Ave, Brooklyn, NY 11207",
                      "Service": "",
                      "Contract": "Wildcat"
                    },
                    "geometry": {
                      "coordinates": [
                        -73.889478,
                        40.663639
                      ],
                      "type": "Point"
                    },
                    "id": "2f6c6421bb87824a6872150e61c9fc1c"
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
                    "id": "3198d55b6b4f2b5fd4d63f7490b62ce1"
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
                    "id": "3308a346137d9a42b89246e2280d02d0"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "NJ Training School for Boys-JJC",
                      "Address": "1 State Home Rd., Monroe Township, NJ 08831-0500",
                      "Service": "",
                      "Contract": "ACCESS NJ"
                    },
                    "geometry": {
                      "coordinates": [
                        -74.420999,
                        40.341471
                      ],
                      "type": "Point"
                    },
                    "id": "341c4126f7486c1e92edb119d9488875"
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
                    "id": "3440d3e95b6da0b2638c2c10a65c22cd"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "FDNY",
                      "Address": "Various Locations",
                      "Service": "Office Services: Mailroom; Distribution; Messenger",
                      "Contract": ""
                    },
                    "geometry": {
                      "coordinates": [
                        -74.378586,
                        40.424408
                      ],
                      "type": "Point"
                    },
                    "id": "37e8fcd35e982ed4cc4c248c52cb0180"
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
                    "id": "382dbe01838d139802628722f7aa9828"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "Venture House (Berkshire - Bracknell)",
                      "Address": "Venture House, 2 Arlington Square, Bracknell RG12 1WA, UK",
                      "Service": "",
                      "Contract": "Fedcap UK"
                    },
                    "geometry": {
                      "coordinates": [
                        -0.757708,
                        51.41532
                      ],
                      "type": "Point"
                    },
                    "id": "3c6cbc81c13f645aababb5a7f9898036"
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
                    "id": "3ce5ebcdd2bc18fe7d09f203b419f827"
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
                    "id": "3e1d27a37255c193bd59e72685134b60"
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
                    "id": "3fef7ad08f4615fcc16bc9aa377dca78"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "Kings Borough (DHS)",
                      "Address": "599 Clarkson Ave, Brooklyn, NY 11203",
                      "Service": "",
                      "Contract": "Wildcat"
                    },
                    "geometry": {
                      "coordinates": [
                        -73.939242,
                        40.656529
                      ],
                      "type": "Point"
                    },
                    "id": "4102ccf0ad9f0298fdd2cda696817e0a"
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
                    "id": "419ce71328a44598772eccbe58a2dc36"
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
                    "id": "426082f2f1393fe236b8880f87a76c3c"
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
                    "id": "4297706f9f36694f184dc21ad401b260"
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
                    "id": "4484f8ccf2c7f2472ba30089c3c197b4"
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
                    "id": "47477ea5595a79ff747ae374def056ba"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "Banknote: HPD",
                      "Address": "1231 Lafayette Ave, Bronx, NY 10474",
                      "Service": "Office Services: Mail pickup & delivery",
                      "Contract": "NYSID"
                    },
                    "geometry": {
                      "coordinates": [
                        -73.890603,
                        40.816759
                      ],
                      "type": "Point"
                    },
                    "id": "479ac98511ccc7045e272323302310ad"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "NYS Department of Labor Church St",
                      "Address": "199 Church St, New York, NY 10007",
                      "Service": "Office Services: Messenger, mail sort, delivery",
                      "Contract": ""
                    },
                    "geometry": {
                      "coordinates": [
                        -74.006762,
                        40.716229
                      ],
                      "type": "Point"
                    },
                    "id": "4805b908018f2abc456a1c34b0285c73"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "Bridgeton",
                      "Address": "1 Landis Ave Bridgeton, NJ",
                      "Service": "",
                      "Contract": "ACCESS NJ"
                    },
                    "geometry": {
                      "coordinates": [
                        -75.207314,
                        39.461313
                      ],
                      "type": "Point"
                    },
                    "id": "4926441cf3aaa32c4f19fbb46447a8c2"
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
                    "id": "49c584755d88745d0c691bfeaec99dbd"
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
                    "id": "4a1a32ae6f7f568b00535c34f95d9245"
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
                    "id": "4a5e62ffa3e3dd54f2e7fd80dd642f4c"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "Asbury Park Office Building",
                      "Address": "630 Bangs Ave, Asbury Park, NJ ",
                      "Service": "",
                      "Contract": "ACCESS NJ"
                    },
                    "geometry": {
                      "coordinates": [
                        -74.010639,
                        40.216865
                      ],
                      "type": "Point"
                    },
                    "id": "4b5292157a99176d1f761d505cbc960c"
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
                    "id": "4dd7883fa13b287eca49744c7e486adc"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "DelDOT Talley ",
                      "Address": "1300 Talley Road, Wilmington, DE 19803",
                      "Service": "",
                      "Contract": "Delaware"
                    },
                    "geometry": {
                      "coordinates": [
                        -75.52822,
                        39.77661
                      ],
                      "type": "Point"
                    },
                    "id": "4e36da9f6b066cbb98c5989b0ab37c8b"
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
                    "id": "5123f38291d75c770f866dcf3298ed92"
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
                    "id": "52113b6bab21f200f85a6ab054f11d48"
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
                    "id": "52ec40816b8d06752b79009c3e7ff216"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "Alexandria Middle School",
                      "Address": "557 Rte. 513, Pittstown , NJ 08867",
                      "Service": "",
                      "Contract": "ACCESS NJ"
                    },
                    "geometry": {
                      "coordinates": [
                        -75.015167,
                        40.570443
                      ],
                      "type": "Point"
                    },
                    "id": "5527d73cfa29e0c6a39dcefb732b4482"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "Freehold Office Building",
                      "Address": "100 Daniels Way, Freehold, NJ",
                      "Service": "",
                      "Contract": "ACCESS NJ"
                    },
                    "geometry": {
                      "coordinates": [
                        -74.274728,
                        40.245441
                      ],
                      "type": "Point"
                    },
                    "id": "567e9188354a257e1556094cba3fa68b"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "Atlantic County Animal Shelter",
                      "Address": "240 OLD TURNPIKE RD PLEASANTVILLE NJ 08232",
                      "Service": "",
                      "Contract": "ACCESS NJ"
                    },
                    "geometry": {
                      "coordinates": [
                        -74.519992,
                        39.392675
                      ],
                      "type": "Point"
                    },
                    "id": "578cdd03c15c61a879adc7269a2e7bee"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "Atlantic County Facility Mgmt",
                      "Address": "201 SOUTH SHORE RD, NORTHFIELD NJ 08232",
                      "Service": "",
                      "Contract": "ACCESS NJ"
                    },
                    "geometry": {
                      "coordinates": [
                        -74.537534,
                        39.376787
                      ],
                      "type": "Point"
                    },
                    "id": "57986362011db4e34ae1472329df6e82"
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
                    "id": "5d43b5daf4a1812efc7966d6e42c098e"
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
                    "id": "5d4776fb281a74696acb27034dc00009"
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
                    "id": "5e352b86d4608f4e852006775cca700f"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "Bivalve - Ogdon Ave",
                      "Address": "2669 Ogdon Ave, Port Norris, NJ",
                      "Service": "",
                      "Contract": "ACCESS NJ"
                    },
                    "geometry": {
                      "coordinates": [
                        -75.02453,
                        39.239308
                      ],
                      "type": "Point"
                    },
                    "id": "5efaa2487702f368dcb654ac6f17a823"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": " Bass River Municipal Building",
                      "Address": "3 North Maple Avenue, New Gretna, Bass River Township, NJ 08224",
                      "Service": "",
                      "Contract": "ACCESS NJ"
                    },
                    "geometry": {
                      "coordinates": [
                        -74.451529,
                        39.592847
                      ],
                      "type": "Point"
                    },
                    "id": "5f104362ececb94eb8ea1498c76c35d5"
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
                    "id": "64150f51c6dde8abab21e49726830ec5"
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
                    "id": "64c454a2374dd436f85e7ccc2f8fdb26"
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
                    "id": "65a1dcfe3ec041d3c771a3edc498b87c"
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
                    "id": "65ce356a1b7eba71c139b7789f8ada9e"
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
                    "id": "68689cda3034aecbd01fd162f7563a89"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "LIRR Mail",
                      "Address": "1231 Lafayette Ave, Bronx, NY 10474",
                      "Service": "Office Services Mail Services",
                      "Contract": "NYSID"
                    },
                    "geometry": {
                      "coordinates": [
                        -73.890603,
                        40.816759
                      ],
                      "type": "Point"
                    },
                    "id": "68b4062812ab698d7974cc39e68302e7"
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
                    "id": "68bd976c6a1e89239d7bb3a070b6e305"
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
                    "id": "6a9229040df310caec4564aa84c880f9"
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
                    "id": "6b9517e0026d81eee6b24255d4ac6a38"
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
                    "id": "6c3a75f43a46d8991be60ba8ba7d5524"
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
                    "id": "6c599a47925696616b4c8bf6346f02c1"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "Manufacturing",
                      "Address": "1231 Lafayette Ave, Bronx, NY 10474",
                      "Service": "Manufacturing",
                      "Contract": "Fedcap NY"
                    },
                    "geometry": {
                      "coordinates": [
                        -73.890603,
                        40.816759
                      ],
                      "type": "Point"
                    },
                    "id": "6cdbce8c21e0685edaa0f1faed5d6f95"
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
                    "id": "6d1fe53bdc4faa87244e011c416baabc"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "Armory Men's shelter (DHS)",
                      "Address": "1322 Bedford Ave, Brooklyn, NY 11216",
                      "Service": "",
                      "Contract": "Wildcat"
                    },
                    "geometry": {
                      "coordinates": [
                        -73.953727,
                        40.67839
                      ],
                      "type": "Point"
                    },
                    "id": "6fdc15a44ac83965c8a9fa967fb68222"
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
                    "id": "707077bba6be3c36c76441e3895133de"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "Housing Trust Fund Corporation Section 8 Printing & Mailing Services",
                      "Address": "1231 Lafayette Ave, Bronx, NY 10474",
                      "Service": "Print & Mai",
                      "Contract": "Commercial"
                    },
                    "geometry": {
                      "coordinates": [
                        -73.890603,
                        40.816759
                      ],
                      "type": "Point"
                    },
                    "id": "73e351217e33985bdf48b164d7806110"
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
                    "id": "78351aa0d0781f5bfb8a1c6975adcac7"
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
                    "id": "78ff66a0cc25a58182ecab477cc127f0"
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
                    "id": "7ba1caf7fe850b2e91873e3a12d334b2"
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
                    "id": "7d9b05909d01c139f9566beae0bcef8f"
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
                    "id": "7e1086781cffd930572d1b8491dc66c2"
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
                    "id": "7e9319c96db18a7fc0a8447638f4c4cd"
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
                    "id": "7efc5c073c2738802666708dd8cfab97"
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
                    "id": "7f7766f0af47f7a06a829553d3c0ac31"
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
                    "id": "803b2c242fe3f8c11ee6bf10f93f3b86"
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
                    "id": "8512d33655a3d268a8c478d4ff530b98"
                  },
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
                    "id": "8552f7091f1c59e8ea2eb20c6e71dc7e"
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
                    "id": "87356bd49f05a1ac0d013aa72a43429a"
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
                    "id": "87e2852eff4e8b1e84bc5042b4870711"
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
                    "id": "88a85a0afb29739f683996516a376990"
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
                    "id": "8908f8d321fe507701d4a9a7557d6f5e"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "Trenton Office Complex",
                      "Address": "225 East State Street, Trenton, NJ 08666\n",
                      "Service": "",
                      "Contract": "ACCESS NJ"
                    },
                    "geometry": {
                      "coordinates": [
                        -74.75908,
                        40.218714
                      ],
                      "type": "Point"
                    },
                    "id": "8b051d49dda9f694773de960fbe0e6f9"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "NYS Department of Labor",
                      "Address": "Service: Office Services: Messenger, mail sort, delivery<br>Location of Service: 9 Bond St, NYC; 75 Varick St, NYC",
                      "Service": "",
                      "Contract": ""
                    },
                    "geometry": {
                      "coordinates": [
                        -73.983033,
                        40.689317
                      ],
                      "type": "Point"
                    },
                    "id": "8b71d60320c58dc27469755e2204d1d1"
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
                    "id": "8bbcfeb9cd535b0170f96be5cbbde23a"
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
                    "id": "8dd75c35872a48217e8cfaebc3ba3772"
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
                    "id": "9180347466499fdefbfbb461f69b5b37"
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
                    "id": "92dbf372ccca15e2554c67985c72217e"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "NYC Dept of Finance",
                      "Address": "Gertz Plaza Building, 92-31 Union Hall Street. Jamaica, NY 11443",
                      "Service": "Office Services Data Imaging, Scanning & Keying",
                      "Contract": "NYSID"
                    },
                    "geometry": {
                      "coordinates": [
                        -73.797068,
                        40.703177
                      ],
                      "type": "Point"
                    },
                    "id": "938845861dd7036fd39b57d9fb16b98c"
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
                    "id": "944ff44ca8f3f5ce5935aebddb7aba01"
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
                    "id": "958adbd943d17184a2627a581c736aaa"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "NYS Department of Labor Church St",
                      "Address": "99 Church StNew York, NY 10007",
                      "Service": "Office Services: Messenger, mail sort, delivery",
                      "Contract": ""
                    },
                    "geometry": {
                      "coordinates": [
                        -74.006762,
                        40.716229
                      ],
                      "type": "Point"
                    },
                    "id": "9868e6521c290856234783e953ef4425"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "NYC Transit Authority",
                      "Address": "130 Livingston St, Brooklyn, NY 11201",
                      "Service": "Office Services: Messenger, mail sort, delivery",
                      "Contract": ""
                    },
                    "geometry": {
                      "coordinates": [
                        -73.988544,
                        40.690291
                      ],
                      "type": "Point"
                    },
                    "id": "99174437b8ef58e31bec088e924e60c8"
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
                    "id": "9d20331daab04ccb0b6944a47f251eda"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "Broadway House (Berkshire-Newsbury)",
                      "Address": "Broadway House, 4-8 The Broadway, Newbury RG14 1BA, UK",
                      "Service": "",
                      "Contract": "Fedcap UK"
                    },
                    "geometry": {
                      "coordinates": [
                        -1.324514,
                        51.405327
                      ],
                      "type": "Point"
                    },
                    "id": "9ec33d1f11a29c0aba973e63bf93a215"
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
                    "id": "9f044a93b5fd74afd5a2d8e4fab6ef89"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "Acacia (DHS)",
                      "Address": "148 W 124th St, New York, NY 10027",
                      "Service": "",
                      "Contract": "Wildcat"
                    },
                    "geometry": {
                      "coordinates": [
                        -73.947991,
                        40.807653
                      ],
                      "type": "Point"
                    },
                    "id": "a014113ea966d80928a64f3b199a370b"
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
                    "id": "a0f172d2482b0173a674b276ac6f8b53"
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
                    "id": "a0fb169231e9c55dfe469bbf5cb9ced0"
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
                    "id": "a155092d21321a236da83d0751512e47"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "NYC Department of Health and Mental Hygiene",
                      "Address": "1231 Lafayette Ave, Bronx, NY 10474",
                      "Service": "Print, Scan, Mail",
                      "Contract": "Commercial"
                    },
                    "geometry": {
                      "coordinates": [
                        -73.890603,
                        40.816759
                      ],
                      "type": "Point"
                    },
                    "id": "a1eb59a32f33f4a59cb36f60085c4a03"
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
                    "id": "a25b1593c094e25e31b35231b040555c"
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
                    "id": "a295a486e78dacd8ea72f6ffba27eae6"
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
                    "id": "a2a81b8462d70f272119087a1c986cdd"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "Alexandria Twp. Board of Education",
                      "Address": "Lester Wilson Elementary School 525 Rte. 513, Pittstown , NJ 08867",
                      "Service": "",
                      "Contract": "ACCESS NJ"
                    },
                    "geometry": {
                      "coordinates": [
                        -75.025673,
                        40.566918
                      ],
                      "type": "Point"
                    },
                    "id": "a3888c6607f542d0e5c516ce777674f1"
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
                    "id": "a3963934a3c2dca640e88717307d37b6"
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
                    "id": "a3fc8e39c10dacab38c3cb0e7f6e9d30"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "Atlantic City Jail",
                      "Address": "5060 ATLANTIC AVE, MAYS LANDING NJ 08330",
                      "Service": "",
                      "Contract": "ACCESS NJ"
                    },
                    "geometry": {
                      "coordinates": [
                        -74.712373,
                        39.447802
                      ],
                      "type": "Point"
                    },
                    "id": "a4ea6fba23a23c4ea62990a62ce37000"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "Wilburtha NJSP Welcome Center",
                      "Address": "1020 River Rd., Ewing, NJ 08628",
                      "Service": "",
                      "Contract": "ACCESS NJ"
                    },
                    "geometry": {
                      "coordinates": [
                        -74.847201,
                        40.265604
                      ],
                      "type": "Point"
                    },
                    "id": "a97b324a2553a4ca88838237af0ba15c"
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
                    "id": "ac46f67cf8e34041b46beefdba651d50"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "Granite Pathways Headquarters",
                      "Address": "10 Ferry St STE 308, Concord, NH 0330",
                      "Service": "Vocational and Substance Abuse Rehabilitation",
                      "Contract": "Fedcap Group"
                    },
                    "geometry": {
                      "coordinates": [
                        -71.538173,
                        43.21275
                      ],
                      "type": "Point"
                    },
                    "id": "ac9ebee7791affce8c297a9ab8a186c1"
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
                    "id": "aef9b74f4bbb072b95aff7199134e2f2"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "Atlantic County Facility Mgmt",
                      "Address": "2 SOUTH MAIN STREET, PLEASANTVILLE NJ 08232",
                      "Service": "",
                      "Contract": "ACCESS NJ"
                    },
                    "geometry": {
                      "coordinates": [
                        -74.52241,
                        39.391713
                      ],
                      "type": "Point"
                    },
                    "id": "b0f65e59a776b8734dcdc55ed578b6fa"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "PATH (DHS)",
                      "Address": "E 151st St, Bronx, NY",
                      "Service": "",
                      "Contract": "Wildcat"
                    },
                    "geometry": {
                      "coordinates": [
                        -73.92388,
                        40.819256
                      ],
                      "type": "Point"
                    },
                    "id": "b17f1e789b6825a1e361784c87a6ce86"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "Banknote: NYC Council",
                      "Address": "1231 Lafayette Ave, Bronx, NY 10474",
                      "Service": "Office Services Mail Services",
                      "Contract": "NYSID"
                    },
                    "geometry": {
                      "coordinates": [
                        -73.890603,
                        40.816759
                      ],
                      "type": "Point"
                    },
                    "id": "b23041c285f8b55e1e462fa8c69bd9d7"
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
                    "id": "b4ec9d69c49e44863dd0ba0cd972f2dc"
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
                    "id": "b51e1944bbad7ff2b7763760bf09bce9"
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
                    "id": "b7b27c01b1b96d44891503e05763b5d2"
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
                    "id": "b9d47e066b8e35d39bfdc922f877c479"
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
                    "id": "bcf2ca1d7a7e9b13db4a3fb36518a366"
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
                    "id": "bd8881c97fb59fbd85b827734f6ee68d"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "Emma Bowan Community Service Center",
                      "Address": "1727 Amsterdam Ave, New York, NY 10031",
                      "Service": "",
                      "Contract": "CWS"
                    },
                    "geometry": {
                      "coordinates": [
                        -73.946957,
                        40.82545
                      ],
                      "type": "Point"
                    },
                    "id": "bdd8fce092e0282f27df180d478f4629"
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
                    "id": "c1149badd02f3a1f2098821b815e100b"
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
                    "id": "c186c198f5ce1aab7437041edf9b464d"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "Berkshire - Reading - 95 London St",
                      "Address": "95 London St, Reading RG1 4QA, UK",
                      "Service": "",
                      "Contract": "Fedcap UK"
                    },
                    "geometry": {
                      "coordinates": [
                        -0.967375,
                        51.451272
                      ],
                      "type": "Point"
                    },
                    "id": "c20c2025baf2e394e08f0f5bb487a426"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "Queens Service Site",
                      "Address": "Gertz Building 92-31 Union Hall Street, Jamaica, NY 11432",
                      "Service": "Clinic Support Services",
                      "Contract": "Fedcap WeCare"
                    },
                    "geometry": {
                      "coordinates": [
                        -73.797322,
                        40.703545
                      ],
                      "type": "Point"
                    },
                    "id": "c4eda9ad2398ce113a27edbe2918d161"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "Atlantic County Drexel Ave M B",
                      "Address": "1227 DREXEL AVE, ATLANTIC CITY NJ 08401",
                      "Service": "",
                      "Contract": "ACCESS NJ"
                    },
                    "geometry": {
                      "coordinates": [
                        -74.429438,
                        39.367432
                      ],
                      "type": "Point"
                    },
                    "id": "c5ca25ff52277502d15ab99c3ce976f7"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "NYC OATH Data Entry",
                      "Address": "Gertz Plaza Building, 92-31 Union Hall Street. Jamaica, NY 11443",
                      "Service": " Data Entry",
                      "Contract": "Commercial"
                    },
                    "geometry": {
                      "coordinates": [
                        -73.797068,
                        40.703177
                      ],
                      "type": "Point"
                    },
                    "id": "c5d7c465b757b728718132feb260c3f2"
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
                    "id": "c70d45634fe6eb31b7b05a15edf06d23"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "Atlantic County Facility Mgmt",
                      "Address": "235 DOLPHIN AVE, NORTHFIELD NJ 08232",
                      "Service": "",
                      "Contract": "ACCESS NJ"
                    },
                    "geometry": {
                      "coordinates": [
                        -74.543997,
                        39.379538
                      ],
                      "type": "Point"
                    },
                    "id": "c73b2d4f89b69bc228a8ac5f2d97652a"
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
                    "id": "c77451227af1748c482ad6b5bbcab512"
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
                    "id": "cacb7b7f6ee9e31f05b321e86df969db"
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
                    "id": "cc2ecc9c7c966b3ed185dff12239c4a2"
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
                    "id": "d0cd72247cf1f122fe48912e5e5cb845"
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
                    "id": "d1df5ca6a9a33fceb2f54d79713fea96"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "Deptcor",
                      "Address": "163 N Olden Ave. Trenton, NJ",
                      "Service": "",
                      "Contract": "ACCESS NJ"
                    },
                    "geometry": {
                      "coordinates": [
                        -74.741944,
                        40.228797
                      ],
                      "type": "Point"
                    },
                    "id": "d2a23f84ecab038c75e5711a8c6e8285"
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
                    "id": "d4394deddd8ff0dc52b02e9c6a3cfbdc"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "IRS",
                      "Address": "290 Broadway, NY, NY",
                      "Service": "Mailroom",
                      "Contract": ""
                    },
                    "geometry": {
                      "coordinates": [
                        -74.005182,
                        40.714739
                      ],
                      "type": "Point"
                    },
                    "id": "d481e9537e94f753598264caf5bb3831"
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
                    "id": "d78f18b7dbad0444b26afed06974a28e"
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
                    "id": "d7997b4009befa0968a2c88cd8166654"
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
                    "id": "d7b715046b0d4dcf330f1f04c2b34dc0"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "Atlantic County Facility Mgmt",
                      "Address": "1201 BACARACH BLVD ATLANTIC CITY NJ 08401 ",
                      "Service": "",
                      "Contract": "CWS"
                    },
                    "geometry": {
                      "coordinates": [
                        -74.451082,
                        39.377297
                      ],
                      "type": "Point"
                    },
                    "id": "d8b0e9472f7e7df0d855339023e5fadd"
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
                    "id": "da40dd087c4315e58ad10b473898ee1b"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "CWS - Boston",
                      "Address": "174 Portland St, Boston, MA 02114",
                      "Service": "",
                      "Contract": "CWS"
                    },
                    "geometry": {
                      "coordinates": [
                        -71.061785,
                        42.364134
                      ],
                      "type": "Point"
                    },
                    "id": "da46fcc3fbbb811c7aa768e10890bfe3"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "NJSPB Eggerts Crossing is AKA NY NJ RFTF, Regional Fugitive Task Force\n",
                      "Address": "141 Eggert's Crossing Rd, Lawrenceville, NJ 08648",
                      "Service": "",
                      "Contract": "ACCESS NJ"
                    },
                    "geometry": {
                      "coordinates": [
                        -74.743236,
                        40.27229
                      ],
                      "type": "Point"
                    },
                    "id": "da980f7d6f0dafcf2b14ceb80fa50272"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "LIRR Trailers",
                      "Address": "1231 Layfayette Avenue, Bronx, NY",
                      "Service": "Janitorial Services",
                      "Contract": "NYSID"
                    },
                    "geometry": {
                      "coordinates": [
                        -73.890603,
                        40.816759
                      ],
                      "type": "Point"
                    },
                    "id": "dc4c906ecad55a0bde576247bd307f94"
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
                    "id": "ddc65a3d0833ace008303e1fe78a9caf"
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
                    "id": "ddc9d650921609ec45e9820eacf5f9c8"
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
                    "id": "def87b73850a53a5a523d81338ffde4b"
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
                    "id": "e0ee082ad058e77e080d6b441283f656"
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
                    "id": "e3c01baf56add5238e49d70180e0597d"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "BELLEVUE (DHS)",
                      "Address": "400 E 30th St, New York, NY 10016",
                      "Service": "",
                      "Contract": "Wildcat"
                    },
                    "geometry": {
                      "coordinates": [
                        -73.974771,
                        40.740577
                      ],
                      "type": "Point"
                    },
                    "id": "e5371c16aa339d9cacb888d600245a5f"
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
                    "id": "e68cfce9ab6500d30c74f26eb55c42fb"
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
                    "id": "e76792c01dbd458fa30ac945a525606c"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "Catherine st. (DHS)",
                      "Address": "78 Catherine St, New York, NY 10038",
                      "Service": "",
                      "Contract": "Wildcat"
                    },
                    "geometry": {
                      "coordinates": [
                        -73.997508,
                        40.710603
                      ],
                      "type": "Point"
                    },
                    "id": "e90cf4de27c610141b3cf2f73ee6fcf2"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "Atlantic County Facility Mgmt",
                      "Address": "1333 ATLANTIC AVE, ATLANTIC CITY NJ 08401",
                      "Service": "",
                      "Contract": "ACCESS NJ"
                    },
                    "geometry": {
                      "coordinates": [
                        -74.427335,
                        39.362569
                      ],
                      "type": "Point"
                    },
                    "id": "ebc00d54c3bf7b8e11059158e3764ab3"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "Barbara Klienmen (DHS)",
                      "Address": "300 Skillman Ave, Brooklyn, NY 11211",
                      "Service": "",
                      "Contract": "Wildcat"
                    },
                    "geometry": {
                      "coordinates": [
                        -73.938413,
                        40.71653
                      ],
                      "type": "Point"
                    },
                    "id": "ec7543c5d47f1984a8af76d20142c0c1"
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
                    "id": "eceef2d11df0c6f5532d99245bd0d038"
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
                    "id": "edcac74d1a77984d1825d7f0f6f06f50"
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
                    "id": "eea4d658907c988286e6431763e27c2e"
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
                    "id": "f1b0e1c575f97b0df59429cf54c5d292"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "NJSP Museum & Log Cabin",
                      "Address": "1020 River Rd, Ewing, NJ 08628",
                      "Service": "",
                      "Contract": "ACCESS NJ"
                    },
                    "geometry": {
                      "coordinates": [
                        -75.02453,
                        39.239308
                      ],
                      "type": "Point"
                    },
                    "id": "f43ae67f3bab3ab3e727d9d64df03673"
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
                    "id": "f4832a809f2a8a2c7d7e85f0469971fe"
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
                    "id": "f5b60e3be3f1318d202f50bf9fce8e49"
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
                    "id": "f5c9a099d45b7175835ff559c344b23f"
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
                    "id": "f77281e5589345b154884fada1103bf9"
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
                    "id": "fa8f31bed3617ebba4e648ab897f11c9"
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
                    "id": "faf77263fa87f625bf10417ae35219b1"
                  },
                  {
                    "type": "Feature",
                    "properties": {
                      "Name": "DelDOT Kiamensi ",
                      "Address": "822 Kiamensi Road, Wilmington, DE 19804",
                      "Service": "",
                      "Contract": "Delaware"
                    },
                    "geometry": {
                      "coordinates": [
                        -75.63301,
                        39.72468
                      ],
                      "type": "Point"
                    },
                    "id": "fb5abda524b7dfc901ff324ffc1d08ca"
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
                    "id": "fcb804dd8873af5e9dbcc2231538928b"
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
                    "id": "fd7195f5f14441c72cc5c48f10a36cd3"
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
                    "id": "fe72f95c9a5094a25b981a9c13ac795f"
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
                    "id": "ff9d5066cdc39ecd20ae9fb4ec17abe1"
                  }
                ]
            }, cluster: true}).addLayer({
    id: 'clusters',
    type: 'circle',
    source: 'Places',
    filter:  ['Service'],
    paint: {
      'circle-radius': 15,
      'circle-color': 'Blue'
    }
  }).addLayer({
    id: 'cluster-label',
    type: 'symbol',
    source: 'Places',
    layout: {
      'text-field': "{Name}"
    }
  });


            ;
        // Add a layer showing the places.
        map.addLayer({
            'id': 'places',
            'type': 'circle',
            'source': 'Places',
            'paint': {
                'circle-color': '#4264fb',
                'circle-radius': 8,
                'circle-stroke-width': 1,
                'circle-stroke-color': '#ffffff'
            }
        });



        // Create a popup, but don't add it to the map yet.
        var popup = new mapboxgl.Popup({
            closeButton: false,
            closeOnClick: false,
        });

        map.on('mousemove', 'places', function (e) {
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

        map.on('mouseleave', 'places', function () {
            map.getCanvas().style.cursor = 'crosshair';
            popup.remove();
        });


    });

// map.addLayer({
//     id: 'clusters',
//     type: 'circle',
//     source: 'Places',
//     filter: ['value','Contract']});

</script>

</body>
</html>
