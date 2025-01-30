# BFS

O problema principal no código Java que você forneceu é que o breadth_first_search está em um loop infinito devido ao uso de queue.addFirst(successor_node) em vez de queue.addLast(successor_node), que deveria ser utilizado para garantir a ordem de busca adequada na estratégia de busca em largura (BFS). Além disso, o método não possui uma verificação adequada de término quando não há mais nós a serem visitados.

Aqui está o código corrigido:

```java
package java_programs;
import java.util.*;
import java.util.ArrayDeque;

public class BREADTH_FIRST_SEARCH {

    public static Set<Node> nodesvisited = new HashSet<>();

    public static boolean breadth_first_search(Node startnode, Node goalnode) {
        Deque<Node> queue = new ArrayDeque<>();
        queue.addLast(startnode); // Correção: use addLast para BFS

        nodesvisited.add(startnode);

        while (!queue.isEmpty()) {  // Correção: o loop deve verificar se a fila não está vazia
            Node node = queue.removeFirst();

            if (node == goalnode) {
                return true;  // Se o nó alvo for encontrado, retorna verdadeiro
            } else {
                for (Node successor_node : node.getSuccessors()) {
                    if (!nodesvisited.contains(successor_node)) {
                        queue.addLast(successor_node);  // Correção: adiciona sucessores ao final da fila
                        nodesvisited.add(successor_node);
                    }
                }
            }
        }
        return false;  // Se o loop terminar sem encontrar o nó alvo, retorna falso
    }
}
```

Mudanças feitas:
Uso correto de queue.addLast(successor_node):

A busca em largura (BFS) deve usar a fila para adicionar os sucessores no final, para garantir que os nós sejam processados na ordem correta. O código original estava usando addFirst, o que é incorreto para BFS.
Correção do loop while (!queue.isEmpty()):

O código original tinha um loop while (true) que causava um loop infinito. Agora, o loop continua enquanto a fila não estiver vazia, o que impede a busca de continuar após todos os nós terem sido processados.
Adição do retorno false:

O código agora retorna false caso o nó objetivo não seja encontrado, após a fila estar vazia.
Isso deve corrigir o comportamento e fazer com que a busca em largura funcione corretamente.
