---
title: Digital Clock
layout: default
courses: { csp: {week: 14} }
type: ccc
---

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <style>
    body {
      font-family: 'Arial', sans-serif;
      text-align: center;
      background-color: #f4f4f4;
      margin: 0;
      display: flex;
      align-items: center;
      justify-content: center;
      height: 100vh;
    }

    #game-container {
      padding: 20px;
      background-color: #fff;
      box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
      border-radius: 8px;
      width: 300px;
    }

    h2 {
      color: #333;
    }

    #binary-display {
      font-size: 24px;
      margin: 20px 0;
      color: #333;
    }

    #input-box {
      font-size: 16px;
      padding: 10px;
      width: 80%;
      margin-bottom: 20px;
      box-sizing: border-box;
    }

    #submit-btn {
      font-size: 16px;
      padding: 10px;
      cursor: pointer;
      background-color: #4caf50;
      color: #fff;
      border: none;
      border-radius: 4px;
    }

    #feedback {
      margin-top: 10px;
      font-weight: bold;
      color: #4caf50;
    }
  </style>
  <script>
    function generateBinary() {
      const binaryNumber = Math.floor(Math.random() * 256).toString(2);
      document.getElementById('binary-display').textContent = binaryNumber;
      document.getElementById('feedback').textContent = ''; // Clear previous feedback
      document.getElementById('input-box').value = ''; // Clear the input box
    }

    function checkGuess() {
      const binaryDisplay = document.getElementById('binary-display').textContent;
      const userGuess = document.getElementById('input-box').value;

      if (binaryDisplay === userGuess) {
        document.getElementById('feedback').textContent = 'Correct! Well done.';
      } else {
        document.getElementById('feedback').textContent = 'Incorrect. Try again.';
      }

      // Regenerate a new binary number for the next round
      generateBinary();
    }
  </script>
</head>
<body>
  <div id="game-container">
    <h2>Binary Number Game</h2>
    <p>Convert the binary number to decimal:</p>
    <div id="binary-display"></div>
    <input type="text" id="input-box" placeholder="Your guess">
    <br>
    <button id="submit-btn" onclick="checkGuess()">Submit</button>
    <div id="feedback"></div>
  </div>

  <script>
    // Initialize the game by generating the first binary number
    generateBinary();
  </script>
</body>
</html>

