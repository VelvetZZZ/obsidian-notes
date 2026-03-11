# Scanner 类 (数据输入)

## 1. 它是做什么的？ 
> 程序默认是“自闭”的。Scanner 就像给程序插了一根管子，让用户可以通过键盘 (System.in) 往程序里“灌”数据。

## 2. 考试必背三部曲 (模板) 📝
> 手写代码题，这三行代码必须形成肌肉记忆！少一行都会扣分。

```java
// 第一步：导包 (在代码最最最上面)
// ⚠️ 忘记写这行是初学者扣分最多的地方！
import java.util.Scanner; 

public class Main {
    public static void main(String[] args) {
        // 第二步：创建 Scanner 对象 (通常叫 input 或 sc)
        // System.in 代表“标准输入流” (键盘)
        Scanner sc = new Scanner(System.in); 
        
        System.out.println("请输入你的年龄：");
        
        // 第三步：接收数据 (根据想要的数据类型调用不同方法)
        int age = sc.nextInt(); // 程序会在这里暂停，等用户按回车
        
        System.out.println("你的年龄是：" + age);
    }
}
```
## 3. 常用方法 (Method) 

> 就像遥控器上的按钮，想要什么类型的数据，就按什么按钮。

| **想要的数据类型**      | **调用的方法**      | **说明**             | **实例**                                                       |
| ---------------- | -------------- | ------------------ | ------------------------------------------------------------ |
| **整数 (int)**     | `nextInt()`    | 最常用                | `int n = sc.nextInt();`                                      |
| **小数 (double)**  | `nextDouble()` | 输入金额、成绩时用          | `double d = sc.nextDouble();`                                |
| **字符串 (String)** | `next()`       | **遇到空格就停止** (不吃空格) | 输入姓名: "Zhang San" -> 只能读到 "Zhang"                            |
| **整行字符串**        | `nextLine()`   | **读取一整行** (吃回车)    | 输入地址时用，<span style="background:rgba(236, 57, 57, 0.55)">能读空格 |

### 考试防坑实例 (Scanner 的深坑) ️

**场景**：先读数字，再读字符串。

```Java
// ❌ 错误示范
int age = sc.nextInt();      // 用户输入 18 并且按了回车
String name = sc.nextLine(); // 😱 完了！这里读不到名字！

// 💡 为什么？
// nextInt() 只拿走了数字 18，但你按的那个“回车符”还留在管道里。
// 下面的 nextLine() 一看管道里有个回车，以为用户输入结束了，直接读取为空。
```
**解决方案**： 如果你又要由数字又要由字符串，建议**全用 `next()`** (如果不含空格) 或者在 `nextInt()` 后加一句 `sc.nextLine()` 专门吃掉那个回车。