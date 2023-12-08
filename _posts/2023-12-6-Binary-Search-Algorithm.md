---
toc: true
comments: false
layout: hack
title: Binary Search Algorithm
type: ccc
courses: { csp: {week: 14} }
---

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>{{ page.title }}</title>
    <script>
        // Define the binary_search function in JavaScript
        function binary_search(arr, target) {
            var low = 0, high = arr.length - 1;
            var steps = 0;

            while (low <= high) {
                steps++;
                var mid = Math.floor((low + high) / 2);

                if (arr[mid] === target) {
                    return { index: mid, steps: steps };
                } else if (arr[mid] < target) {
                    low = mid + 1;
                } else {
                    high = mid - 1;
                }
            }

            return { index: -1, steps: steps };
        }

        // Example usage
        document.addEventListener('DOMContentLoaded', function () {
            var sortedArray = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
            var targetValue = 7;
            var result = binary_search(sortedArray, targetValue);

            if (result.index !== -1) {
                alert("Target " + targetValue + " found at index " + result.index + " in " + result.steps + " steps.");
            } else {
                alert("Target " + targetValue + " not found in the array in " + result.steps + " steps.");
            }
        });
    </script>
</head>
<body>
    <!-- Your HTML content goes here -->
</body>
</html>
