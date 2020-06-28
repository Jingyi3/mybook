---
weight: 10
---

# Union Find (Disjoint Set)

## Purpose
Detect Cycle in an Undirected Graph  

Kruskal's minimum spanning  
Grid percolation  
Network connection  
Least common ancestor in trees  
Image processing  

## Algo
### Union and Find
**Find**: Determine which subset a particular element is in. This can be used for determining if two elements are in the same subset.

**Union**: Join two subsets into a single subset.

## Complexity
Construction O(n)  
Union O(n) *    
Find O(n) *   
Get component size O(n) *   
Check if connected O(n) *   
Count component O(1)

`*` $\alpha$(n) means Amortized constant time

[Amortized slide](http://research.engineering.nyu.edu/~greg/algorithms/classnotes/applications-amortization.pdf)


## Code
    // Creates a graph with V vertices and E edges 
    Graph(int v,int e) { 
        V = v; 
        E = e; 
        edge = new Edge[E]; 
        for (int i=0; i<e; ++i) 
            edge[i] = new Edge(); 
    } 
  
    // A utility function to find the subset of an element i 
    int find(int parent[], int i) { 
        if (parent[i] == -1) 
            return i; 
        return find(parent, parent[i]); 
    } 
  
    // A utility function to do union of two subsets 
    void Union(int parent[], int x, int y) { 
        int xset = find(parent, x); 
        int yset = find(parent, y); 
        parent[xset] = yset; 
    } 
  
  
    // The main function to check whether a given graph 
    // contains cycle or not 
    int isCycle( Graph graph) { 
        // Allocate memory for creating V subsets 
        int parent[] = new int[graph.V]; 
  
        // Initialize all subsets as single element sets 
        for (int i=0; i<graph.V; ++i) 
            parent[i]=-1; 
  
        // Iterate through all edges of graph, find subset of both 
        // vertices of every edge, if both subsets are same, then 
        // there is cycle in graph. 
        for (int i = 0; i < graph.E; ++i) 
        { 
            int x = graph.find(parent, graph.edge[i].src); 
            int y = graph.find(parent, graph.edge[i].dest); 
  
            if (x == y) 
                return 1; 
  
            graph.Union(parent, x, y); 
        } 
        return 0; 
    } 
    
## Leetcode
[305. Number of Islands II](https://leetcode.com/problems/number-of-islands-ii/)

    
## reference
[union-find introduction](https://www.geeksforgeeks.org/union-find/)  
[union-find slide](http://research.engineering.nyu.edu/~greg/algorithms/classnotes/MST-kruskal.pdf)
[Job Sequencing Problem](https://www.geeksforgeeks.org/job-sequencing-using-disjoint-set-union/)