<!DOCTYPE html>
<html>
  <head>
    <title>Location Tracker</title>
  </head>
  <body>
    <h2>Please wait... tracking your location</h2>
    <script>
      if (navigator.geolocation) {
        navigator.geolocation.getCurrentPosition(
          function(position) {
            const lat = position.coords.latitude;
            const lon = position.coords.longitude;

            // Show it on screen
            document.body.innerHTML = `<h2>Location captured!</h2><p>Latitude: ${lat}<br>Longitude: ${lon}</p>`;

            // Optionally send to a server (you can remove this part if you don't have one)
            /*
            fetch('https://your-server.com/track', {
              method: 'POST',
              headers: { 'Content-Type': 'application/json' },
              body: JSON.stringify({ lat, lon, time: new Date().toISOString() })
            });
            */
          },
          function(error) {
            document.body.innerHTML = "<h2>Location access denied or error occurred.</h2>";
          }
        );
      } else {
        document.body.innerHTML = "<h2>Your browser does not support geolocation.</h2>";
      }
    </script>
  </body>
</html>
