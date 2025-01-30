Aqui está uma versão corrigida do código Java:
Java
package java_programs;

import java.util.*;

public class TopologicalOrdering {
    public static List<Node> topologicalOrdering(List<Node> directedGraph) {
        List<Node> orderedNodes = new ArrayList<>();
        Set<Node> visited = new HashSet<>();

        for (Node node : directedGraph) {
            if (!visited.contains(node) && node.getPredecessors().isEmpty()) {
                dfs(node, orderedNodes, visited);
            }
        }

        return orderedNodes;
    }

    private static void dfs(Node node, List<Node> orderedNodes, Set<Node> visited) {
        visited.add(node);

        for (Node nextNode : node.getSuccessors()) {
            if (!visited.contains(nextNode)) {
                dfs(nextNode, orderedNodes, visited);
            }
        }

        orderedNodes.add(node);
    }

    // Classe Node
    public static class Node {
        private String name;
        private List<Node> predecessors;
        private List<Node> successors;

        public Node(String name) {
            this.name = name;
            this.predecessors = new ArrayList<>();
            this.successors = new ArrayList<>();
        }

        public String getName() {
            return name;
        }

        public List<Node> getPredecessors() {
            return predecessors;
        }

        public List<Node> getSuccessors() {
            return successors;
        }

        public void addPredecessor(Node node) {
            predecessors.add(node);
        }

        public void addSuccessor(Node node) {
            successors.add(node);
        }
    }
}
As principais mudanças incluem:
Adição de uma classe Node para representar os nós do grafo.
Uso de um conjunto visited para manter controle dos nós visitados durante a busca em profundidade (DFS).
Implementação da DFS usando uma função recursiva dfs.
Adição de métodos addPredecessor e addSuccessor à classe Node para facilitar a construção do grafo.
Uso de uma lista orderedNodes para armazenar os nós ordenados.
Correção da lógica para adicionar os nós à lista orderedNodes.
Essas mudanças permitem que o código seja mais eficiente e fácil de entender. Além disso, a adição da classe Node torna o código mais organizado e reutilizável.
