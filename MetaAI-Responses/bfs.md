# BFS

O código em Java acima implementa uma busca em largura (Breadth-First Search) em um grafo. No entanto, há um problema: o método breadth_first_search nunca retorna false, pois está preso no loop while (true).
Aqui está a correção do código:

```java
package java_programs;

import java.util.*;
import java.util.ArrayDeque;

/**
 *

* @author derricklin
 */
public class BREADTH_FIRST_SEARCH {

    public static Set<Node> nodesvisited = new HashSet<>();

    public static boolean breadth_first_search(Node startnode, Node goalnode) {
        Deque<Node> queue = new ArrayDeque<>();
        queue.addLast(startnode);

        nodesvisited.add(startnode);

        while (!queue.isEmpty()) {
            Node node = queue.removeFirst();

            if (node == goalnode) {
                return true;
            } else {
                for (Node successor_node : node.getSuccessors()) {
                    if (!nodesvisited.contains(successor_node)) {
                        queue.addLast(successor_node);
                        nodesvisited.add(successor_node);
                    }
                }
            }
        }
        return false; // Retorna false se não encontrar o nó objetivo
    }
}
```

As alterações feitas foram:
Substituí while (true) por while (!queue.isEmpty()) para que o loop termine quando a fila estiver vazia.
Adicionei return false; após o loop para retornar false se o nó objetivo não for encontrado.
Alterei queue.addFirst(successor_node) para queue.addLast(successor_node) para manter a ordem de inserção correta na fila.
Com essas alterações, o código agora funciona corretamente e retorna true se o nó objetivo for encontrado e false caso contrário.
