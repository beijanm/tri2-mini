---
toc: true
comments: false
layout: post
title: Left Shift Binary
description: Starting off the second trimester strong!
type: tangibles
courses: { compsci: {week: 1} }
---

def left_shift_binary(number, shifts):
    results = []
    for _ in range(shifts):
        number = number << 1
        results.append(number)
    return results
# Example usage:
binary_number = 0b1101  # Binary literal for 13
shift_amount = 5
shifted_results = left_shift_binary(binary_number, shift_amount)
print(f"Initial binary number: {binary_number:b}")
for i, result in enumerate(shifted_results, 1):
    print(f"Left-shift {i} times: {result:b}")