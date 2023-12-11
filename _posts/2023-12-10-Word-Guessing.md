---
toc: true
comments: true
layout: hack
title: Binary Word Guessing
type: ccc
courses: { csp: {week: 15} }
---

<html>
<head>
    <title>Binary Word Guessing Game</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #000;
            color: #0f0;
            padding: 30px;
        }
        h1 {
            font-weight: bold;
            text-shadow: 0 0 1px #0f0, 0 0 20px #0f0, 0 0 30px #0f0, 0 0 40px #0f0;
        }
        #binaryWord {
            font-weight: bold;
            margin-bottom: 10px;
            font-size: 20px;
        }
        #guess {
            margin-bottom: 10px;
            padding: 10px;
            font-size: 16px;
            border-radius: 5px;
            border: 1px solid #0f0;
            background-color: #000;
            color: #0f0;
        }
        #submit {
            padding: 10px 20px;
            font-size: 16px;
            border-radius: 5px;
            border: none;
            color: #000;
            background-color: #0f0;
            cursor: pointer;
        }
        #submit:hover {
            background-color: #1a1;
        }
        #result {
            margin-top: 20px;
            font-size: 18px;
        }
    </style>
</head>
<body>
    <h1>Binary Word Guessing Game</h1>
    <p>Guess the word represented by the binary code:</p>
    <p id="binaryWord"></p>
    <input type="text" id="guess" placeholder="Your guess here">
    <button id="submit">Submit</button>
    <p id="result"></p>

    <script>
        // Word bank
        const wordBank = ['apple', 'banana', 'cherry', 'date', 'elderberry'];

        // Function to convert a string to binary
        function stringToBinary(str) {
            return str.split('').map(function (char) {
                return char.charCodeAt(0).toString(2);
            }).join(' ');
        }

        // Convert word bank to binary
        const binaryWordBank = wordBank.map(word => stringToBinary(word));

        // Randomly select a word
        const randomIndex = Math.floor(Math.random() * binaryWordBank.length);
        const randomBinaryWord = binaryWordBank[randomIndex];

        // Display binary word
        document.getElementById('binaryWord').textContent = randomBinaryWord;

        // Handle submit button click
        document.getElementById('submit').addEventListener('click', function() {
            // Get user's guess
            const userGuess = document.getElementById('guess').value;

            // Check if the user's guess is correct
            if (userGuess === wordBank[randomIndex]) {
                document.getElementById('result').textContent = 'Correct!';
            } else {
                document.getElementById('result').textContent = `Incorrect. The correct word was ${wordBank[randomIndex]}`;
            }
        });
    </script>
</body>
</html>