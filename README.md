//# bfs-traversal
//bfs traversal of an undirected graph
#include<bits/stdc++.h>
using namespace std;
void bfs(vector<int> adj[],int n,vector<int>&vis,int node,vector<int>&ans){
    queue<int>q;
    q.push(node);
    vis[node]=1;
    while(!q.empty()){
        int x=q.front();
        q.pop();
        
        ans.push_back(x);
        for(auto it:adj[x]) {
           if(vis[it]==0) {q.push(it);vis[it]=1;}
        }
    }

}
int main(){
    int t;
    cin>>t;
    while(t--){
        int n,m;
        cin>>n>>m;
        vector<int>adj[n];
        for(int i=0;i<m;i++) {
            int a,b;
            cin>>a>>b;
            adj[a].push_back(b);
            adj[b].push_back(a);
        }
        vector<int>ans;
        vector<int>vis(n,0);
        for(int i=0;i<n;i++){
            if(vis[i]==0) {
                bfs(adj,n,vis,i,ans);
            }
        }
        for(auto it:ans) cout<<it<<" ";
        cout<<endl;
    }
}
