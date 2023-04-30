---
layout: page
title: Test
permalink: /test/
---

# Heading 1
## HEading 2
### HEAding 3
#### HEADing 4
##### HEADIng 5
###### HEADINg 6
####### HEADING 7

<center> center </center>

> Quating

Task list
- [ ] To be done
- [x] Done

###### Math Equation

1. Gaussion Distribution
   $$ \Phi(x) = \frac{1}{\sqrt{2 \pi} \sigma} e^{- \frac{(x - \mu)^2}{2 \sigma^2} } $$
2. Alignment
   $$
   \left\{
        \begin{aligned}
            \det \left(
                \begin{bmatrix}
                    {a_{11}} & {a_{12}} \\
                    {a_{21}} & {a_{22}} \\
                \end{bmatrix}
            \right) &= {a_{11}} {a_{22}} - {a_{12}} {a_{21}} \\
            \begin{bmatrix}
                {a} \\
                {b} \\
            \end{bmatrix}^{\top} \cdot 
            \begin{bmatrix}
                {c} \\
                {d} \\
            \end{bmatrix} &= ac + bd
        \end{aligned}
    \right.
   $$


###### Codes
+ C
    ```C { .line-numbers }
    #include <stdio.h>
    #include <stdlib.h>
    #include <stdarg.h>

    double average(int num, ...) {
        va_list vars;
        double sum = 0.0;

        va_start(vars, num);

        int i;
        for (i = 0; i < num; ++i) {
            sum += va_arg(vars, int);
        }

        va_end(vars);
        return sum / num;
    }

    int main() {
        printf("%lf", average(5, 1, 2, 3, 4, 5));
        printf("%lf", average(5, 5, 2, 6, 4, 5));

        return 0;
    }
    ```
+ C++
    ```C++
    #include <iostream>
    using namespace std;

    int main(int argc, char* argv[], char* env[]) {
        cout << "Programme Name: " << argv[0] << endl;

        cout << "Command line input arguments num: " << argc << endl;
        for (int i = 0; i < argc; ++i) {
            cout << "\tArg[" << i "]: " << argc[i] << endl;
        }

        cout << "Environment Variables:" << endl;
        for (int i = 0; env[i] != nullptr; ++i) {
            cout << "Env[" << i "]: " << env[i] << endl;
        }

        return 0
    }
    ```
+ Python
    ```Python
    #! /bin/python
    #方法1：使用os.listdir
    import os
    for filename in os.listdir(r'D:\'):
        print(filename)
    
    #方法2：使用glob模块，可以设置文件过滤
    import glob
    for filename in glob.glob(r'D:\'):
        print(filename)
    
    #方法3：通过os.path.walk递归遍历，可以访问子文件夹
    import os.path
    def processDirectory(args, dirname, filenames):
        print('Directory', dirname)
        for filename in filenames:
            print(' File', filename)
    
    os.path.walk(r'c:\windows', processDirectory, None)
    
    #方法4：非递归
    import os
    for dirpath, dirnames, filenames in os.walk(r'D:\'):
        print('Directory', dirpath)
        for filename in filenames:
            print(' File', filename)
    ```

###### Table

| Caption | Left | Middle | Right |
|:-:|:--------|:-----:|-----:|
|||
| :-1: |1Il\|       |   $1Il\|$   |    `Il\|` |
|$\alpha$|`code`|[link](https://markdown.com.cn/basic-syntax/)|![pic](https://markdown.com.cn/hero.png)|

---

Heading 1
---


HEading 2
===
