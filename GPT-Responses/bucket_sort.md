# Bucket Sort

O código fornecido tem alguns problemas que precisam ser corrigidos para implementar corretamente o algoritmo de Bucket Sort. O primeiro problema está relacionado à maneira como você está tentando contar os elementos e ordená-los. Aqui está uma versão corrigida do código:

O uso do `java
ArrayList<Integer> counts = new ArrayList<Integer>(Collections.nCopies(k, 0));`
está correto, mas é necessário garantir que o valor k seja o valor máximo do array + 1 para mapear corretamente os números.
No loop onde você percorre arr, você deveria estar iterando sobre counts, não sobre arr, pois arr já foi usado para fazer a contagem.
O tamanho do sorted_arr precisa ser dimensionado para o número total de elementos em arr, não apenas 100.
Aqui está o código corrigido:

```java
package java_programs;
import java.util.*;

public class BUCKETSORT {

    public static ArrayList<Integer> bucketsort(ArrayList<Integer> arr, int k) {
        // Cria o array de contagem com k posições, todas inicializadas com 0
        ArrayList<Integer> counts = new ArrayList<Integer>(Collections.nCopies(k, 0));

        // Preenche o array de contagem com as frequências de cada número
        for (Integer x : arr) {
            counts.set(x, counts.get(x) + 1);
        }

        // Lista que armazenará o array ordenado
        ArrayList<Integer> sorted_arr = new ArrayList<Integer>();

        // Para cada número (i), adiciona ao array ordenado o número de vezes que ele aparece
        for (int i = 0; i < counts.size(); i++) {
            // Adiciona i repetidamente, counts.get(i) vezes
            for (int j = 0; j < counts.get(i); j++) {
                sorted_arr.add(i);
            }
        }

        return sorted_arr;
    }

    public static void main(String[] args) {
        ArrayList<Integer> arr = new ArrayList<Integer>();
        arr.add(4);
        arr.add(2);
        arr.add(3);
        arr.add(1);
        arr.add(4);
        arr.add(2);
        arr.add(5);
        arr.add(3);

        // Encontrando o valor máximo para determinar k
        int k = Collections.max(arr) + 1;

        ArrayList<Integer> sortedArr = bucketsort(arr, k);
        System.out.println(sortedArr);
    }
}
```

Explicação das mudanças:
Criação do array de contagem (counts): A lista counts é inicializada para ter um número de elementos equivalente ao maior valor presente no array de entrada, mais 1. Isso é feito utilizando Collections.max(arr) + 1 para garantir que temos um índice válido para o maior valor de arr.

Contagem de ocorrências: Cada valor em arr aumenta a contagem correspondente no array counts.

Construção do array ordenado: Após contar as ocorrências de cada número, o código cria o array ordenado, onde cada número é repetido conforme a quantidade de vezes que aparece.

main(): Foi adicionado um método main() para testar o algoritmo, utilizando um conjunto de números e chamando o método bucketsort.

Esse código agora deve funcionar corretamente, ordenando os elementos da lista arr.
