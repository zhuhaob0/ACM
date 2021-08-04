# 求一个数n二进制表示中每个1的位置（lowbit(n)）

```cpp
/*取出n最低位的1以及后边的0构成的数值*/
int lowbit(int n){
   return n& -n;
}
```

```cpp
法一：
while(cin>>n){
     while(n>0){
        cout<<log2(lowbit(n))<<" ";
        n-=lowbit(n);
     }
     cout<<endl;
   }
```



```cpp
法二：
/*Hash代替log2()*/
const int MAX_N=1<<20;
   int H[MAX_N+1];
   for(int i=0;i<=20;i++) H[1<<i]=i;
   while(cin>>n){
    while(n>0){
        cout<<H[lowbit(n)]<<" ";
        n-=lowbit(n);
    }
    cout<<endl;
   }
```
$a^2$

$$
这里有一个稍微复杂但更高效的方法，就是建立一个长度为37的数组H，令H[2^k mod\ 37]=k。这里利用了一个数学小技巧：∀ k∈[0,35],
$$

$$
2^kmod 37互不相等，且恰好取遍整数1-36。程序如下：
$$

```cpp
法三：
int H[37],n;
   for(int i=0;i<36;i++) H[((long long)1<<i)%37]=i;
   while(cin>>n){
    while(n>0){
        cout<<H[lowbit(n)%37]<<" ";
        n-=lowbit(n);
    }
    cout<<endl;
   }
```

```cpp
GCC部分内置函数如下：
    int __builtin_ctz(unsigned int x)
    int __builtin_ctzll(unsigned long long x)
返回x的二进制表示下最低位的1后边有多少个0    
```

```cpp
    int __builtin_popcount(unsigned int x)
    int __builtin_popcountll(unsigned long long x)
返回x的二进制表示下有多少位为1        
```

```cpp
int __builtin_clz(unsigned int x);        //  求x的二进制数前导0的个数(ps:一共有32位)
__builtin_clz(0100) == 29;

int __builtin_ffs(unsigned int x);         //  求x的二进制数中最低位1的位置（突然发现和lowbit有一样的作用，但是要比lowbit慢）
__builtin_ffs(0100) == 3;

int __builtin_parity(unsigned int x);       //  求x的二进制数中1的个数的奇偶性(奇数为1  偶数为0)
__builtin_parity(0100) == 1;

```

