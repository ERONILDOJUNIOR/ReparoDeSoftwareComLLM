Aqui está o código corrigido:
Java
package java_programs;

import java.util.Arrays;

public class FIND_FIRST_IN_SORTED {

    /**
     * Encontra a primeira ocorrência de um elemento em um array ordenado.
     * 
     * @param arr O array ordenado.
     * @param x   O elemento a ser encontrado.
     * @return O índice da primeira ocorrência de x em arr, ou -1 se x não estiver presente.
     */
    public static int findFirstInSorted(int[] arr, int x) {
        int lo = 0;
        int hi = arr.length - 1; // Correção: hi deve ser o último índice do array
        while (lo <= hi) {
            int mid = (lo + hi) / 2;
            if (x == arr[mid] && (mid == 0 || x != arr[mid - 1])) {
                return mid;
            } else if (x < arr[mid]) { // Correção: x < arr[mid] em vez de x <= arr[mid]
                hi = mid - 1; // Correção: hi = mid - 1 em vez de hi = mid
            } else {
                lo = mid + 1;
            }
        }
        return -1;
    }

    public static void main(String[] args) {
        int[] arr = {1, 2, 2, 3, 4, 5};
        Arrays.sort(arr); // Garantir que o array esteja ordenado
        int x = 2;
        int result = findFirstInSorted(arr, x);
        System.out.println("A primeira ocorrência de " + x + " está no índice " + result);
    }
}
