#include <iostream>
#include <map>
#include <vector>
#include <queue>
#include<bits/stdc++.h>
using namespace std;

bitset<10> row,col,d1,d2;
vector<vector<string>> ans;
void h(int i,int n,vector<string>& board){
    if (i==n){
        ans.push_back(board);
        return;
    }
    for (int j=0;j<n;j++){
        if (row[i]==0 && col[j]==0 && d1[i+j]==0 && d2[i-j+n-1]==0){
            row[i]=col[j]=d1[i+j]=d2[i-j+n-1]=1;
            board[i][j]='Q';
            h(i+1,n,board);
            board[i][j]='.';
            row[i]=col[j]=d1[i+j]=d2[i-j+n-1]=0;
        }
    }
    }
vector<vector<string>> solveNQueens(int n) {
    vector<string> board(n,string(n,'.'));
    h(0,n,board);
    return ans;
}


int main(){
    solveNQueens(4);
    for (auto a:ans){
        cout << "\n\n";
        for (auto r:a){
            cout << r << endl;
        }

    }
}
