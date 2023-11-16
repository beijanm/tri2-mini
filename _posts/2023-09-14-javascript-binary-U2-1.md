---
title: 2.1 Binary
layout: default
description: A Binary Math illustrative application using HTML, Liquid, and JavaScript.
courses: { csp: {week: 5, categories: [3.B, 3.C]} }
categories: [C4.4]
type: ccc
---

<!-- 

Learn how page works, plus learu about binary
Hack 0: Do your own on/off thing with Image and Buttons thing
Hack 1: change diplay to indicate value of bin (128, 64, 32, 16, 8, 4, 2, 1)
Hack 2: change one-zero input under bulb to perform updates to page

Learn about binary representations
Hack 3: add a ASCII character display to text when 8 bits, determine if printable or not printable
Hack 4: change to 24 bits and add a color code and display color when 24 bits. Think about display on this one, perhaps wrap bits 

Jekyll Table Reference: https://idratherbewriting.com/documentation-theme-jekyll/mydoc_tables.html

--->

<!DOCTYPE html>
<html>
<head>
    <style>
        td {
            text-align: center;
            vertical-align: middle;
        }
    </style>
</head>
<body>

<table>
    <thead>
        <tr class="header" id="table">
            <th>Plus</th>
            <th>Binary</th>
            <th>Octal</th>
            <th>Hexadecimal</th>
            <th>Decimal</th>
            <th>Minus</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><div class="button" id="add1" onclick="add(1)">+1</div></td>
            <td id="binary">00000000</td>
            <td id="octal">0</td>
            <td id="hexadecimal">0</td>
            <td id="decimal">0</td>
            <td><div class="button" id="sub1" onclick="add(-1)">-1</div></td>
        </tr>
    </tbody>
</table>

<table>
    <thead>
        <tr>
            <!-- Dynamically generate table headers with JavaScript -->
        </tr>
    </thead>
    <tbody>
        <tr>
            <!-- Dynamically generate table body with JavaScript -->
        </tr>
    </tbody>
</table>

<script>
    const BITS = 8;
    const MAX = 2 ** BITS - 1;
    const MSG_ON = "Turn on";
    const IMAGE_ON = "path_to_your_on_image"; // Replace with your image path
    const MSG_OFF = "Turn off";
    const IMAGE_OFF = "path_to_your_off_image"; // Replace with your image path

    // Function to create table headers and body
    function createTable() {
        let headerRow = document.querySelector('thead tr');
        let bodyRow = document.querySelector('tbody tr');
        for (let i = 0; i < BITS; i++) {
            let th = document.createElement('th');
            th.innerHTML = `<img id="bulb${i}" src="${IMAGE_OFF}" alt="" width="40" height="Auto">
                            <div class="button" id="butt${i}" onclick="toggleBit(${i})">Turn on</div>`;
            headerRow.appendChild(th);

            let td = document.createElement('td');
            td.innerHTML = `<input type='text' id="digit${i}" Value="0" size="1" readonly>`;
            bodyRow.appendChild(td);
        }
    }

    // Rest of your JavaScript functions remain the same...

    // Call function to create table on load
    createTable();
</script>

</body>
</html>

