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
    .weather {
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
    <div class="weather">
      <div class="label">Current Weather:</div>
      <p>                                       </p>
      <div>
                <a class="weatherwidget-io" href="https://forecast7.com/en/32d72n117d16/san-diego/" data-label_1="SAN DIEGO" data-label_2="WEATHER" data-theme="original" >SAN DIEGO WEATHER</a>
        <script>
        !function(d,s,id){var js,fjs=d.getElementsByTagName(s)[0];if(!d.getElementById(id)){js=d.createElement(s);js.id=id;js.src='https://weatherwidget.io/js/widget.min.js';fjs.parentNode.insertBefore(js,fjs);}}(document,'script','weatherwidget-io-js');
        </script>
      </div>
    </div>
  </div>

  <script>
    function updateClock() {
      var now = new Date();
      var hours = now.getHours();
      var minutes = now.getMinutes();
      var seconds = now.getSeconds();

      // Determine AM or PM
      var amPm = hours >= 12 ? 'PM' : 'AM';

      // Convert to 12-hour format for display
      var displayHours = hours % 12;
      displayHours = displayHours ? displayHours : 12; // Convert '0' to '12'

      // Convert hours, minutes, and seconds to binary
      var binaryHours = padZero(displayHours.toString(2));
      var binaryMinutes = padZero(minutes.toString(2));
      var binarySeconds = padZero(seconds.toString(2));

      // Update binary time display
      document.getElementById('binaryHours').innerText = binaryHours;
      document.getElementById('binaryMinutes').innerText = binaryMinutes;
      document.getElementById('binarySeconds').innerText = binarySeconds;
      document.getElementById('binaryAmPm').innerText = amPm;

      // Update decimal time display
      document.getElementById('decimalHours').innerText = padZero(displayHours.toString());
      document.getElementById('decimalMinutes').innerText = padZero(minutes.toString());
      document.getElementById('decimalSeconds').innerText = padZero(seconds.toString());
      document.getElementById('decimalAmPm').innerText = amPm;

      // Update date display
      document.getElementById('currentDate').innerText = formatDate(now);

      // Update every second
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

    // Initial call to display the clock
    updateClock();
  </script>
</body>
</html>
