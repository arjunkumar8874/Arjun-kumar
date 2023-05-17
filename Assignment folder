#include <iostream>
#include <vector>
#include <queue>
#include <climits>

using namespace std;

int networkDelayTime(vector<vector<int>>& times, int n, int k) {
    vector<vector<pair<int, int>>> adjList(n + 1);
    for (const auto& time : times) {
        int u = time[0];
        int v = time[1];
        int w = time[2];
        adjList[u].push_back({v, w});
    }

    vector<int> dist(n + 1, INT_MAX);

    priority_queue<pair<int, int>, vector<pair<int, int>>, greater<pair<int, int>>> pq;

  
    dist[k] = 0;
    pq.push({0, k});

    while (!pq.empty()) {
        int u = pq.top().second;
        int uDist = pq.top().first;
        pq.pop();

        if (uDist > dist[u])
            continue;

        for (const auto& neighbor : adjList[u]) {
            int v = neighbor.first;
            int w = neighbor.second;

            if (uDist + w < dist[v]) {
                dist[v] = uDist + w;
                pq.push({dist[v], v});
            }
        }
    }

    int maxTime = 0;
    for (int i = 1; i <= n; i++) {
        if (dist[i] == INT_MAX)
            return -1;
        maxTime = max(maxTime, dist[i]);
    }

    return maxTime;
}

int main() {
    vector<vector<int>> times = {{2, 1, 1}, {2, 3, 1}, {3, 4, 1}};
    int n = 4;
    int k = 2;

    int minTime = networkDelayTime(times, n, k);
    cout << "Minimum time for all nodes to receive the signal: " << minTime << endl;

    return 0;
}
