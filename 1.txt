import java.util.*;

public class GraphTraversal {

    int vertices = 5;

    // Adjacency Matrix
    int graph[][] = {
        {0,1,1,0,0},
        {1,0,0,1,0},
        {1,0,0,0,1},
        {0,1,0,0,0},
        {0,0,1,0,0}
    };

    // ---------------- BFS ----------------
    void bfs(int start) {

        boolean visited[] = new boolean[vertices];

        Queue<Integer> queue = new LinkedList<>();

        visited[start] = true;
        queue.add(start);

        System.out.print("BFS Traversal: ");

        while (!queue.isEmpty()) {

            int node = queue.poll();
            System.out.print(node + " ");

            for (int i = 0; i < vertices; i++) {

                if (graph[node][i] == 1 && !visited[i]) {
                    visited[i] = true;
                    queue.add(i);
                }
            }
        }
    }

    // ---------------- DFS ----------------
    void dfs(int node, boolean visited[]) {

        visited[node] = true;

        System.out.print(node + " ");

        for (int i = 0; i < vertices; i++) {

            if (graph[node][i] == 1 && !visited[i]) {
                dfs(i, visited);
            }
        }
    }

    // ---------------- Main ----------------
    public static void main(String[] args) {

        GraphTraversal g = new GraphTraversal();

        // BFS
        g.bfs(0);

        System.out.println();

        // DFS
        boolean visited[] = new boolean[5];

        System.out.print("DFS Traversal: ");
        g.dfs(0, visited);
    }
}