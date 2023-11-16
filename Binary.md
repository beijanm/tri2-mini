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
  <style>
    body {
      font-family: 'Arial', sans-serif;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      background-color: #333;
      color: white;
      text-align: center;
    }
    #clock {
      font-size: 24px;
      letter-spacing: 2px;
    }
    .binary, .decimal {
      margin: 10px 0;
    }
    .label {
      font-size: 18px;
      margin-bottom: 5px;
    }
  </style>
</head>
<body>
  <div id="clock">
    <div class="binary">
      <div class="label">Binary Time</div>
      <span id="binaryHours">00</span> : <span id="binaryMinutes">00</span> : <span id="binarySeconds">00</span>
    </div>
    <div class="decimal">
      <div class="label">Decimal Time</div>
      <span id="decimalHours">00</span> : <span id="decimalMinutes">00</span> : <span id="decimalSeconds">00</span>
    </div>
  </div>

  <script>
    function updateClock() {
      var now = new Date();
      var hours = now.getHours();
      var minutes = now.getMinutes();
      var seconds = now.getSeconds();

      // Convert hours, minutes, and seconds to binary
      var binaryHours = padZero((hours % 12 || 12).toString(2));
      var binaryMinutes = padZero(minutes.toString(2));
      var binarySeconds = padZero(seconds.toString(2));

      // Update binary time display
      document.getElementById('binaryHours').innerText = binaryHours;
      document.getElementById('binaryMinutes').innerText = binaryMinutes;
      document.getElementById('binarySeconds').innerText = binarySeconds;

      // Update decimal time display
      document.getElementById('decimalHours').innerText = padZero(hours.toString());
      document.getElementById('decimalMinutes').innerText = padZero(minutes.toString());
      document.getElementById('decimalSeconds').innerText = padZero(seconds.toString());

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
