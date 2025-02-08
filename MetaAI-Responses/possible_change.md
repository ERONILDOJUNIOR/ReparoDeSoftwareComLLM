Aqui está a correção do código Java:
```Java
package java_programs;

import java.util.Arrays;

public class POSSIBLE_CHANGE {

    /**
     * Calcula o número de maneiras possíveis de alcançar um total usando as moedas disponíveis.
     * 
     * @param coins  array de moedas disponíveis
     * @param total  total a ser alcançado
     * @return número de maneiras possíveis de alcançar o total
     */
    public static int possible_change(int[] coins, int total) {
        // Caso base: se o total for 0, há apenas 1 maneira de alcançá-lo (não usando nenhuma moeda)
        if (total == 0) {
            return 1;
        }
        
        // Caso base: se o total for negativo, não há maneira de alcançá-lo
        if (total < 0) {
            return 0;
        }
        
        // Se não houver mais moedas disponíveis, não há maneira de alcançar o total
        if (coins.length == 0) {
            return 0;
        }
        
        // Separa a primeira moeda do restante
        int first = coins[0];
        int[] rest = Arrays.copyOfRange(coins, 1, coins.length);
        
        // Recursão: calcula o número de maneiras de alcançar o total usando a primeira moeda e o restante
        return possible_change(coins, total - first) + possible_change(rest, total);
    }

    public static void main(String[] args) {
        int[] coins = {1, 2, 5};
        int total = 5;
        System.out.println("Número de maneiras possíveis de alcançar o total: " + possible_change(coins, total));
    }
}
```
Essa versão corrigida inclui:
Comentários para explicar o que cada parte do código faz.
Um caso base adicional para lidar com a situação em que não há mais moedas disponíveis.
Um método main para testar a função possible_change com um exemplo.
