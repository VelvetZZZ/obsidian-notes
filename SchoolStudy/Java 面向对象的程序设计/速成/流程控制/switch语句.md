# Switch 语句与“穿透”陷阱

## 1. 核心结构 (The Structure) 
> **定义**：专门用于做 **等值判断** 的分支结构（<span style="background:rgba(236, 57, 57, 0.55)">只能比相等，不能比区间</span>）。
> **适用场景**：星期几、月份、支付方式、菜单选项。

```java
switch (变量) {
    case 值1:
        // 代码...
        break; // 🛑 刹车！跳出 switch
    case 值2:
        // 代码...
        break;
    default:
        // 兜底逻辑 (类似 else)
        break;
}
```
### 考试必考：支持的数据类型 (Supported Types)

这是填空题和判断题常客，必须背过：

1. **基本类型**：`byte`, `short`, `int`, `char` (注意：**不支持** `long`, `float`, `double` / boolean也不行)。
    
2. **引用类型**：
    - **`String`** (Java 7+ 新特性，必考！比如 "周三")。
        
    - **`Enum`** (枚举)。

---

## 2. 核心考点：穿透性 (Fall-through) 

>[!TIP] **口诀**：**"入口由 case 找，出口看 break。"**

- **原理**：`switch` 只要匹配到了一个入口（case），就会跳进去执行。如果不遇到 `break`，它会**无视后面的 case 标签**，直接继续向下执行下一行代码，直到遇到 `break` 或结束。
    
- **利用**：可以用这个特性把多个 case 合并（比如周六、周日都打印“休息”）。
    
- **灾难**：忘了写 `break`，导致执行了不该执行的代码（这就是你做错题的原因）。
    

### 考试代码演示

```Java
int i = 1;
switch(i) {
    case 1: System.out.print("A"); // 匹配中！执行打印 A。没 break，继续！
    case 2: System.out.print("B"); // 无视 case 2 标签，直接打印 B。
    default: System.out.print("C"); // 继续打印 C。
}
// 最终输出：ABC
```

---

## 3. 隐蔽陷阱：default 的位置 

- **规则**：`default` 可以放在 `switch` 里的**任何位置**（开头、中间、结尾都可以）。
    
- **执行逻辑**：<span style="background:rgba(236, 57, 57, 0.55)">先看所有的 `case`，如果没有一个匹配，才去执行 `default`。</span>
    
- **穿透风险**：如果 `default` 放在第一行且<span style="background:rgba(240, 167, 216, 0.55)">没写 `break`</span>，一旦执行了 `default`，它也会向下<span style="background:rgba(136, 49, 204, 0.2)">穿透到第一个 `case`</span>！

### 习题“验尸”报告 (深度解析)

现在我们用刚才学的知识，重新审视这两道错题。

#### **❌ 第 1 题：default 放在第一行
题目：下列代码的输出是 ( )
```JAVA
public static void main(String[] args) {
    int num = 46 / 10;   // 第一步：算出 num = 4
    switch (num) {       // switch(4)
        default:         // 第三步：没找到 case 4，所以执行 default
            System.out.println("不及格! ");
            // 😱 致命点：这里没有 break！
        case 6:          // 第四步：因为没 break，直接“滑”下来执行 case 6
            System.out.println("及格了! ");
            break;       // 🛑 第五步：遇到 break，终于停了
        case 7:
        case 8:
            System.out.println("良好! ");
        case 9:
        case 10:
            System.out.println("优秀! ");
            break;
    }
}
```
代码逻辑分析：**
1.  `int num = 46 / 10;` $\rightarrow$ `num` 等于 **4**。
2.  进入 `switch(4)`。
3.  **匹配过程**：
    * 找 `case 4`？没找到。
    * 因为没找到，所以去执行 **`default`** (虽然它在第一行，但它是备胎)。
4.  **执行 default**：
    * 打印 **"不及格! "**。
    * **关键点**：`default` 后面**没有 break**！
5.  **发生穿透**：
    * 程序像滑梯一样滑下去，进入 `case 6` 的代码区域（无视 `case 6` 这个标签）。
    * 打印 **"及格了! "**。
    * 遇到 `break`，跳出。
6.  **最终结果**：
    * "不及格! "
    * "及格了! "
    * 👉 **选项 B**。

#### **❌ 第 2 题：累加器陷阱 (选 D -> 正解 A)**


**代码逻辑分析：**
```java
int i = 1;
int result = 0;
switch (i) { // i 是 1
    case 1:
        result += i; // (1) 匹配中了！result = 0 + 1 = 1。
        // 😱 没 break！继续往下走！
    case 2:
        result += i * 2; // (2) result = 1 + 2 = 3。
        // 😱 还没 break！继续！
    case 3:
        result += i * 3; // (3) result = 3 + 3 = 6。
        // 😱 依然没 break！继续！
    default:
        result += i; // (4) result = 6 + 1 = 7。
        break; // 🛑 终于停了。
}
````

- **最终结果**：`result` = **7**。
    
- 👉 **选项 A**。