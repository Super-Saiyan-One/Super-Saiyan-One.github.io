---
title: leetcode 51
url: leetcode-51_url
tags:
  - dfs
categories:
  - 算法与数据结构
date: 2020-012-17 22:03:00
---
# 题意：简单搜索，学习注意格式
https://leetcode-cn.com/problems/n-queens/

```c++
class Solution {
public:
    int n;
    vector<bool> col,dg,udg;
    vector<vector<string>> ans;
    vector<string> path;

    vector<vector<string>> solveNQueens(int _n) {
        n=_n;
        col = vector<bool>(n);
        dg = udg = vector<bool>(n*2);
        path = vector<string>(n,string(n,'.'));

        dfs(0);
        return ans;
    }
    void dfs(int u){
        if(u == n){
            ans.push_back(path);
            return;
        }
        
        for(int i=0; i < n; i ++){
            if(!col[i]&&!dg[u-i+n]&&!udg[u+i]){
                col[i] = dg[u-i+n] = udg[u+i] = true;
                path[u][i] = 'Q';
                dfs(u+1);
                path[u][i] = '.';
                col[i] = dg[u-i+n] = udg[u+i] = false;
            }
        }
    }

};
<!-- more -->
