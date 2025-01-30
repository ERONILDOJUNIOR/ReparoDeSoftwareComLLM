Certainly, let's correct the Java code you provided.

```java
package java_programs;

import java.util.*;

public class KTH {

    public static Integer kth(ArrayList<Integer> arr, int k) {
        if (arr.isEmpty()) {
            return null; // Handle empty array case
        }

        int pivotIndex = (int) (Math.random() * arr.size()); // Choose a random pivot index
        int pivot = arr.get(pivotIndex);

        // Swap pivot to the beginning for easier partitioning
        Collections.swap(arr, 0, pivotIndex);

        int left = 1;
        int right = arr.size() - 1;

        while (left <= right) {
            while (left <= right && arr.get(left) <= pivot) {
                left++;
            }
            while (left <= right && arr.get(right) > pivot) {
                right--;
            }
            if (left <= right) {
                Collections.swap(arr, left, right);
                left++;
                right--;
            }
        }

        // Place the pivot in its correct position
        Collections.swap(arr, 0, right);

        int numLess = right;

        if (k == numLess) {
            return pivot;
        } else if (k < numLess) {
            return kth(new ArrayList<>(arr.subList(0, numLess)), k); 
        } else {
            return kth(new ArrayList<>(arr.subList(numLess + 1, arr.size())), k - numLess - 1); 
        }
    }

    public static void main(String[] args) {
        ArrayList<Integer> arr = new ArrayList<>(Arrays.asList(3, 2, 1, 5, 4));
        int k = 2; 
        Integer kthSmallest = kth(arr, k);

        if (kthSmallest != null) {
            System.out.println("The " + k + "-th smallest element is: " + kthSmallest);
        } else {
            System.out.println("Array is empty.");
        }
    }
}
```

**Key improvements:**

* **Handles empty array:** Checks for an empty array at the beginning and returns `null` accordingly.
* **Random pivot selection:** Chooses a random pivot index for better average-case performance.
* **In-place partitioning:** Performs in-place partitioning of the array around the pivot using the classic "Lomuto partition scheme" for efficiency.
* **Optimized subarray creation:** Creates subarrays using `arr.subList()` for better memory management.
* **Corrected k value for recursive calls:** Adjusts the `k` value correctly for recursive calls on subarrays.
* **Added a `main` method:** Includes a `main` method to demonstrate how to use the `kth` function.

This improved code should now correctly find the k-th smallest element in an array using the Quickselect algorithm.

I hope this corrected version is helpful!
