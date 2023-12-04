---
title: Num Game
layout: default
courses: { csp: {week: 14} }
type: ccc
---

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Binary to Decimal Guessing Game</title>
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
            background-color: #000000;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            border-radius: 8px;
            width: 300px;
        }

        .game-element {
            margin: 10px 0;
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
</head>
<body>
    <div id="game-container">
        <h2>Binary to Decimal Guessing Game</h2>
        <div class="game-element" id="binary-number"></div>
        <input class="game-element" type="number" id="user-guess" placeholder="Enter decimal number">
        <button class="game-element" id="submit-btn" onclick="checkGuess()">Guess</button>
        <div class="game-element" id="feedback"></div>
    </div>

    <script>
        function generateBinaryNumber() {
            const binaryNumber = Math.floor(Math.random() * 256).toString(2);
            document.getElementById('binary-number').textContent = `Guess the decimal value of ${binaryNumber}`;
            return binaryNumber;
        }

        let correctDecimalValue = parseInt(generateBinaryNumber(), 2);

        function checkGuess() {
            const userGuess = parseInt(document.getElementById('user-guess').value);
            if (userGuess === correctDecimalValue) {
                document.getElementById('feedback').textContent = 'Correct! Well done.';
            } else {
                document.getElementById('feedback').textContent = `Incorrect. The correct answer was ${correctDecimalValue}.`;
            }
            correctDecimalValue = parseInt(generateBinaryNumber(), 2);
        }
    </script>
</body>
</html>
