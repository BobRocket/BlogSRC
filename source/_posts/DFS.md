---
title: 深度优先搜索模板
date: 2023-03-04 21:27:26
index_img: https://pic.imgdb.cn/item/64034835f144a01007ead5bf.jpg
tags:
- 模板
- 深度优先搜索
categories: 
- OI
---

DFS 最显著的特征在于其 **递归调用自身**。同时与 BFS 类似，DFS 会对其访问过的点打上访问标记，在遍历图时跳过已打过标记的点，以确保 **每个点仅访问一次**。符合以上两条规则的函数，便是广义上的 DFS。

具体地说，DFS 大致结构如下：

```cpp
void dfs(int dep,'其他参数')
 {
   '自定义参数';
   if('无法再更新的状态')//对目标状态的判断
   {
     '输出解或计数作评价处理' ; 
   } 
   else if('剪枝条件满足 当前状态无用')
   {
     return;
   } 
   else
   {
     for(int i=1;i<='状态的拓展可能性';i++)
     {
       if('第i种拓展可行')
       {
         '标记' ;
         dfs(i+1,'其他参数') ; //更新状态
         '清除标记' 
       }
     }
   }
 } 
```

例题：[Luogu P1706 全排列问题](https://www.luogu.com.cn/problem/P1706)

```cpp
#include <iomanip>
#include <iostream>
using namespace std;
int n;
bool vis[50];  // 访问标记数组
int a[50];     // 排列数组，按顺序储存当前搜索结果

void dfs(int step) {
  if (step == n + 1) {  // 边界
    for (int i = 1; i <= n; i++) {
      cout << setw(5) << a[i];  // 保留5个场宽
    }
    cout << endl;
    return;
  }
  for (int i = 1; i <= n; i++) {
    if (vis[i] == 0) {  // 判断数字i是否在正在进行的全排列中
      vis[i] = 1;
      a[step] = i;
      dfs(step + 1);
      vis[i] = 0;  // 这一步不使用该数 置0后允许下一步使用
    }
  }
  return;
}

int main() {
  cin >> n;
  dfs(1);
  return 0;
}
```

