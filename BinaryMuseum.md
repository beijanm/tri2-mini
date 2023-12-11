---
title: Binary Museum
layout: post
courses: { csp: {week: 14} }
type: ccc
---

<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Binary Museum</title>

    <!-- Styles for the first section -->
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

<title>The Binary Museum</title>
<h3>Binary Digital Clock</h3>

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

    /* Styles for the clock elements */
    #clock {
      font-family: 'Digital-7', sans-serif;
      font-size: 24px; /* Updated font size */
      letter-spacing: 2px;
    }

    .date, .binary, .decimal {
      font-family: 'Digital-7', sans-serif;
      margin: 20px 0;
      padding: 10px;
      background-color: rgba(255, 255, 255, 0.1);
    }

    .label {
      font-size: 18px; /* Smaller label font size */
      color: #20C20E; /* Green */
      border: 3px solid #20C20E; /* Green */
      border-radius: 10px;
      box-shadow: 0px 0px 10px #20C20E; /* Green */
      padding: 10px; /* Add space around the text */
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
    <div id="colorExplanation">Clock color changes based on the combined binary representation of time (hours, minutes, seconds). For instance, the individual binary digits affect the color.</div>
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
      
      // Extract the tens place of seconds
      var tensPlaceSeconds = Math.floor(seconds / 10);

      // Define colors based on the tens place of seconds
      var color;
      switch (tensPlaceSeconds) {
        case 0:
          color = 'yellow'; // 00-09 seconds
          break;
        case 1:
          color = 'red'; // 10-19 seconds
          break;
        case 2:
          color = 'blue'; // 20-29 seconds
          break;
        case 3:
          color = 'green'; // 30-39 seconds
          break;
        case 4:
          color = 'purple'; // 40-49 seconds
          break;
        case 5:
          color = 'pink'; // 50-59 seconds
          break;
        default:
          color = 'yellow'; // Default color for seconds beyond 59
          break;
      }

      // Apply the color to the clock
      document.getElementById('clock').style.color = color;

      setTimeout(updateClock, 1000); // Change every 1 second
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

    updateClock(); // Initial call to start the clock update
    setInterval(updateClock, 1000); // Update the clock every second
  </script>
</body>
</html>


<h3>Binary Clock</h3>

<html>
<head>
    <title>BCD Clock</title>
    <style>
        .led {
            width: 30px;
            height: 30px;
            border-radius: 50%;
            background-color: #ddd;
            margin: 10px;
        }

        .active {
            background-color: #0f0;
        }

        .digit {
            display: inline-block;
            vertical-align: top;
            margin-right: 15px;
            text-align: center;
        }

        #bcdClock {
            position: relative;
            margin: 0 auto;
            padding: 20px;
            text-align: center;
        }

        .time {
            margin-top: 10px;
            font-size: 20px;
        }

        h1 {
            text-align: center;
        } 
        
        p {
            text-align: left;
        }

        .label {
            position: absolute;
            left: 185px;
        }

        .colon {
            display: inline-block;
            vertical-align: top;
            margin-right: 15px;
            text-align: center;
            margin-top: 175px;
        }
    </style>
</head>
<body>
    <h1>Binary Coded Decimal (BCD) Clock</h1>
    <p>This is a Binary Coded Decimal (BCD) clock. It displays the current time in both binary and decimal formats. Each column represents a digit of the current time in binary format, from top (most significant bit) to bottom (least significant bit). The first two columns represent the hour, the next two represent the minute, and the last two represent the second. The time is displayed in 12-hour format with an AM/PM indicator.</p>
    <div id="bcdClock"></div>
    <p>
    <br>- The `updateClock` function first gets the current time using the JavaScript `Date` object. It then calculates the hours, minutes, and seconds, and converts the hours to a 12-hour format.
    <br>- The function then creates two arrays: `binaryTime` and `realTime`. The `binaryTime` array stores the binary representation of each digit of the current time, and the `realTime` array stores the decimal representation of each digit of the current time.
    <br>- The function then clears the `bcdClock` div and creates the BCD clock. It does this by looping through each digit of the time, creating a `div` for each digit, and adding the appropriate number of LEDs to each `div`. The LEDs are styled according to whether their corresponding bit in the binary representation is a 1 (on) or a 0 (off).
    <br>- The function also creates a `div` for each digit of the real time and appends it to the corresponding digit `div`. This displays the decimal representation of the time underneath the binary representation.
    <br>- Finally, the function creates a `div` for the AM/PM indicator and appends it to the `bcdClock` div.
    <br>- The `updateClock` function is then set to be called again after a delay of 1000 milliseconds (1 second) using the `setTimeout` function. This updates the clock every second.
</p>
    <script>
        function updateClock() {
            const currentTime = new Date();
            let hours = currentTime.getHours();
            const minutes = currentTime.getMinutes();
            const seconds = currentTime.getSeconds();

            const ampm = hours >= 12 ? 'PM' : 'AM';
            hours = hours % 12;
            hours = hours ? hours : 12; // the hour '0' should be '12'

            const binaryTime = [
                pad((Math.floor(hours / 10)).toString(2), 4),
                pad((hours % 10).toString(2), 4),
                pad((Math.floor(minutes / 10)).toString(2), 4),
                pad((minutes % 10).toString(2), 4),
                pad((Math.floor(seconds / 10)).toString(2), 4),
                pad((seconds % 10).toString(2), 4)
            ];

            const realTime = [
                Math.floor(hours / 10).toString(),
                (hours % 10).toString(),
                Math.floor(minutes / 10).toString(),
                (minutes % 10).toString(),
                Math.floor(seconds / 10).toString(),
                (seconds % 10).toString()
            ];

            document.getElementById('bcdClock').innerHTML = '';

            for (let i = 0; i < 6; i++) {
                const digitContainer = document.createElement('div');
                digitContainer.className = 'digit';
                for (let j = 3; j >= 0; j--) {
                    const led = document.createElement('div');
                    led.className = 'led' + (binaryTime[i][j] === '1' ? ' active' : '');
                    digitContainer.appendChild(led);
                    if (i === 0) {
                        const label = document.createElement('div');
                        label.className = 'label';
                        label.textContent = Math.pow(2, 3 - j).toString();
                        led.appendChild(label);
                    }
                }
                const timeElement = document.createElement('div');
                timeElement.className = 'time';
                timeElement.textContent = realTime[i];
                digitContainer.appendChild(timeElement);
                document.getElementById('bcdClock').appendChild(digitContainer);

                // Add a colon after every two digits, but not after the last pair
                if (i === 1 || i === 3) {
                    const colonElement = document.createElement('div');
                    colonElement.className = 'colon';
                    colonElement.textContent = ':';
                    document.getElementById('bcdClock').appendChild(colonElement);
                }
            }

            const ampmElement = document.createElement('div');
            ampmElement.className = 'time';
            ampmElement.textContent = ampm;
            document.getElementById('bcdClock').appendChild(ampmElement);

            setTimeout(updateClock, 1000);
        }

        function pad(str, length) {
            return '0'.repeat(Math.max(0, length - str.length)) + str;
        }

        updateClock();  // Initial call to display the clock
    </script>
</body>
</html>
