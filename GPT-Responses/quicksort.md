O código que você forneceu para o algoritmo Quicksort em Java contém alguns erros de lógica. O problema principal é a forma como os elementos são combinados ao final do processo recursivo. O código atualmente coloca `greater` antes de `middle` e depois adiciona o resultado de `lesser` no final, o que não está correto.

Aqui está o código corrigido:

```java
package java_programs;
import java.util.*;

public class QUICKSORT {
    public static ArrayList<Integer> quicksort(ArrayList<Integer> arr) {
        // Caso base: se o array estiver vazio ou tiver apenas um elemento, já está ordenado
        if (arr.size() <= 1) {
            return arr;
        }

        Integer pivot = arr.get(0); // Usando o primeiro elemento como pivô
        ArrayList<Integer> lesser = new ArrayList<Integer>();  // Elementos menores que o pivô
        ArrayList<Integer> greater = new ArrayList<Integer>(); // Elementos maiores que o pivô

        // Dividindo os elementos em menores e maiores que o pivô
        for (Integer x : arr.subList(1, arr.size())) {
            if (x < pivot) {
                lesser.add(x);
            } else if (x > pivot) {
                greater.add(x);
            }
        }

        // Recursivamente ordenando as sublistas
        lesser = quicksort(lesser);
        greater = quicksort(greater);

        // Combinando os resultados: menor + pivô + maior
        ArrayList<Integer> result = new ArrayList<Integer>();
        result.addAll(lesser);
        result.add(pivot);
        result.addAll(greater);

        return result;
    }

    public static void main(String[] args) {
        ArrayList<Integer> list = new ArrayList<>(Arrays.asList(5, 2, 9, 1, 5, 6));
        System.out.println("Original: " + list);
        ArrayList<Integer> sortedList = quicksort(list);
        System.out.println("Sorted: " + sortedList);
    }
}
```

**Principais correções:**
1. **Caso base da recursão:** Agora o código verifica se a lista tem tamanho 1 ou 0 e retorna a lista como está, o que é o comportamento esperado para listas pequenas.
2. **Combinação final dos sublistas:** Depois de ordenar as sublistas `lesser` e `greater`, a lista final é formada pela concatenação de `lesser`, o `pivot`, e `greater`.
3. **Função `main` adicionada:** Para testar o código, adicionei um exemplo de entrada para exibir a lista original e a lista ordenada após a execução do `quicksort`.

Isso agora deve funcionar corretamente!