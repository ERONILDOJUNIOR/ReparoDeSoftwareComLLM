Aqui está o código Java corrigido:
Java
package java_programs;

import java.util.ArrayList;

public class Sieve {
    /**
     *Verifica se todos os elementos de um ArrayList são verdadeiros.
     *
     *@param arr ArrayList de booleanos
     * @return true se todos os elementos forem verdadeiros, false caso contrário
     */
    public static boolean all(ArrayList<Boolean> arr) {
        for (boolean value : arr) {
            if (!value) {
                return false;
            }
        }
        return true;
    }

    /**
     * Verifica se pelo menos um elemento de um ArrayList é verdadeiro.
     * 
     * @param arr ArrayList de booleanos
     * @return true se pelo menos um elemento for verdadeiro, false caso contrário
     */
    public static boolean any(ArrayList<Boolean> arr) {
        for (boolean value : arr) {
            if (value) {
                return true;
            }
        }
        return false;
    }

    /**
     * Cria um ArrayList de booleanos representando se um número é divisível por cada primo.
     * 
     * @param n     número a ser verificado
     * @param primes ArrayList de primos
     * @return ArrayList de booleanos
     */
    public static ArrayList<Boolean> listComp(int n, ArrayList<Integer> primes) {
        ArrayList<Boolean> builtComprehension = new ArrayList<>();
        for (Integer p : primes) {
            builtComprehension.add(n % p > 0);
        }
        return builtComprehension;
    }

    /**
     * Implementação do Algoritmo de Sieve of Eratosthenes para encontrar primos até um máximo.
     * 
     * @param max máximo valor a ser verificado
     * @return ArrayList de primos
     */
    public static ArrayList<Integer> sieve(int max) {
        ArrayList<Integer> primes = new ArrayList<>();
        for (int n = 2; n <= max; n++) {
            if (all(listComp(n, primes))) {
                primes.add(n);
            }
        }
        return primes;
    }

    public static void main(String[] args) {
        int max = 30;
        ArrayList<Integer> primes = sieve(max);
        System.out.println("Primos até " + max + ": " + primes);
    }
}
Mudanças realizadas:
Renomeei a classe para Sieve (sem acento e seguindo o padrão de nomenclatura Java).
Adicionei Javadoc para explicar o propósito de cada método.
Alterei o método any para all no método sieve, pois queremos verificar se o número não é divisível por nenhum dos primos conhecidos.
Adicionei um método main para demonstrar o uso do algoritmo.
Corrigi a condição do loop no método sieve para n <= max, pois queremos incluir o valor máximo na verificação.
