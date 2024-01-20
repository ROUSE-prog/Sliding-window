There are many algorithms that come up frequently in coding interviews, with Sliding Windows being one of the most popular.



Basic Concept: The sliding window algorithm involves moving a window of fixed size over a data structure (like an array or string) to process a subset of its elements at any given time.

Use Cases: Sliding window algorithms are widely used in various domains, including string manipulation (e.g., finding substrings), array processing (e.g., finding maximum sum of subarrays of a given size). 

Window Size: The size of the window is predefined and remains constant throughout the operation. It determines the number of elements processed at each step.

Moving the Window: The window slides one element at a time from left to right (or in a specified direction) across the data structure. At each step, a new element enters the window from one end, and an old element exits from the other end.

Processing Elements: Within each window, a specific operation or a set of operations is performed. This could include calculations like finding the sum, average, minimum, or maximum, or applying a filter or a pattern matching.

function fixedSlidingWindow(arr, k) {
  // Sum up the first subarray and add it to the result
  let currSubarray = arr.slice(0, k).reduce((a, b) => a + b, 0);
  let result = [currSubarray];

  // To get each subsequent subarray, add the next value in the array and remove the first value
  for (let i = 1; i <= arr.length - k; i++) {
    currSubarray = currSubarray - arr[i - 1];
    currSubarray = currSubarray + arr[i + k - 1];
    result.push(currSubarray);
  }

  return result;
}
