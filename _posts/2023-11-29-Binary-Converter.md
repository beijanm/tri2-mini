---
toc: true
comments: true
layout: hack
title: Binary converter
type: ccc
courses: { csp: {week: 14} }
---

<html>
<head>
    <!-- Title of the Webpage -->
    <title>Binary Operations</title>
</head>
<body>
    <!-- Heading of the Webpage -->
    <h2>Binary Conversion and Operations</h2>

    <!-- Input field for binary number -->
    <input type="text" id="inputBinary" placeholder="Enter Binary Number">

    <!-- Button to trigger operations -->
    <button onclick="performOperations()">Perform Operations</button>

    <!-- Div to display the results of operations -->
    <div id="output"></div>

    <script>
        // Function to convert binary to decimal
        function binaryToDecimal(binaryStr) {
            return parseInt(binaryStr, 2);
        }

        // Function to convert decimal to binary
        function decimalToBinary(decimalInt) {
            return decimalInt.toString(2);
        }

        // Function to perform bitwise AND operation
        function bitwiseAnd(binStr1, binStr2) {
            return (parseInt(binStr1, 2) & parseInt(binStr2, 2)).toString(2);
        }

        // Function to perform bitwise OR operation
        function bitwiseOr(binStr1, binStr2) {
            return (parseInt(binStr1, 2) | parseInt(binStr2, 2)).toString(2);
        }

        // Function to perform bitwise XOR operation
        function bitwiseXor(binStr1, binStr2) {
            return (parseInt(binStr1, 2) ^ parseInt(binStr2, 2)).toString(2);
        }

        // Function to perform bitwise NOT operation
        function bitwiseNot(binStr) {
            let num = parseInt(binStr, 2);
            let numOfBits = binStr.length;
            return (~num & (Math.pow(2, numOfBits) - 1)).toString(2);
        }

        // Function to perform left shift operation
        function leftShift(binStr, shifts) {
            return (parseInt(binStr, 2) << shifts).toString(2);
        }

        // Function to perform right shift operation
        function rightShift(binStr, shifts) {
            return (parseInt(binStr, 2) >> shifts).toString(2);
        }

        // Function to handle the UI interaction and display results
        function performOperations() {
            let binaryNumber = document.getElementById('inputBinary').value;
            let output = `
                <p>Decimal: ${binaryToDecimal(binaryNumber)}</p>
                <p>Binary: ${decimalToBinary(binaryNumber)}</p>
                <p>Bitwise AND (with 1010): ${bitwiseAnd(binaryNumber, "1010")}</p>
                <p>Bitwise OR (with 1010): ${bitwiseOr(binaryNumber, "1010")}</p>
                <p>Bitwise XOR (with 1010): ${bitwiseXor(binaryNumber, "1010")}</p>
                <p>Bitwise NOT: ${bitwiseNot(binaryNumber)}</p>
                <p>Left Shift (2 bits): ${leftShift(binaryNumber, 2)}</p>
                <p>Right Shift (2 bits): ${rightShift(binaryNumber, 2)}</p>
            `;
            document.getElementById('output').innerHTML = output;
        }
    </script>
</body>
</html>
