Aqui está o código corrigido:
```Java
package java_programs;

import java.util.ArrayList;

public class WRAP {

    /**
     * Quebra uma string em linhas com um número máximo de colunas.
     * 
     * @param text O texto a ser quebrado.
     * @param cols O número máximo de colunas por linha.
     * @return Uma lista de strings, onde cada string é uma linha do texto quebrado.
     */
    public static ArrayList<String> wrap(String text, int cols) {
        ArrayList<String> lines = new ArrayList<>();
        String line;
        while (text.length() > cols) {
            int end = text.lastIndexOf(" ", cols); // Encontra o último espaço antes da coluna cols
            if (end == -1) {
                end = cols; // Se não encontrar um espaço, quebra na coluna cols
            }
            line = text.substring(0, end); // Cria uma linha com o texto até o espaço encontrado
            text = text.substring(end + 1); // Atualiza o texto removendo a linha criada
            lines.add(line); // Adiciona a linha à lista
        }
        if (!text.isEmpty()) { // Se ainda houver texto, adiciona como uma linha
            lines.add(text);
        }
        return lines;
    }

    public static void main(String[] args) {
        String text = "Este é um exemplo de texto que será quebrado em linhas.";
        int cols = 20;
        ArrayList<String> lines = wrap(text, cols);
        for (String line : lines) {
            System.out.println(line);
        }
    }
}
```
As principais correções foram:
Adicionar um espaço após o end no text.substring(end + 1) para remover o espaço da linha criada.
Adicionar uma condição para adicionar o texto restante como uma linha após o loop.
Melhorar a formatação e adicionar comentários para explicar o código.
