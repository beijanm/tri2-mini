---
toc: true
comments: false
layout: hack
title: Left/Right Shift Binary Code Visual 
type: ccc
courses: { csp: {week: 14} }

<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Binary Shifts Example</title>
  <style>
    body { font-family: Arial, sans-serif; }
    label, input, button { margin: 10px 0; }
    #output { margin-top: 20px; }
  </style>
  <script>
    function isBinary(number) {
      return /^[01]+$/.test(number);
    }

    function shiftBinary(isLeftShift) {
      const binaryNumberInput = document.getElementById('binaryInput').value;
      if (!isBinary(binaryNumberInput)) {
        alert("Please enter a valid binary number.");
        return;
      }

      let binaryNumber = parseInt(binaryNumberInput, 2);
      const shifts = parseInt(document.getElementById('shiftInput').value);

      if (shifts < 0) {
        alert("Please enter a non-negative integer for shifts.");
        return;
      }

      let results = [];
      let operation = isLeftShift ? (num) => num << 1 : (num) => num >> 1;

      for (let i = 0; i < shifts; i++) {
        binaryNumber = operation(binaryNumber);
        results.push(binaryNumber.toString(2));
      }

      let outputHtml = `<p>Initial binary number: ${binaryNumberInput}</p>`;
      results.forEach((result, index) => {
        outputHtml += `<p>${isLeftShift ? 'Left' : 'Right'}-shift ${index + 1} times: ${result}</p>`;
      });
      document.getElementById('output').innerHTML = outputHtml;
    }

    function clearResults() {
      document.getElementById('binaryInput').value = '';
      document.getElementById('shiftInput').value = '';
      document.getElementById('output').innerHTML = '';
    }
  </script>
</head>
<body>
  <h1>Binary Shifts Example</h1>

  <label for="binaryInput">Enter a binary number:</label>
  <input type="text" id="binaryInput" placeholder="Enter binary number">

  <label for="shiftInput">Enter the number of shifts:</label>
  <input type="number" id="shiftInput" placeholder="Enter shift amount">

  <button onclick="shiftBinary(true)">Left Shift</button>
  <button onclick="shiftBinary(false)">Right Shift</button>
  <button onclick="clearResults()">Clear</button>

  <div id="output"></div>
</body>
</html>
