---
title: Digital Clock
layout: default
courses: { csp: {week: 13} }
type: ccc
---

<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Binary Digital Clock</title>
</head>
<body>
  <div id="clock"></div>

  <script>
    function updateClock() {
      
      // Get the current date
      var day = now.getDate();
      var month = now.getMonth() + 1; // JavaScript months are 0-11
      var year = now.getFullYear();

      var now = new Date();
      var hours = now.getHours();
      var minutes = now.getMinutes();
      var seconds = now.getSeconds();

      // Convert hours, minutes, and seconds to binary
      var binaryHours = padZero((hours % 12 || 12).toString(2));
      var binaryMinutes = padZero(minutes.toString(2));
      var binarySeconds = padZero(seconds.toString(2));

      // Convert binary to decimal
      var decimalHours = parseInt(binaryHours, 2);
      var decimalMinutes = parseInt(binaryMinutes, 2);
      var decimalSeconds = parseInt(binarySeconds, 2);

      // Update the clock display
      document.getElementById('clock').innerHTML =
      padZero(decimalHours.toString()) + ' : ' + padZero(decimalMinutes.toString()) + ' : ' + padZero(decimalSeconds.toString()) + (hours >= 12 ? ' PM' : ' AM') +
      '<br>' + padZero(day.toString()) + '/' + padZero(month.toString()) + '/' + year; // Add the date


      // Update every second
      setTimeout(updateClock, 1000);
    }


    function padZero(value) {
      return value.length < 2 ? '0' + value : value;
    }

    // Initial call to display the clock
    updateClock();
  </script>
</body>
</html>
