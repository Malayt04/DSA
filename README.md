# DSA

## Maximum Subarray Sum

```
class Solution {

    int maxSubarraySum(int[] arr) {

        int res = Integer.MIN_VALUE;
        int maxEnding = 0;
        
        for(int i =0; i < arr.length; i++){
            maxEnding = Math.max(maxEnding + arr[i], arr[i]);
            res = Math.max(res, maxEnding);
        }
        
        return res;
    }
}
```

## Missing number in an array

```
class Solution {
    // Note that the size of the array is n-1
    int missingNumber(int n, int arr[]) {
        
        int sum = 0;
        int naturalSum = (n * (n + 1))/2;

        for(int i =0; i < n - 1; i++){
            sum = sum + arr[i];
        }
        return naturalSum - sum;
    }
}
```

## Trapping Rainwater

```

class Solution {

    // arr: input array
    // n: size of array
    // Function to find the trapped water between the blocks.
    static long trappingWater(int arr[]) {
        int n = arr.length;

        // If there are less than 3 bars, no water can be trapped
        if (n < 3) {
            return 0;
        }

        long left[] = new long[n];
        long right[] = new long[n];

        // Initialize result
        long water = 0;

        // Fill left array
        left[0] = arr[0];
        for (int i = 1; i < n; i++) {
            left[i] = Math.max(left[i - 1], arr[i]);
        }

        // Fill right array
        right[n - 1] = arr[n - 1];
        for (int i = n - 2; i >= 0; i--) {
            right[i] = Math.max(right[i + 1], arr[i]);
        }

        // Calculate the accumulated water element by element
        for (int i = 0; i < n; i++) {
            water += Math.min(left[i], right[i]) - arr[i];
        }

        return water;
    }
}

```
