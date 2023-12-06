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
  <title>Binary Digital Clock with AM/PM and Date</title>
  <style>
    /* Your existing CSS styles */
    @font-face {
      font-family: 'Digital-7';
      src: url('Digital-7.ttf') format('truetype');
    }

    body {
      font-family: 'Digital-7', sans-serif;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      background-color: #333;
      color: white;
      text-align: center;
    }

    /* Styles for the clock elements */
    #clock {
      font-family: 'Digital-7', sans-serif;
      font-size: 48px;
      letter-spacing: 2px;
    }

    .date, .binary, .decimal {
      font-family: 'Digital-7', sans-serif;
      margin: 20px 0;
      padding: 10px;
      background-color: rgba(255, 255, 255, 0.1);
    }

    .label {
      font-size: 24px;
      color: #20C20E; /* Green */
      border: 3px solid #20C20E; /* Green */
      border-radius: 10px;
      box-shadow: 0px 0px 10px #20C20E; /* Green */
      padding: 10px; /* Add space around the text */
    }

    .circle {
      width: 100px;
      height: 100px;
      border-radius: 50%;
      background-color: #20C20E; /* Initial color */
      margin-top: 20px;
    }
  </style>
</head>
<body>
  <div id="clock">
    <div class="date">
      <div class="label">Current Date</div>
      <span id="currentDate">2023-11-16</span>
    </div>
    <div class="binary">
      <div class="label">Binary Time</div>
      <span id="binaryHours">00</span> : <span id="binaryMinutes">00</span> : <span id="binarySeconds">00</span>
      <span id="binaryAmPm">AM</span>
    </div>
    <div class="decimal">
      <div class="label">Decimal Time</div>
      <span id="decimalHours">00</span> : <span id="decimalMinutes">00</span> : <span id="decimalSeconds">00</span>
      <span id="decimalAmPm">AM</span>
    </div>
    <div class="circle" id="colorCircle"></div>
  </div>

  <script>
    function updateClock() {
      var now = new Date();
      var hours = now.getHours();
      var minutes = now.getMinutes();
      var seconds = now.getSeconds();

      var amPm = hours >= 12 ? 'PM' : 'AM';
      var displayHours = hours % 12;
      displayHours = displayHours ? displayHours : 12;

      var binaryHours = padZero(displayHours.toString(2));
      var binaryMinutes = padZero(minutes.toString(2));
      var binarySeconds = padZero(seconds.toString(2));

      document.getElementById('binaryHours').innerText = binaryHours;
      document.getElementById('binaryMinutes').innerText = binaryMinutes;
      document.getElementById('binarySeconds').innerText = binarySeconds;
      document.getElementById('binaryAmPm').innerText = amPm;

      document.getElementById('decimalHours').innerText = padZero(displayHours.toString());
      document.getElementById('decimalMinutes').innerText = padZero(minutes.toString());
      document.getElementById('decimalSeconds').innerText = padZero(seconds.toString());
      document.getElementById('decimalAmPm').innerText = amPm;

      var currentDateElement = document.getElementById('currentDate');
      currentDateElement.innerText = formatDate(now);
      
      var binaryDate = padZero(now.getDate().toString(2));
      var binaryValue = parseInt(binaryDate, 2);
      var color = '#' + binaryValue.toString(16).padStart(6, '0');
      
      // Apply the color to the circle
      document.getElementById('colorCircle').style.backgroundColor = color;

      setTimeout(updateClock, 1000);
    }

    function padZero(value) {
      return value.length < 2 ? '0' + value : value;
    }

    function formatDate(date) {
      var day = padZero(date.getDate().toString());
      var month = padZero((date.getMonth() + 1).toString());
      var year = date.getFullYear();
      return year + '-' + month + '-' + day;
    }

    updateClock();
  </script>
</body>
</html>
