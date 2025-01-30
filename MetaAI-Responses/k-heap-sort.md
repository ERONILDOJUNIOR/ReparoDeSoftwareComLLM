Aqui está o código corrigido:
Java
package java_programs;

import java.util.ArrayList;
import java.util.PriorityQueue;

public class KHeapSort {

    /**
     * Implementação do algoritmo K-HeapSort.
     * 
     * @param arr ArrayList de números inteiros a serem ordenados.
     * @param k    Tamanho do heap.
     * @return ArrayList ordenado.
     */
    public static ArrayList<Integer> kheapsort(ArrayList<Integer> arr, int k) {
        // Verifica se o tamanho do heap é válido
        if (k < 1) {
            throw new IllegalArgumentException("O tamanho do heap deve ser maior que 0");
        }

        // Cria um heap com os primeiros k elementos do array
        PriorityQueue<Integer> heap = new PriorityQueue<>();
        for (int i = 0; i < Math.min(k, arr.size()); i++) {
            heap.add(arr.get(i));
        }

        // Cria um array para armazenar a saída
        ArrayList<Integer> output = new ArrayList<>();

        // Percorre o array original, adicionando elementos ao heap e removendo o menor elemento
        for (int i = k; i < arr.size(); i++) {
            heap.add(arr.get(i));
            output.add(heap.poll());
        }

        // Adiciona os elementos restantes do heap à saída
        while (!heap.isEmpty()) {
            output.add(heap.poll());
        }

        return output;
    }

    public static void main(String[] args) {
        ArrayList<Integer> arr = new ArrayList<>(Arrays.asList(5, 2, 8, 1, 9));
        int k = 3;
        ArrayList<Integer> sortedArr = kheapsort(arr, k);
        System.out.println("Array ordenado: " + sortedArr);
    }
}
As principais alterações incluem:
Adição de uma verificação para garantir que o tamanho do heap seja maior que 0.
Uso de Math.min(k, arr.size()) para evitar um IndexOutOfBoundsException ao criar o heap.
Inclusão de um exemplo de uso no método main.
Melhorias na documentação e no formato do código para maior clareza e legibilidade.
