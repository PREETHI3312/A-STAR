<h1>ExpNo 4 : Implement A* search algorithm for a Graph</h1> 
<h3>Name: PREETHI A K</h3>
<h3>Register Number: 212223230156</h3>
<H3>Aim:</H3>
<p>To ImplementA * Search algorithm for a Graph using Python 3.</p>
<H3>Algorithm:</H3>


A* Search Algorithm
<ol>
<li> Initialize the open list</li>
<li> Initialize the closed list put the starting node on the open list (you can leave its f at zero)</li>
<li> While the open list is not empty<br>
    a. Find the node with the least f on 
       the open list, call it "q"<br>
    b. Pop q off the open list<br>
    c. Generate q's 8 successors and set their parents to q for each successor<br><ol>
        i. If successor is the goal, stop search<br>
        ii. Else, compute both g and h for successor
          <br>
          successor.g = q.g + distance between successor and successor.h = distance from goal to 
          successor (This can be done using many 
          ways, we will discuss three heuristics- 
          Manhattan, Diagonal and Euclidean 
          Heuristics)<br>
          successor.f = successor.g + successor.h<br>
        iii. if a node with the same position as successor is in the OPEN list which has a lower f than successor, skip this successor <br>
        iv. if a node with the same position as 
            successor  is in the CLOSED list which has
            a lower f than successor, skip this successor
            otherwise, add  the node to the open list
     end (for loop)<br></ol>
    d. push q on the closed list
    end (while loop)
</li>
</ol>

<h2>PROGRAM :</h2>
<pre><code>
from collections import defaultdict
H_dist ={}
def aStarAlgo(start_node, stop_node):
    open_set = set(start_node)
    closed_set = set()
    g = {}  
    parents = {}   
    g[start_node] = 0
    parents[start_node] = start_node
    while len(open_set) > 0:
        n = None
        for v in open_set:
            if n == None or g[v] + heuristic(v) < g[n] + heuristic(n):
                n = v
        if n == stop_node or Graph_nodes[n] == None:
            pass
        else:
            for (m, weight) in get_neighbors(n):
                if m not in open_set and m not in closed_set:
                    open_set.add(m)
                    parents[m] = n
                    g[m] = g[n] + weight
                else:
                    if g[m] > g[n] + weight:
                        g[m] = g[n] + weight
                        parents[m] = n
                        if m in closed_set:
                            closed_set.remove(m)
                            open_set.add(m)
        if n == None:
            print("Path does not exist!")
            return None
        if n == stop_node:
            path = []
            while parents[n] != n:
                path.append(n)
                n = parents[n]
            path.append(start_node)
            path.reverse()
            print('Path found: {}'.format(path))
            return path
        open_set.remove(n)
        closed_set.add(n)
    print('Path does not exist!')
    return None
def get_neighbors(v):
    if v in Graph_nodes:
        return Graph_nodes[v]
    else:
        return None
def heuristic(n):
    return H_dist[n]
graph = defaultdict(list)
n,e = map(int,input().split())
for i in range(e):
    u,v,cost = map(str,input().split())
    t=(v,int(cost))
    graph[u].append(t)
    t1=(u,int(cost))
    graph[v].append(t1)
for i in range(n):
    node,h=map(str,input().split())
    H_dist[node]=int(h)
Graph_nodes=graph
start=input()
goal=input()
aStarAlgo(start, goal)
</code></pre>

<hr>
<h2> INPUT</h2>
<hr>
<img width="124" height="365" alt="image" src="https://github.com/user-attachments/assets/5d5b22b1-23f8-4c48-a47f-88f76e0b65fb" />







<hr>
<h2> Output</h2>
<hr>
<img width="442" height="68" alt="image" src="https://github.com/user-attachments/assets/6f4e57d6-3dee-4cbd-878c-8cc0ad41f845" />




<h2>RESULT :</h2>
Thus a graph was constructed and implemantation of A star Search for the same graph was done successfully.
