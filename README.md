# Smart-parking-system-
IOT-based car parking management system help in efficient parking space utilization only Arduino code and components used.
code:

<!DOCTYPE html>
<html>
<head>
  <title>IoT Car Parking Management System</title>
</head>
<body>
  <h1>IoT Car Parking Management System</h1>
  <p>This system uses an Arduino microcontroller, an ultrasonic sensor, and a WiFi module to track the availability of parking spots.</p>
  <p>The current status of the parking spots is shown below.</p>
  <div id="parking-spots"></div>
  <script>
    function updateParkingSpots() {
      var xhr = new XMLHttpRequest();
      xhr.open("GET", "/parking-spots");
      xhr.onload = function() {
        if (xhr.status == 200) {
          var parkingSpots = JSON.parse(xhr.responseText);
          var html = "";
          for (var i = 0; i < parkingSpots.length; i++) {
            var parkingSpot = parkingSpots[i];
            html += "<div class='parking-spot'>";
            html += "<span class='status'>" + parkingSpot.status + "</span>";
            html += "</div>";
          }
          document.getElementById("parking-spots").innerHTML = html;
        }
      };
      xhr.send();
    }
    setInterval(updateParkingSpots, 1000);
  </script>
</body>
</html>
