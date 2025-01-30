Certainly, let's correct the Java code for the `possible_change` function.

```java
package java_programs;

import java.util.Arrays;

public class PossibleChange {

    public static int possible_change(int[] coins, int total) {
        if (total == 0) {
            return 1; // Base case: If the total is 0, there's only one way to make change (no coins)
        }
        if (total < 0) {
            return 0; // Base case: If the total is negative, there's no way to make change
        }

        int ways = 0; // Initialize ways to 0

        // Iterate through each coin
        for (int coin : coins) {
            ways += possible_change(coins, total - coin); 
        }

        return ways;
    }

    public static void main(String[] args) {
        int[] coins = {1, 2, 5};
        int total = 10;
        int numWays = possible_change(coins, total);
        System.out.println("Number of ways to make change: " + numWays); 
    }
}
```

**Explanation of Changes:**

1. **Corrected Recursive Logic:**
   - The original code incorrectly combined the results of two recursive calls:
      - `possible_change(coins, total-first)`: This considers using the first coin.
      - `possible_change(rest, total)`: This considers not using the first coin.
   - The correct approach is to iterate through each coin and recursively calculate the number of ways to make change using that coin.

2. **Initialization of `ways`:**
   - Introduced a variable `ways` to accumulate the number of ways to make change. It is initialized to 0.

3. **Iterating Through Coins:**
   - Added a `for` loop to iterate through each `coin` in the `coins` array.
   - In each iteration, the `ways` variable is incremented by the result of the recursive call `possible_change(coins, total - coin)`.

4. **Added `main` Method for Testing:**
   - Included a `main` method to demonstrate how to use the `possible_change` function with sample input.

This corrected code should accurately calculate the number of possible ways to make change using the given coins to reach the specified total.
