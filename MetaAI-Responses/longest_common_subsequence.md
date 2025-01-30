Aqui está o código corrigido:
Java
package java_programs;

import java.util.*;

public class LongestCommonSubsequence {

    /**
     * Retorna a maior subsequência comum entre duas strings.
     *
     * @param a Primeira string.
     * @param b Segunda string.
     * @return Maior subsequência comum.
     */
    public static String longestCommonSubsequence(String a, String b) {
        if (a.isEmpty() || b.isEmpty()) {
            return "";
        } else if (a.charAt(0) == b.charAt(0)) {
            return a.charAt(0) + longestCommonSubsequence(a.substring(1), b.substring(1));
        } else {
            String fst = longestCommonSubsequence(a, b.substring(1));
            String snd = longestCommonSubsequence(a.substring(1), b);
            return fst.length() >= snd.length() ? fst : snd;
        }
    }

    public static void main(String[] args) {
        String a = "ABCBDAB";
        String b = "BDCABA";
        System.out.println("Maior subsequência comum: " + longestCommonSubsequence(a, b));
    }
}
As principais correções foram:
Renomeei a classe para LongestCommonSubsequence para seguir as convenções de nomenclatura Java.
Adicionei um main para testar a função.
No caso em que os primeiros caracteres são iguais, passei a.substring(1) e b.substring(1) para a chamada recursiva, para avançar em ambas as strings.
Adicionei uma documentação Javadoc para a função longestCommonSubsequence.
