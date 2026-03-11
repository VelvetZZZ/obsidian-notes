# if 分支语句 (Branching)

## 1. 三大基本结构 (The Big Picture) 
> 任何复杂的程序，底层也只有这三种结构：
1.  **顺序结构**：从上往下，一行行执行 (默认)。
2.  **分支结构**：遇到路口，选一条路走 (`if`, `switch`)。
3.  **循环结构**：原地转圈，直到条件满足 (`for`, `while`)。

---

## 2. if 语句家族 (Family Tree) 

### A. 单分支 (if)
* **场景**：如果是我的生日，就送长寿面；如果不是，什么都不做。
* **代码**：
    ```java
    if (条件表达式) {
        // 条件为 true 时执行的代码
    }
    ```

### B. 双分支 (if-else)
* **场景**：如果下雨 -> 在家玩；否则 -> 去游乐园。
* **口诀**：**非此即彼**。

### C. 多分支 (if-else if-else)
* **场景**：年龄段判断（婴儿、少儿、青少年、成年）。
* **逻辑**：层层筛选，**只要有一个满足了，后面的统统不看**（自带短路效果）。

###  教授的“布尔值”高分写法
PPT 第 7 页专门提到了这一点：
* **❌ 菜鸟写法**：`if (isBirthday == true)`
* **✅ 大神写法**：`if (isBirthday)`
* **原理**：`boolean` 变量<span style="background:rgba(236, 57, 57, 0.55)">本身就是真或假</span>，不需要再和 `true` 比一次。

---

## 3. 陷阱：省略大括号 (The No-Brace Trap) 
> **规则**：如果 `if` 或 `else` 后面 **只有 1 行代码**，大括号 `{}` 可以省略。

### 考试/开发双重警告
虽然语法允许，但**极度危险**！
```java
if (a > b)
    System.out.println("a大"); // ✅ 这句受 if 控制
    System.out.println("我无关"); // ❌ 这句其实已经在 if 外面了！
```
>[!WARNING] **考试策略**：
>1. **读代码题**：看到没大括号的 `if`，一定要盯着缩进，确认**只有紧跟的第一行**归它管。
>2. **写代码题**：**永远不要省略大括号！** 哪怕只有一行也加上 `{}`，防止扣分。


---
## 4. 经典算法：闰年判断 (Leap Year) 

> 这是期末考 **填空题** 和 **简答题** 的常客。 **规则**：
> 
> 1. 能被 4 整除，且 **不能** 被 100 整除。
>     
> 2. **或者**，能被 400 整除。

### 满分代码 (逻辑运算符版)

PPT 第 12 页展示了两种写法，**推荐用这一种**，一行搞定：

```Java
// 1. 导包 (千万别漏！)
import java.util.Scanner; 

public class LeapYear {
    public static void main(String[] args) {
        // 2. 创建 Scanner 对象
        Scanner sc = new Scanner(System.in);
        
        System.out.println("请输入年份：");
        // 3. 接收用户输入的年份
        int year = sc.nextInt(); 
        
        // 4. 核心逻辑 (背这个!)
        // 规则：(能被4整除 且 不能被100整除) 或者 (能被400整除)
        if ((year % 4 == 0 && year % 100 != 0) || (year % 400 == 0)) {
            System.out.println(year + " 是闰年");
        } else {
            System.out.println(year + " 不是闰年");
        }
    }
}
```

---

## 5. 复杂逻辑：个税计算器 (Tax Calculator) 

> **背景**：PPT 第 13 页展示了一个阶梯税率表。 **难点**：如何把表格翻译成 `if-else if` 链条。

### 📊 逻辑拆解 (Step-by-Step)

假设 `taxIncome` 是应纳税所得额。

```Java
double tax = 0; // 最终税额

if (taxIncome <= 1500) {
    // 第1档：3%
    tax = taxIncome * 0.03;
} else if (taxIncome <= 4500) {
    // 第2档：10% - 速算扣除数
    tax = taxIncome * 0.10 - 105;
} else if (taxIncome <= 9000) {
    // 第3档：20% - 速算扣除数
    tax = taxIncome * 0.20 - 555;
} else if (taxIncome <= 35000) {
    // ...以此类推
    tax = taxIncome * 0.25 - 1005;
} else {
    // 最高档
    tax = taxIncome * 0.45 - 13505;
}
```

**核心考点**：

1. **顺序很重要**：必须从**小到大**判断（先判 `<=1500`，再判 `<=4500`）。
    
2. **互斥性**：因为用了 `else if`，进入第2档时，隐含条件已经是 `>1500` 了，不用重复写。


### 教授的课后小灶

`if` 语句其实不难，难的是**逻辑的严密性**。

**我们来做一个快速自测（关于省略大括号的坑）：**

```java
int a = 10;
if (a > 50)
    System.out.println("A");
    System.out.println("B");
````

**问：屏幕会打印什么？**

- **你的直觉**：啥都不打印（因为 10 不大于 50）。
    
- **真相**：<span style="background:#ff4d4f">会打印 **"B"**！</span>
    
    - 因为省略了大括号，`if` 只管得住第一行（打印A）。
        
    - 第二行（打印B）<span style="background:rgba(240, 107, 5, 0.2)">是自由的</span>，不管 `a` 是多少，<span style="background:rgba(236, 57, 57, 0.55)">它都会执行</span>。

## 3. 编程大题速解 (Homework Solutions) 

### 题 1：奇偶数判断

> **口诀**：模 2 不等于 0 就是奇数。

```Java
import java.util.Scanner;
public class Demo1 {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        
        // 核心代码
        if (n % 2 != 0) {
            System.out.println("您输入的是奇数");
        } else {
            System.out.println("您输入的是偶数");
        }
    }
}
```

### 题 2：成绩分级 (Score Grading)

> **口诀**：从高往低判，逻辑最清晰。

```Java
// 假设 int score 已经接收了输入
if (score == 100) {
    System.out.println("满分");
} else if (score >= 80) { // 隐含了 < 100
    System.out.println("优秀");
} else if (score >= 60) { // 隐含了 < 80
    System.out.println("及格");
} else {
    System.out.println("不及格");
}
```

### 题 3：企业奖金提成 (Bonus Calculation)

> **这题是“分段计算”，比较麻烦。考试如果考这题，大概率是直接套公式。** 这里给出一个**最容易理解**的写法：不要算总数，**分段累加**。

```Java
import java.util.Scanner;
public class Bonus {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        double profit = sc.nextDouble(); // 利润 (万)
        double bonus = 0; // 奖金

        // 倒着算太麻烦，我们正着一段一段切 (类似切香肠)
        // 但为了代码短，我们用标准的 if-else 链，每一级算出“全额+超出部分”
        // 不过最简单的还是：
        
        if (profit <= 10) {
            bonus = profit * 0.1;
        } else if (profit <= 20) {
            // 10万的满额奖金(1万) + 超出部分 * 7.5%
            bonus = 1 + (profit - 10) * 0.075; 
        } else if (profit <= 40) {
            // 20万时的满额奖金(1.75万) + 超出部分 * 5%
            bonus = 1.75 + (profit - 20) * 0.05;
        } else if (profit <= 60) {
            // 40万时的满额奖金(2.75万) + 超出部分 * 3%
            bonus = 2.75 + (profit - 40) * 0.03;
        } 
        // ... 后面以此类推，只需要算出上一档封顶是多少钱即可
        
        System.out.println("应发奖金：" + bonus + "万");
    }
}
```

_(注：如果考试觉得算基数 1.75 这种太难记，就写分段累加的代码，虽然长但逻辑简单，不过上面这种写法代码行数最少)_