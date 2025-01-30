Segue abaixo o código corrigido:
Java
package java_programs;

import java.util.ArrayList;

public class KTH {
    /**
     *Retorna o k-ésimo menor elemento em uma lista.
     *
     *@param arr Lista de números inteiros.
     * @param k    Índice do elemento desejado (1-indexado).
     *@return O k-ésimo menor elemento na lista, ou null se a lista for vazia.
     */
    public static Integer kth(ArrayList<Integer> arr, int k) {
        if (arr.isEmpty() || k < 1 || k > arr.size()) {
            return null; // Caso de erro: lista vazia ou k inválido
        }

        int pivot = arr.get(0);
        ArrayList<Integer> below = new ArrayList<>(arr.size());
        ArrayList<Integer> above = new ArrayList<>(arr.size());

        for (Integer x : arr) {
            if (x < pivot) {
                below.add(x);
            } else if (x > pivot) {
                above.add(x);
            }
        }

        int numLess = below.size();
        int numLessOrEq = arr.size() - above.size();

        if (k <= numLess) {
            return kth(below, k);
        } else if (k > numLessOrEq) {
            return kth(above, k - numLessOrEq);
        } else {
            return pivot;
        }
    }

    public static void main(String[] args) {
        ArrayList<Integer> arr = new ArrayList<>();
        arr.add(5);
        arr.add(2);
        arr.add(8);
        arr.add(1);
        arr.add(9);

        int k = 3;
        Integer result = kth(arr, k);

        System.out.println("O " + k + "º menor elemento é: " + result);
    }
}
As principais correções incluem:
Adição de verificação de erro para lidar com casos em que a lista está vazia ou k é inválido.
Correção na lógica de recursão para calcular o k-ésimo menor elemento.
Inclusão de um exemplo de uso no método main para demonstrar a funcionalidade do método kth.
