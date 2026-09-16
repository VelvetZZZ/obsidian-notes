1.%d
%d 是 C 语言里 printf 和 scanf 常见的**格式说明符**，表示 **十进制整数 int**。

2.&
& 在 C 里最常见的意思是：**取地址符**。

也就是“拿到某个变量在内存里的位置”。
- a：变量里的值
- &a：变量的地址

3.scanf
scanf 是 C 语言里用来**接收输入**的函数。

通常是从键盘读入数据，然后存进变量里。

```c
#include <stdio.h>

int main() {
    int a;
    scanf("%d", &a);
    printf("%d\n", a);
    return 0;
}
```
**它和printf的区别**:
- printf：输出
- scanf：输入

你可以先这样记：
- printf = print formatted按格式打印
- scanf = scan formatted按格式读取


4.变量的名字——标识符

构造规则：只能由字母、数字、下划线组成，<font color="#ff0000">数字不可以出现在第一个位置上，C语言关键字（保留字）不能做标识符。</font>
![[Pasted image 20260318203026.png]]
5.\n 是**换行符**。

6.
- scanf 读 double：重点记 %lf
    
- printf 输出浮点数：常见写 %f

7.运算符优先级
![[Pasted image 20260318215955.png]]
赋值是运算符（对C语言来说）
赋值也是运算，也有==结果==，结合关系是<font color="#ff0000">自右向左</font>，优先级<font color="#ff0000">最低</font>，嵌入式赋值不利于阅读，不推荐。

8.![[Pasted image 20260318221350.png]]
![[Pasted image 20260318221420.png]]
![[Pasted image 20260318221459.png]]
<span style="background:rgba(240, 107, 5, 0.2)"><font color="#ff0000">a++：先用，后加</font></span>
<span style="background:rgba(240, 107, 5, 0.2)"><font color="#ff0000">++a：先加，后用</font></span>
![[Pasted image 20260325214300.png]]

![[Pasted image 20260318221910.png]]


3.18 完成20/100


![[Pasted image 20260326145509.png]]
![[Pasted image 20260326145924.png]]
关系运算结果：成立1；不成立0.

switch case语句
![[Pasted image 20260326202743.png]]
3.26 完成32/100
![[Pasted image 20260326203533.png]]

