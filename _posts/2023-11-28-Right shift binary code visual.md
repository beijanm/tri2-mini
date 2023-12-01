---
toc: true
comments: true
layout: hack
title: Left/Right Shift Binary Code Visual 
type: ccc
courses: { csp: {week: 14} }
---

<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Binary Shifts Example</title>
  <style>
    body { font-family: Arial, sans-serif; background-color: #f4f4f4; color: #333; }
    .container { max-width: 600px; margin: auto; padding: 20px; }
    label, input, button { display: block; width: 100%; padding: 10px; margin: 10px 0; }
    button { background-color: #007bff; color: white; border: none; cursor: pointer; }
    button:hover { background-color: #0056b3; }
    #output {
      background-color: #erd;
      border: 1px solid #ddd;
      padding: 10px;
      display: none; /* Hide when empty */
    }
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
      const outputDiv = document.getElementById('output');
      outputDiv.innerHTML = outputHtml;
      outputDiv.style.display = 'block'; // Show the output div when it has content
    }

    function clearResults() {
      document.getElementById('binaryInput').value = '';
      document.getElementById('shiftInput').value = '';
      const outputDiv = document.getElementById('output');
      outputDiv.innerHTML = '';
      outputDiv.style.display = 'none'; // Hide the output div when cleared
    }
  </script>
</head>
<body>
  <div class="container">
    <h1>Binary Shifts Example</h1>

    <label for="binaryInput">Enter a binary number:</label>
    <input type="text" id="binaryInput" placeholder="Enter binary number" aria-label="Binary Input">

    <label for="shiftInput">Enter the number of shifts:</label>
    <input type="number" id="shiftInput" placeholder="Enter shift amount" aria-label="Shift Amount">

    <button onclick="shiftBinary(true)">Left Shift</button>
    <button onclick="shiftBinary(false)">Right Shift</button>
    <button onclick="clearResults()">Clear</button>

    <div id="output"></div>
  </div>
</body>
</html>

