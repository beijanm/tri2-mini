---
toc: true
comments: false
layout: hack
title: Left/Right Shift Binary Code Visual 
type: ccc
courses: { csp: {week: 14} }

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Binary Shifts Example</title>
  <script>
    function leftShiftBinary() {
      let binaryNumber = parseInt(document.getElementById('binaryInput').value, 2);
      let shifts = parseInt(document.getElementById('shiftInput').value);

      let results = [];

      for (let i = 0; i < shifts; i++) {
        binaryNumber = binaryNumber << 1;
        results.push(binaryNumber);
      }

      document.getElementById('output').innerHTML = `<p>Initial binary number: ${binaryNumber.toString(2)}</p>`;
      
      results.forEach((result, index) => {
        document.getElementById('output').innerHTML += `<p>Left-shift ${index + 1} times: ${result.toString(2)}</p>`;
      });
    }

    function rightShiftBinary() {
      let binaryNumber = parseInt(document.getElementById('binaryInput').value, 2);
      let shifts = parseInt(document.getElementById('shiftInput').value);

      let results = [];

      for (let i = 0; i < shifts; i++) {
        binaryNumber = binaryNumber >> 1;
        results.push(binaryNumber);
      }

      document.getElementById('output').innerHTML = `<p>Initial binary number: ${binaryNumber.toString(2)}</p>`;

      results.forEach((result, index) => {
        document.getElementById('output').innerHTML += `<p>Right-shift ${index + 1} times: ${result.toString(2)}</p>`;
      });
    }
  </script>
</head>
<body>
  <h1>Binary Shifts Example</h1>

  <label for="binaryInput">Enter a binary number:</label>
  <input type="text" id="binaryInput" placeholder="Enter binary number">

  <label for="shiftInput">Enter the number of shifts:</label>
  <input type="number" id="shiftInput" placeholder="Enter shift amount">

  <button onclick="leftShiftBinary()">Left Shift</button>
  <button onclick="rightShiftBinary()">Right Shift</button>

  <div id="output"></div>
</body>
</html>
