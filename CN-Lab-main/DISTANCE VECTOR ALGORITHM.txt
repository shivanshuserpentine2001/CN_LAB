class Graph:

    def __init__(self, vertices):
        self.V = vertices   
        self.graph = []   


    def add_edge(self, s, d, w):
        self.graph.append([s, d, w])


    def print_solution(self, dist, src, next_hop):
        print("Routing table for ", src)
        print("Dest \t Cost \t Next Hop")
        for i in range(self.V):
            print("{0} \t {1} \t {2}".format(i, dist[i], next_hop[i]))

    def bellman_ford(self, src):

        dist = [99] * self.V
        dist[src] = 0
        next_hop = {src: src}
        for _ in range(self.V - 1):
            for s, d, w in self.graph:
                if dist[s] != 99 and dist[s] + w < dist[d]:
                    dist[d] = dist[s] + w
                    if s == src:
                        next_hop[d] =d
                    elif s in next_hop:
                        next_hop[d] = next_hop[s]
        
        for s, d, w in self.graph:
            if dist[s] != 99 and dist[s] + w < dist[d]:
                print("Graph contains negative weight cycle")
                return

        self.print_solution(dist, src, next_hop)


def main():
    matrix = []
    print("Enter the no. of routers:")
    n = int(input())
    print("Enter the adjacency matrix : Enter 99 for infinity")
    for i in range(0,n):
        a = list(map(int, input().split(" ")))
        matrix.append(a)
        
    g = Graph(n)
    for i in range(0,n):
        for j in range(0,n):
            g.add_edge(i,j,matrix[i][j])
                
    for k in range(0, n):
        g.bellman_ford(k)

main()








/*

PS D:\codes\Practice Code\C++\lab> python -u "d:\codes\Practice Code\C++\lab\cn.py"
Enter the no. of routers:
5
Enter the adjacency matrix : Enter 99 for infinity
0 1 5 99 99
1 0 3 99 9 
5 3 0 4 99 
99 99 4 0 2
99 9 99 2 0
Routing table for  0     
Dest     Cost    Next Hop
0        0       0       
1        1       1       
2        4       1       
3        8       1       
4        10      1       
Routing table for  1     
Dest     Cost    Next Hop
0        1       0       
1        0       1
2        3       2
3        7       2
4        9       4
Routing table for  2
Dest     Cost    Next Hop
0        4       1
1        3       1
2        0       2
3        4       3
4        6       3
Routing table for  3
Dest     Cost    Next Hop
0        8       2
1        7       2
2        4       2
3        0       3
4        2       4
Routing table for  4
Dest     Cost    Next Hop
0        10      1
1        9       1
2        6       3
3        2       3
4        0       4
PS D:\codes\Practice Code\C++\lab>

*/