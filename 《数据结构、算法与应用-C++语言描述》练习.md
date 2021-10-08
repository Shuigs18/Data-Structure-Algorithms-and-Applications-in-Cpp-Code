---
title: 《数据结构、算法与应用 C++语言描述》练习
---

# 第一章 C++回顾

1. swap函数不会交换实参的值，因为x和y是在程序中是传值参数。调用swap函数会将实际参数的值复制非传值参数x和y，在作用域内x和y的值会进行交换，但是函数结束后不会将参数x和y的值传回。因此可以将参数形式改为引用参数，`swap(int &x, int &y)`

2. **count函数，返回值数组a[0:n-1]的数值个数???**

   ```c++
   template <class T>
   int count(T a[], int n, const T &value){
     //返回数组a中值为value的个数
     int theCount = 0;
     for (int i = 0; i < n; ++i){
       if (a[i] == value)
         theCount++;
     }
     return theCount;
   }
   ```

3. **函数fill：给数组a[start: end-1] 赋值value**

   ```c++
   template <class T>
   void fill(T a[], int start, int end, const T &value){
     //给数组a[start:end-1]赋值value
     for (i=0; i < end; ++i){
       a[i] = value;
     }
     return;
   }
   ```

4. **模版函数inner_prodcut，返回值是 $\sum_{i=0}^{n-1}a[i]*b[i]$** 

   ```c++
   template <class T>
   T inner_prodcut(const T a[], const T b[], int n){
       // 返回数组a和数组b的内积
       T ip = 0;
       for (int i = 0; i < n; ++i){
           ip += a[i] * b[i];
       }
       return ip;
   }
   ```

5. **模版函数iota：使 $a[i]=value+i, 0 \leq i < n$**

```C++
template <class T>
void iota(T a[], const T &value, int n){
    for (int i = 0; i < n; ++i){
        a[i] = i + value;
    }
}
```

6. **模版函数is_sorted：当且仅当 a[0: n-1] 有序时，返回值为true**

   ```c++
   template <class T>
   bool is_sorted(const T a[], int n){
     for (int i = 0; i < n - 1; ++i){
       if (a[i] > a[i+1])
         return false;
     }
     return true;
   }
   ```

7. **模版函数mismatch：返回值是使不等式 $a[i] \neq b[i]$** 成立的最小索引 i，$0 \leq i < n$

   ```c++
   template <class T>
   int mismatch(const T a[], const T b[], int n){
     for (int i = 0; i < n; ++i)
       if (a[i] != b[i])
         return i;
    	return n; // 没有匹配
   }
   ```

8. **是相同的签名函数，函数名、形参数量和类型都一样，当调用这两个函数时，编译器不能够分辨是哪个函数**

9. 1）调用了1-1 int abc(int a, int b, int c)

   2）调用了1-2 float abc(float a, float b, float c)

   3）编译错误

   4）调用了1-2

10. **修改1-8程序**

    ```c++
    #include <iostream>
    using std::cout; using std::endl;
    
    int abc(int, int, int);
    
    int main() {
        try {cout << abc(0, 0, 0) << endl;}
        catch (int e){
          cout << "The parameters to abc were 0, 0, 0" << endl;
          cout << "An exception has been thrown" << endl;
          cout << e << endl;
          return 1;
        }
        return 0;
    }
    
    int abc(int a, int b, int c){
      if (a < 0 && b < 0 && c < 0)
        throw 1;
      if ((a == 0) && (b == 0) && (c == 0))
        throw 2;
      return a + b * c;
    }
    ```

11. **重做练习2， 当 n < 1 时， 抛出类型为 char* 的异常。测试你的代码**

    ```c++
    template <class T>
    int count(T a[], int n, const T &value){
      //返回数组a中值为value的个数
      if (n < 1)
        throw "n should be positive !"
      int theCount = 0;
      for (int i = 0; i < n; ++i){
        if (a[i] == value)
          theCount++;
      }
      return theCount;
    }
    ```

    
