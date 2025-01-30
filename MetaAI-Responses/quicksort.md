Aqui está o código corrigido:
Java
package java_programs;

import java.util.ArrayList;

public class QuickSort {

    public static ArrayList<Integer> quickSort(ArrayList<Integer> arr) {
        if (arr.size() <= 1) {
            return arr;
        }

        Integer pivot = arr.get(0);
        ArrayList<Integer> lesser = new ArrayList<>();
        ArrayList<Integer> greater = new ArrayList<>();

        for (Integer x : arr.subList(1, arr.size())) {
            if (x <= pivot) {
                lesser.add(x);
            } else {
                greater.add(x);
            }
        }

        lesser = quickSort(lesser);
        greater = quickSort(greater);

        ArrayList<Integer> result = new ArrayList<>();
        result.addAll(lesser);
        result.add(pivot);
        result.addAll(greater);

        return result;
    }

    public static void main(String[] args) {
        ArrayList<Integer> arr = new ArrayList<>();
        arr.add(5);
        arr.add(2);
        arr.add(9);
        arr.add(1);
        arr.add(7);

        System.out.println("Array original: " + arr);
        System.out.println("Array ordenado: " + quickSort(arr));
    }
}
As principais mudanças foram:
Renomeei a classe para QuickSort para seguir as convenções de nomenclatura Java.
Mudei a condição de parada do algoritmo para arr.size() <= 1, pois um array com um elemento já está ordenado.
Criei um novo array result para armazenar o resultado final, em vez de modificar os arrays lesser e greater.
Adicionei um método main para testar o algoritmo com um exemplo.
