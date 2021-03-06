# [牛客假日团队赛40](https://ac.nowcoder.com/acm/contest/5207#question)

## A

!!! note "题意"
    给一个$1,2...n$的序列,给定一种重排序方式,一次长度为$m$的重排使得其中第$i$位的数转移到第$p[i]$位,之后将这$m$个数中的第一张牌放入弃牌堆顶端,之后再取前$m$个数进行重排，当序列中剩余的数字个数小于$m$时,不进行重排,直接将牌放入弃牌堆顶端,有$q$次询问,每次询问一个$x$,求弃牌堆从上至下第$x$个数是多少

??? note "题解"
    对于弃牌堆中任意连续的$m$个数,我们都可以标记出他们的相对位置$1,2...m$,对于其中的任意一位置$i$都可以找到一个$nxt[i]$使得$p[nxt[i]]=i$,由于每次操作过后第一张牌会进入到弃牌堆,因此此次操作的$m$个数相对于上一次操作的$m$个数的相对位置应为$nxt[i]+1$,因此我们可以使用倍增,复杂度为$O((m+q)logn)$

## B

!!! note "题意"
	在长度为$n$的数列中选择一些数，要求相邻的数不能同时被选，求最大值；单点修改，每次修改后询问。
	
??? note "题解"
	线段树维护”只选区间左端点“，”只选区间右端点“，”区间左右端点都选“，”区间左右端点都不选“四个值即可。

## C

!!! note "题意"
	$n(n<=20000)$个点$m(m<=20000)$条边的有向图，其中有$k(k<=200)$个点是特殊点，保证每条边起点和终点至少有一个是特殊点，$q(q<=50000)$次询问求两点间最短路。
	
??? note "题解"
	可以发现任意一条路径一定可以拆分成$A$到$B$和$B$到$C$，其中$B$是特殊点，而$k$只有$200$，因此以每个特殊点为起点来$k$次正反图SPFA，每次暴力枚举中转点就卡过去了。
	
## D

!!! note "题意"
	$n(1<=n<=100)$头未拥有的牛，每个牛的形容词数量为$2~30$，同时拥有所有其他组合情况的牛（最多$1e9$），问拥有的牛中字典序第k小的牛的形容词组合

??? note "题解"
	把字典序转换成进制，直接求出不同组合情况的排名，将未拥有的牛加入，如果排名$<=k$，$k$就$+1$，求所有牛的第k小即可

## E

!!! note "题意"
	$n(1<=n<=20000)$头牛,每头牛有两个参数$A(i),B(i)$,当温度$T<A(i)$时贡献为$X$,$A(i)<=T<=B(i)$时贡献为$Y$,$T>=B(i)$时贡献为$Z$，求答案的最大值

??? note "题解"
	将$A(i),B(i)+1$离散化,从左到右扫一遍,每扫到一个数更新下答案,最后取最大值即可

## F

!!! note "题意"
	一个表盘为圆形的锁，两种三元组可以打开锁（可能相同），如果某个三元组与正确三元组对应位置的数字在锁上的距离$<=2$同样可以打开，询问能打开的方案数

??? note "题解"
	每位最多$5$种情况，直接暴力跑一遍即可

## G

!!! note "题意"
	数轴上$n(1<=n<=1000)$个带权目标点，选一个点和方向开始跳跃，每次跳跃的距离必须$>=$上次跳跃的距离，求最大得分

??? note "题解"
	$dp[i][j]$记录从$j$跳到$i$的最大得分，$f[i][j]$记录相反方向，左右方向分别dp取最大值即可

## H

!!! note "题意"
	$n(1<=n<=50000)$头牛，如果一头牛两侧$D$的区域里各有身高在她$2$倍及以上的牛，这头牛就会感到“拥挤”，求这种牛的个数

??? note "题解"
	考虑两棵平衡树，一个记录坐标，一个记录高度，每次找合法区间的最大值是否满足，正反各来一次即可。（也可以用单调队列或暴力）

## I

!!! note "题意"
	同$D$
	
??? note "题解"

## J

!!! note "题意"
	$k(1<=k<=16)$枚硬币，每枚面额在$1~1e9$，进行连续的$n(1<=n<=100000)$次购买，每次可以选择一枚硬币对任意一段购买区间付账，没有找零，问最多剩余多少钱，无法全部购买输出$-1$
	
??? note "题解"
	状压$dp$，$dp[sta]$表示状态$sta$下最多从$1$开始购买的数量（前缀和），每次枚举当前没有花的钱币，二分查找即可。

## K

!!! note "题意"
    二维平面上有$n$个点,有一以原点为圆心,半径为$R$的圆,问有多少对$(i,j)$使得点$i$与点$j$的连线不与圆相交

??? note "题解"
    对于每个点$i$做圆的切线，交圆于所对应的弧,两个点连线与圆不相交等价于两个点所对应的弧线相交,弧线用角度来表示即可

## L

!!! note "题意"
	有$n(2<=n<=3000000)$个房间,编号$0$到$n-1$,房间环状分布,每只奶牛都有一个喜欢的房间,如果房间被占用会依次向后探索房间。求所有奶牛入住后没有奶牛入住的编号最小的房间是多少

??? note "题解"
	暴力安排房间,用并查集合并一下即可