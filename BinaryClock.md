---
title: Binary Clock
layout: default
courses: { csp: {week: 14} }
type: ccc
---

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
            left: -30px;
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
