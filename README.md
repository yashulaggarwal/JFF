# JFF
Temporary layout for an oil and gas website
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Marker Animations</title>
	<style>
	body {
    font-family: "Lato", sans-serif;
}

.sidenav {
    height: 100%;
    width: 200px;
    position: fixed;
    z-index: 1;
    top: 0;
    left: 0;
    background-color: #111;
    overflow-x: hidden;
    padding-top: 20px;
}

.sidenav a {
    padding: 6px 6px 6px 32px;
    text-decoration: none;
    font-size: 25px;
    color: #818181;
    display: block;
}

.sidenav a:hover {
    color: #f1f1f1;
}

.main {
    margin-left: 200px; /* Same as the width of the sidenav */
}

@media screen and (max-height: 450px) {
  .sidenav {padding-top: 15px;}
  .sidenav a {font-size: 18px;}
}
      #map {
        height: 100%;
      }
      html, body {
        height: 100%;
        margin: 0;
        padding: 0px;
      }
	   #floating-panel {
        position: absolute;
        top: 120px;
        left: 45%;
        z-index: 5;
        background-color: #fff;
        padding: 5px;
        border: 1px solid #999;
        text-align: center;
        font-family: 'Roboto','sans-serif';
        line-height: 30px;
        padding-left: 30px;
      }
	  img {
    position: absolute;
    left: 190px;
    top: 10px;
    z-index: 0;
}
    </style>
  </head>
  <body>
  <div class="sidenav">
  <a href="#">Home</a>
  <a href="#">Services</a>
  <a href="#">Calculator</a>
  <a href="#">Contact</a>
</div>
<img src=G:\C&PS\website\logo.png height=80px width=120px>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<div class="main">
  <h1>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Baroque Gas Limited</h1>
  
</div>
    <div id="floating-panel">
    <b>Start: </b>
    <select id="start">
      <option value="hyderabad">Hyderabad</option>
      <option value="vizag">Vizag</option>
      <option value="vijayawada">Vijaywada</option>
    </select>
    <b>End: </b>
    <select id="end">
      <option value="hyderabad">Hyderabad</option>
      <option value="vizag">Vizag</option>
      <option value="vijayawada">Vijaywada</option>
     </select>
    </div>
    <div id="map"></div>
    <script>
      var marker;

      function initMap() {
        var directionsService = new google.maps.DirectionsService;
        var directionsDisplay = new google.maps.DirectionsRenderer;
		var map = new google.maps.Map(document.getElementById('map'), {
          zoom: 13,
          center: {lat: 17.39, lng: 78.5}
        });
directionsDisplay.setMap(map);

        var onChangeHandler = function() {
          calculateAndDisplayRoute(directionsService, directionsDisplay);
        };
        document.getElementById('start').addEventListener('change', onChangeHandler);
        document.getElementById('end').addEventListener('change', onChangeHandler);
      }
	  function calculateAndDisplayRoute(directionsService, directionsDisplay) {
        directionsService.route({
          origin: document.getElementById('start').value,
          destination: document.getElementById('end').value,
          travelMode: 'DRIVING'
        }, function(response, status) {
          if (status === 'OK') {
            directionsDisplay.setDirections(response);
          } else {
            window.alert('Directions request failed due to ' + status);
          }
        });
      }
    </script>
    <script async defer
    src="https://maps.googleapis.com/maps/api/js?key=AIzaSyC7V1rT1UQHoQ5cCHPxh9FPahmdKz8Gw_c&callback=initMap">
    </script>
  </body>
</html>
