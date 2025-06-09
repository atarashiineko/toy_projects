---
id: dev.leetcode.literate-leetcode.example.3sum.v000
title: Literate 3Sum Example
description: Demonstrates solving the 3Sum problem using literate functions
tags:
- coding
- leetcode
created_date: 2025-05-03
updated_date: 2025-05-03
version: 0
---

## Prompt
Implement the Leetcode "3Sum" problem. Given an array of integers, return all unique triplets `[a, b, c]` such that `a + b + c = 0`. Apply the literate style described in `2025-05-03_literate-leetcode.v000.md` and respond only with the final code block.

## Parameters
This prompt has no parameters.

## Usage Example
**Input**
User: "Generate a literate solution for the 3Sum problem in JavaScript."

**Expected Output**
```javascript
/** Finds every unique triplet of numbers that sums to zero. */
function threeSum(nums) {
  const sorted = ascendingCopyOf(nums);
  const triplets = newTripletList();
  forEachIndex(sorted, index => {
    if (shouldSkipIndex(sorted, index)) {
      return;
    }
    searchPairsFromIndex(sorted, index, triplets);
  });
  return triplets;
}

/** Produces a sorted copy of the numbers. */
function ascendingCopyOf(numbers) {
  return [...numbers].sort((a, b) => a - b);
}

/** Returns an empty list for the resulting triplets. */
function newTripletList() {
  return [];
}

/** Runs a callback for every starting index. */
function forEachIndex(array, callback) {
  for (let i = 0; i < array.length - 2; i++) {
    callback(i);
  }
}

/** Determines if the current index should be skipped. */
function shouldSkipIndex(array, index) {
  return index > 0 && array[index] === array[index - 1];
}

/** Looks for valid pairs using two pointers. */
function searchPairsFromIndex(array, index, triplets) {
  let left = index + 1;
  let right = array.length - 1;
  while (left < right) {
    const sum = sumOfThree(array[index], array[left], array[right]);
    if (isZero(sum)) {
      appendTriplet(triplets, array[index], array[left], array[right]);
      left = increment(left);
      right = decrement(right);
      left = skipDuplicatesOnLeft(array, left, right);
      right = skipDuplicatesOnRight(array, left, right);
    } else if (sum < 0) {
      left = increment(left);
    } else {
      right = decrement(right);
    }
  }
}

/** Returns the sum of three numbers. */
function sumOfThree(a, b, c) {
  return a + b + c;
}

/** Checks if a value is exactly zero. */
function isZero(value) {
  return value === 0;
}

/** Adds a triplet to the list of results. */
function appendTriplet(list, a, b, c) {
  list.push([a, b, c]);
}

/** Increments a numeric index. */
function increment(value) {
  return value + 1;
}

/** Decrements a numeric index. */
function decrement(value) {
  return value - 1;
}

/** Skips duplicate values while moving the left pointer. */
function skipDuplicatesOnLeft(array, left, right) {
  while (left < right && areEqual(array[left], array[left - 1])) {
    left = increment(left);
  }
  return left;
}

/** Skips duplicate values while moving the right pointer. */
function skipDuplicatesOnRight(array, left, right) {
  while (left < right && areEqual(array[right], array[right + 1])) {
    right = decrement(right);
  }
  return right;
}

/** Determines if two numbers are equal. */
function areEqual(a, b) {
  return a === b;
}
```

## Notes
The function `threeSum` begins by copying and sorting the input array so that two-pointer scanning works reliably. It iterates over every possible starting index, skipping duplicates to avoid repeated triplets. For each index it runs a search with two pointers (`left` and `right`) that moves inward until all combinations are checked. Helpers like `sumOfThree`, `isZero`, and `appendTriplet` break down the logic into very small, descriptive operations. Duplicate values are skipped using `skipDuplicatesOnLeft` and `skipDuplicatesOnRight` so each triplet appears only once.
