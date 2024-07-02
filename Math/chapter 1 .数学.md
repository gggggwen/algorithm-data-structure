# chapter 1 .数学



##  1.取最小公倍数

- **题目描述**:给出两个整数,求出两个整数的最小公倍数

###     方法Ⅰ:暴力枚举

   从大数开始枚举,容易超时。



###      方法Ⅱ: 欧几里得算法(求最大公约数)

$$
LCM(n,m)=\frac{n*m}{GAC(n,m)}
$$

- LCM为最小个公倍数

- GAC为最大公约数 

  那么该公式在代码实现上需要注意什么呢?

     首先是**整数溢出**的问题：在运算过程中若先调用（n*m）很容易出现**整数溢出的情况**这时，应当考虑先除后乘**减小运算过程中的中间数值**

    同时res=LCM(n，m)应当尽量取long long int 考虑**n=100001 m=100000**的情况

  

  **那么剩下的问题就是如何取最大公约数？**

  ###  欧几里得算法：

  思想：若两数为n与m（n>m),那么**k=(n-m)%GAC**也必然为其**最大公约数的整数倍**，那么**k与m的最大公约数也为GAC**

  ![](C:\Users\32939\Desktop\github_repo\algorithm-data-structure\Math\README.md)

####                   欧几里得算法代码实现

```C++
int gcd(int n ,int m)
{ 
   //假定n为大数
   while(m!=0)
   {
      int temp = n%m;
      n= m;
      m= temp;
   }
    //当循环结束 大数为所需的值,小数为0
   return n;
}
```

考虑m>n?  **yy**一下,很好想到,在m>n时,while循环内部操作其实就相当于进行了**一次交换**操作妙不妙!!!!!

-   递归实现

```c++
int gcd(int n ,int m)
 {
   if(n==0) return n;
   else return(gcd(m,n%m));
 }
```

