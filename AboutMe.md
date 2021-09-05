# Patrick Trani

## Interesting Facts

Aside from being a computer student who holes up and plays skyrim waiting for elder scrolls 7 to be announced, I also have partaken in a some less than ordinary sports. I took fencing lessons for a summer once and got stabbed many times. I tried out downhill mountain biking and had I not run into a tree, I would've flown down the side of a mountain. My father coached my brother and I to be better than average table tennis players. I love racing and had a quick stint of a go karting phase. Possibly the craziest of them all is, choosing to run cross country and enjoying it. 

Also... I own this
![Hey you, finally awake?](/pic.jpg)

---

### Food and Drinks I would suggest

This is a quick table of food/drinks I suggest people try. It has a variety of probably basic options since I dont eat out at a lot of places with interesting menu items.

| Food/Drink | Location | Price |
| ---------- | -------- | ----- |
| Chicken and Shrimp | Kobe Steakhouse of Japan | $30.00 |
| Pot of Gold (Mangocolada) | Applebees | $5.00 |
| Smashburger | Made by my friend Aaron | Free |
| Any Pizza | Chester's Bakery in Fairfield Vermont | $10.00 |

---

### Quotes I enjoy

> "Where are you going chief?
> "To give the covenant back their bomb" - Master Chief 'Halo 2'

>"All your life, you'll meet people that only want to break you down. Forget them, stand strong with the people who build you up." - Markiplier

---

### Alogrithm Fun
#### Minimum Spanning Tree - Prims Algorithm

> "In computer science, Prim's algorithm (also known as Jarník's algorithm) is a greedy algorithm that finds a minimum spanning tree for a weighted undirected graph. This means it finds a subset of the edges that forms a tree that includes every vertex, where the total weight of all the edges in the tree is minimized. The algorithm operates by building this tree one vertex at a time, from an arbitrary starting vertex, at each step adding the cheapest possible connection from the tree to another vertex." - **[Wikipedia](https://en.wikipedia.org/wiki/Prim%27s_algorithm)**\

#### **Code for Prims Algorithm**

    int n;
    vector<vector<int>> adj; // adjacency matrix of graph
    const int INF = 1000000000; // weight INF means there is no edge

    struct Edge {
        int w = INF, to = -1;
    }; 

    void prim() {
        int total_weight = 0;
        vector<bool> selected(n, false);
        vector<Edge> min_e(n);
        min_e[0].w = 0;

    for (int i=0; i<n; ++i) {
        int v = -1;
        for (int j = 0; j < n; ++j) {
            if (!selected[j] && (v == -1 || min_e[j].w < min_e[v].w))
                v = j;
        }

        if (min_e[v].w == INF) {
            cout << "No MST!" << endl;
            exit(0);
        }

        selected[v] = true;
        total_weight += min_e[v].w;
        if (min_e[v].to != -1)
            cout << v << " " << min_e[v].to << endl;

        for (int to = 0; to < n; ++to) {
            if (adj[v][to] < min_e[to].w)
                min_e[to] = {adj[v][to], v};
        }
    }

    cout << total_weight << endl;
}`
