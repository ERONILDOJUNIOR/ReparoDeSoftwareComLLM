# BitCount

O código que você forneceu possui um erro lógico na implementação do método bitcount. O código atualmente tenta contar o número de bits '1' em um número utilizando uma abordagem incorreta com o operador XOR (^). O correto é iterar pelos bits do número e contar quantos são 1. Aqui está uma versão corrigida do código:

```java
package java_programs;

public class BITCOUNT {
    public static int bitcount(int n) {
        int count = 0;
        while (n != 0) {
            // Remove o bit mais à direita que é 1
            n = n & (n - 1);
            count++;
        }
        return count;
    }

    public static void main(String[] args) {
        // Testando o método com alguns valores
        System.out.println(bitcount(9));  // Exemplo: 9 em binário é 1001, tem 2 bits 1
        System.out.println(bitcount(15)); // Exemplo: 15 em binário é 1111, tem 4 bits 1
    }
}
```

Explicação:
O operador n & (n - 1) é uma maneira eficiente de apagar o bit mais à direita que é 1 no número n.
Isso é feito repetidamente até que n seja zero, e a variável count é incrementada a cada iteração para contar os bits '1'.
O código agora deve funcionar corretamente para contar o número de bits 1 em um número.
