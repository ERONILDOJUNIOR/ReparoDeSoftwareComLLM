Certainly, let's correct the provided Java code for binary search:

```java
package java_programs;

public class FIND_IN_SORTED {

    public static int binarySearch(int[] arr, int x, int start, int end) {
        if (start > end) { 
            return -1; 
        } 
        int mid = start + (end - start) / 2; 
        if (x < arr[mid]) {
            return binarySearch(arr, x, start, mid - 1); 
        } else if (x > arr[mid]) {
            return binarySearch(arr, x, mid + 1, end); 
        } else {
            return mid;
        }
    }

    public static int findInSorted(int[] arr, int x) {
        return binarySearch(arr, x, 0, arr.length - 1); 
    }

    public static void main(String[] args) {
        int[] arr = {2, 3, 4, 10, 40};
        int x = 10;
        int result = findInSorted(arr, x);
        if (result == -1)
            System.out.println("Element is not present in array");
        else
            System.out.println("Element is present at index " + result);
    }
}
```

Here are the corrections made:

1. **Base Case:** In the `binarySearch` function, the base case should be `start > end`. If `start` becomes greater than `end`, it means the element is not found in the array.

2. **Recursive Calls:**
   - When `x < arr[mid]`, the recursive call should be `binarySearch(arr, x, start, mid - 1)`.
   - When `x > arr[mid]`, the recursive call should be `binarySearch(arr, x, mid + 1, end)`.

3. **`findInSorted` Function:** The initial call to `binarySearch` should use `arr.length - 1` as the `end` index, as array indices are zero-based.

4. **Main Function:** A `main` function is added to demonstrate the usage of the `findInSorted` function.

This corrected code should now perform binary search correctly on a sorted array.
