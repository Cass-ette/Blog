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
#include<cstring>
#define N 51
using namespace std;
int n,m,r,c,tot_dfn,tot,sum;
int head[N*N],next[N*N*N],e[N*N*N],vis[N*N],ma[N*N];
int map[N][N],dfn[N][N],way[4][2];
char ch[N];
void add(int x,int y){e[++tot]=y,next[tot]=head[x],head[x]=tot;}
int dfs(int x)
{{
	for (int i=head[x];i;i=next[i]) 
		if (!vis[e[i]]) 
		{
			vis[e[i]]=1;
			if (!ma[e[i]]||dfs(ma[e[i]])) 
			{
				ma[e[i]]=x;
				return 1;
			}
		}
	return 0;
}
}
int main()
{
	scanf("%d%d%d%d",&n,&m,&r,&c);
	way[0][0]=r,way[0][1]=c;
	way[1][0]=r,way[1][1]=-c;
	way[2][0]=c,way[2][1]=r;
	way[3][0]=c,way[3][1]=-r;
	for (int i=1;i<=m;i++)
	{
		scanf("%s",ch+1);
		for (int j=1;j<=n;j++) 
		{
			if (ch[j]=='x') map[i][j]=1;
			else dfn[i][j]=++tot_dfn;
		}
	}
	for (int i=1;i<=m;i++)
		for (int j=1;j<=n;j++)
			if (!map[i][j]) 
				for (int k=0;k<=3;k++)
				{
					int x=i+way[k][0],y=j+way[k][1];
					if (x&&x<=n&&y&&y<=m&&!map[x][y]) add(dfn[i][j],dfn[x][y]);
				}
	for (int i=1;i<=tot_dfn;i++)
		{
			memset(vis,0,sizeof(vis));
			if (dfs(i)) sum++;
		}
	printf("%d",tot_dfn-sum);
}
```
