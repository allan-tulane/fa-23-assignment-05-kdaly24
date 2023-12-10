# CMPS 2200 Assignment 5
## Answers

**Name:**_______Killian Daly______






- **1a.**
Given that there are d branching paths of the d-ary tree, I believe the maximum depth is $ \log_d  e$ , as we are accounting for the number of edges as well as the d branches to find our depth.

- **1b.**
I believe that work for deletion is $O((\log_d e) * d)$, given that removing the minimum will cause $d$ comparisons at $(\log_d e) - 1$ levels between the successive members of the branch as the minimum element is replaced.
For insertion the work is $O(\log_d e)$, as we are only making one comparison between the newly inserted element and the branch member $(\log_d e)$ times.

- **1c.**
Changing from binary to d-ary, the work becomes $O(e * (\log_d e))$

- **1d.**
Given the above algorithm, the optimal scenario for $O(e * (\log_d e))$ is that 

- **2a.**
For k = 1 & k = 2, all pairs are as following:
    APSP(0,2,k) == 0 -> 1 -> 2 = -1
    APSP(0,1,k) == 0 -> 1  = -2
    APSP(1,0,k) == 1 -> 0 = -2
    APSP(1,2,k) == 1 -> 0 -> 2 = 0
    APSP(2,1,k) == 2 -> 0 -> 1 = 0
    APSP(2,0 k) == 2 -> 1 -> 0 = -1
If k = 0, then:
    APSP(0,2,k) == 0 -> 2 = 2
    APSP(0,1,k) == 0 -> 1  = -2
    APSP(1,0,k) == 1 -> 0 = -2
    APSP(1,2,k) == 1 -> 2 = 1
    APSP(2,1,k) == 2 -> 1 = 1
    APSP(2,0 k) == 2 -> 0 = 2

- **2b.**
Yes, in this graph k of 1 and k of 2 are the same, because there are only 3 nodes and they can only be visited once, so the node available does not matter.
Yes, you can write all APSP(i,j,2) in terms of APSP(i,j,1), because with one node in between start and destination, you can transverse every node in this 3 node graph, thus taking the optimal route that would be taken in APSP(i,k,2) as there is no returning to previously visited nodes.


- **2c.**
Taking the oracles information, and looking at the above graph we can learn that for a value k, if APSP(i,j,k) connects to j by node x, APSP(i,j,k) will also include node x, and that APSP(i,x,k-1) follows the same path


- **2d.**
Considering that we only compute each subproblem once, # of distinct subproblems are at worst |V|!, given that each vertex is connected to each other vertex and thus results in the largest possible number of edges. Thus, work is $O(|E| * |V|^2)$ when we memoize.

- **2e.**
Work of Johnson's algorithm is better than ours in every circumstance.


- **3a.**
No, as the minimum spanning tree minimizes the overall weight, whereas MMET focuses on minimizing every possible edge. The MMET will always take the shortest edge between routes, which in short term is good but may end up creating a larger overall tree weight.

- **3b.**
As we in this problem care about 2nd to minimum weight rather than time complexity, we will take a cmix of minimum spanning tree and brute force. First, use the minimum spanning tree and from there, compare all vertices in the spanning tree that have more than one edge. For each non crucial optimal edge (ones that are the only path to connect a vertex to the spanning tree), compare the optimal edge path to the path that would be taken instead. Then, replace the optimal edge with the new path at the place where the difference between optimal and alternative path is shortest.

- **3c.**
Lets say we take kruskall's for minimum spanning tree, as the work included already sorts all edges by weight and a disjointed structure. From there, the worst case additional work of comparing each non-crucial edge will be |V|, representing that each edge is non crucial as every vertex has multiple paths, and comparison would be constant, as we already have all edges sorted by weight. Thus, work is $O(|V| * (|E| \log V))$