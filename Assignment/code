#include<bits/stdc++.h>
using namespace std;

#define INF 1000000000

int networkDelayTime(vector<vector<int>>& times, int n, int k) {
    vector<pair<int, int>> adj[n+1]; 
    vector<int> dist(n+1, INF); 
    priority_queue<pair<int, int>, vector<pair<int, int>>, greater<pair<int, int>>> pq; 
    
    for(auto time: times) {
        adj[time[0]].push_back({time[1], time[2]}); // adding directed edges to adjacency list
    }
    
    dist[k] = 0;
    pq.push({0, k}); 
    
    while(!pq.empty()) {
        int u = pq.top().second;
        pq.pop();
        
        for(auto v: adj[u]) {
            if(dist[u] + v.second < dist[v.first]) {
                dist[v.first] = dist[u] + v.second;
                pq.push({dist[v.first], v.first});
            }
        }
    }
    
    int ans = *max_element(dist.begin()+1, dist.end());
    
    if(ans == INF) {
        return -1;
    }
    
    return ans;
}

int main() {
    int n, m, k;
    cin >> n >> m >> k;
    vector<vector<int>> times(m, vector<int>(3));
    for(int i=0; i<m; i++) {
        cin >> times[i][0] >> times[i][1] >> times[i][2];
    }
    int ans = networkDelayTime(times, n, k);
    cout << ans << endl;
    return 0;
}
