Certainly, let's correct the Java code for the Sieve of Eratosthenes:

```java
package java_programs;

import java.util.*;

public class Sieve {

    public static boolean all(ArrayList<Boolean> arr) {
        for (boolean value : arr) {
            if (!value) {
                return false;
            }
        }
        return true;
    }

    public static boolean any(ArrayList<Boolean> arr) {
        for (boolean value : arr) {
            if (value) {
                return true;
            }
        }
        return false;
    }

    public static ArrayList<Boolean> list_comp(int n, ArrayList<Integer> primes) {
        ArrayList<Boolean> built_comprehension = new ArrayList<>(); 
        for (Integer p : primes) {
            built_comprehension.add(n % p == 0); // Corrected condition
        }
        return built_comprehension;
    }

    public static ArrayList<Integer> sieve(Integer max) {
        ArrayList<Integer> primes = new ArrayList<>();
        for (int n = 2; n <= max; n++) { // Corrected loop condition
            if (all(list_comp(n, primes))) { // Corrected condition
                primes.add(n);
            }
        }
        return primes;
    }

    public static void main(String[] args) {
        int max = 100;
        ArrayList<Integer> primes = sieve(max);
        System.out.println("Prime numbers up to " + max + ": " + primes);
    }
}
```

Here are the corrections made:

* **`list_comp` method:**
  * The condition `n % p > 0` was incorrect. It should be `n % p == 0` to check if `n` is divisible by `p`.

* **`sieve` method:**
  * The loop condition should be `n <= max` to include the number `max` itself in the check.
  * The condition `any(list_comp(n, primes))` was incorrect. It should be `all(list_comp(n, primes))` because a number is prime if it's not divisible by any of the previously found primes.

* **Added `main` method:**
  * A `main` method has been added to demonstrate how to use the `sieve` method and print the results.

This corrected code should now correctly generate a list of prime numbers up to the given `max` value.
