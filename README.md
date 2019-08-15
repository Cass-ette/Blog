# LegendsChen's blog
  
[未完成，先右转——>CSDN博客](https://blog.csdn.net/qq_31567525)

----------------------------

## 分类：

##### 暴力：

##### 贪心：

##### 动态规划：

##### 数据结构：

##### 树论：

##### 图论：

##### 数论：

##### 字符串：

##### 二分查找：

##### 排序：

##### 概率论：

##### 组合数学：

##### 博弈论：

##### 哈希：

##### 搜索：

##### 网络流：

##### 最短路：

暂存代码：
```c++
#include<cstdio>
#define N 51
using namespace std;
int n,m,r,c;
int map[N][N],way[4][2];
char ch[N];
int main()
{
	scanf("%d%d%d%d",&n,&m,&r,&c);
	way[0][0]=r,way[0][1]=c;
	way[1][0]=r,way[1][1]=-c;
	way[2][0]=c,way[2][1]=-r;
	way[4][0]=c,way[4][1]=r;
	for (int i=1;i<=m;i++)
	{
		scanf("%s",ch+1);
		for (int j=1;j<=n;j++) map[i][j]=ch[j]=='x';
	}
}
```
