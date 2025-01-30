Aqui está uma versão corrigida do código:
Java
package java_programs;

import java.util.*;

public class SHORTEST_PATHS {
    final static int INF = 99999;

    public static Map<String, Integer> shortest_paths(String source, Map<List<String>, Integer> weight_by_edge) {
        Map<String, Integer> weight_by_node = new HashMap<>();
        for (List<String> edge : weight_by_edge.keySet()) {
            weight_by_node.put(edge.get(0), INF);
            weight_by_node.put(edge.get(1), INF);
        }
        weight_by_node.put(source, 0);

        // Implementação do algoritmo de Dijkstra
        Set<String> visited = new HashSet<>();
        while (visited.size() < weight_by_node.size()) {
            String minNode = null;
            int minWeight = INF;
            for (Map.Entry<String, Integer> entry : weight_by_node.entrySet()) {
                if (!visited.contains(entry.getKey()) && entry.getValue() < minWeight) {
                    minNode = entry.getKey();
                    minWeight = entry.getValue();
                }
            }
            visited.add(minNode);

            for (List<String> edge : weight_by_edge.keySet()) {
                if (edge.get(0).equals(minNode)) {
                    int newWeight = minWeight + weight_by_edge.get(edge);
                    if (newWeight < weight_by_node.get(edge.get(1))) {
                        weight_by_node.put(edge.get(1), newWeight);
                    }
                }
            }
        }

        return weight_by_node;
    }

    public static Map<String, Integer> shortest_paths(Node source, List<WeightedEdge> weight_by_edge) {
        Map<String, Integer> weight_by_node = new HashMap<>();
        for (WeightedEdge edge : weight_by_edge) {
            weight_by_node.put(edge.node1.getValue(), INF);
            weight_by_node.put(edge.node2.getValue(), INF);
        }
        weight_by_node.put(source.getValue(), 0);

        // Implementação do algoritmo de Dijkstra
        Set<String> visited = new HashSet<>();
        while (visited.size() < weight_by_node.size()) {
            String minNode = null;
            int minWeight = INF;
            for (Map.Entry<String, Integer> entry : weight_by_node.entrySet()) {
                if (!visited.contains(entry.getKey()) && entry.getValue() < minWeight) {
                    minNode = entry.getKey();
                    minWeight = entry.getValue();
                }
            }
            visited.add(minNode);

            for (WeightedEdge edge : weight_by_edge) {
                if (edge.node1.getValue().equals(minNode)) {
                    int newWeight = minWeight + edge.weight;
                    if (newWeight < weight_by_node.get(edge.node2.getValue())) {
                        weight_by_node.put(edge.node2.getValue(), newWeight);
                    }
                }
            }
        }

        return weight_by_node;
    }

    public static class Node {
        private String value;

        public Node(String value) {
            this.value = value;
        }

        public String getValue() {
            return value;
        }
    }

    public static class WeightedEdge {
        public Node node1;
        public Node node2;
        public int weight;

        public WeightedEdge(Node node1, Node node2, int weight) {
            this.node1 = node1;
            this.node2 = node2;
            this.weight = weight;
        }
    }
}
As principais alterações incluem:
Implementação do algoritmo de Dijkstra para encontrar os caminhos mais curtos.
Correção da lógica de atualização dos pesos nos nós.
Adição de classes para representar os nós e arestas com pesos.
Melhoria na legibilidade e organização do código.
