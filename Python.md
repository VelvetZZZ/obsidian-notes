# **一、期末复习.pdf**
判断题：1. 元组可以使用下标来修改其内部的元素。<font color="#ff0000">F</font>
<font color="#953734">：元组是不可变的对象，创建后不能修改元素，尝试修改会报错</font>
*<font color="#d99694">t = (1, 2, 3)*</font>
<font color="#d99694">*t[0] = 10  # 报错：TypeError</font>*
2.首先import math，然后运行sqrt(4)就可以成功对4求开根号。<font color="#ff0000">F</font>
<font color="#953734">：必须通过模块名调用函数，正确写法是math.sqrt(4)，直接写sqrt(4)会报错</font>
3.带有默认值的参数一定要位于参数列表的末尾位置。<font color="#ff0000">T</font>
<font color="#953734">：Python语法规定，默认参数必须放在非默认参数后面</font>
<font color="#e5b9b7">def func(a=1, b):  # 错误写法</font>
<font color="#e5b9b7">    pass</font>
<font color="#d99694">def func(b, a=1):#正确写法</font>
4.执行break语句，所有循环立即结束。<font color="#ff0000">F</font>
<font color="#953734">：break只会终止当前层的循环。多层嵌套时，外层循环不受影响：</font>
*for i in range(3):*
	*for j in range(3):*
		*if j == 1:*
			*break #只终止内层循环*
5.浮点型字面值可以用十进制或数学计数法表示。<font color="#ff0000">T</font>
<font color="#953734">：两种写法均合法：- 十进制：`3.14`  - 科学计数法：`6.02e23`</font>
6.Python属于编译性语言。<font color="#ff0000">F</font>
<font color="#953734">Python是</font>==**解释型语言**==。<font color="#953734">代码先编译为字节码，再由解释器执行，但用户感知的是解释执行。</font>
7.字符串可以通过索引赋值修改。<font color="#ff0000">F</font>
<font color="#953734">：字符串不可变，索引赋值会报错：</font>
<font color="#d99694">s = "hello"</font>
<font color="#d99694">s[0] = "H"  # 报错：TypeError</font>
8.文件的访问模式默认为可读。<font color="#ff0000">T</font>
<font color="#953734">：在 Python 里用 `open()` 函数去打开一个文件，但又不明确告诉它你是想读、想写、还是想追加内容时，Python 会默认你只是想读取文件内容。</font>
==*open(file, mode)*==
- ==`file`: 文件的路径和名称，例如 `'my_notes.txt'`。==
- ==`mode`: 访问模式，告诉 Python 你想对文件做什么。==
==*f = open('my_notes.txt', 'r') # 'r' 代表 Read (读取)等价于 f = open('my_notes.txt')*==
![[Pasted image 20250617085641.png]]
9.标识符由字母、下划线和数字组成，且数字不能开头。<font color="#ff0000">T</font>
<font color="#953734">Python标识符命名规则：</font>
	**允许的字符**: 只能包含 **字母** (a-z, A-Z)、**数字** (0-9) 和 **下划线** (`_`)。不能有空格、@、-、# 等任何其他特殊字符。
	**开头的字符**: **绝对不能用数字开头**。只能用字母或下划线开头。
	**大小写敏感**: Python 是大小写敏感的，这意味着 `myVar` 和 `myvar` 是两个完全不同的标识符。
	**不能是关键字**: 不能使用 Python 的保留关键字来作为标识符。关键字是 Python 内部有特殊含义的词，比如 `if`, `for`, `while`, `def`, `class` 等。
10.表达式 T[3] in [1, 2, 3, 4] 的值为False。<font color="#ff0000">T</font>
<font color="#953734">：**整个表达式的意思是**：“获取 T 的第 4 个元素（索引为3），然后判断这个元素是不是 1、2、3、4 中的一个。”</font>

单选题：
1.运行以下程序可以得到什么结果？<font color="#ff0000"> A</font>
student = 1
while student <= 3:
	total = 0
	 for score in range(1, 4):
		 score = int(input("Enter test score: "))
		 total += score
	 average = total/3
	 print("Student ",student,"average: ",average)
	 student += 1
A. 从键盘获得每个学生的3次考试成绩，一共3个学生，并输出每个学生的平均成绩。  
B. 从键盘获得每个学生的4次考试成绩，一共3个学生，计算12个成绩的平均值并输出。  
C. 从键盘获得每个学生的4次考试成绩，一共2个学生，然后取平均值并输出所有分数。  
D. 从键盘获得每个学生1次考试成绩，一共3个学生，并输出3个分数的平均值。

2.下列方法中，能够获取字典元组对列表的是  <font color="#ff0000">A</font>
A. `items()`  
B. `keys()`  
C. `item()`  
D. `values()`
<font color="#953734">:`items()` 返回键值对元组的列表（如 `[('key1', val1), ('key2', val2)]`）。</font>
<font color="#953734">B：`keys()` 返回键列表（非键值对）。</font>
<font color="#953734">C：`item()` 不是有效方法。</font>
<font color="#953734">D：`values()` 返回值列表（无键）</font>

3.以下程序的输出结果是  <font color="#ff0000">A</font>
my_toute = (10, 20, 30, 40, 50)
count = 0
for item in my_toute:
    if item > 25:
        count += 1
print(count)
A. 3　　B. 1　　C. 2　　D. 5
<font color="#953734">: 统计元组中大于25的元素：30、40、50 → 共3个。</font>

4.以下选项中，不是Python语言合法命名的是 <font color="#ff0000">C</font>
A. `MyGod5`  
B. `MyGod`  
C. `5MyGod` （数字开头）  
D. `_MyGod
<font color="#953734">:字母/下划线开头</font>

5.以下代码的输出结果是 <font color="#ff0000">C</font>
for s in "Hello World":
    if s == " ":
        break
    print(s, end="")
A. `World`  
B. `Helloorld`  
C. `Hello`  
D. `HelloWorld`

6.如下程序执行后结果为<font color="#ff0000"> A</font>
def func(a, b, c):
    print(a * b / c)
func(c=5, a=6, b=10)
A. 12.0 
B. 12
C. 3 
D. 产生语法错误
<font color="#953734">：该函数调用使用了**关键字参数**，允许不按顺序传递参数。所以 `a` 被赋值为6，`b` 为10，`c` 为5</font>。==在Python 3中，除法运算符 `/` 总是返回一个**浮点数**，即使结果是整数。==

7.编写一个程序, 判断输入的数字是奇数还是偶数。横线处代码请在下面选项中选择补充。<font color="#ff0000">A</font>
num = int(input())
if _ _ _ _ _ :
	print("Even")
else:
	print("Odd")
A. `num % 2 == 0`   
B. `num / 2 == 0.  
C. `num // 2 == 0`
D. `num % 2 != 0`
：==Even:偶数  Odd：奇数==      <font color="#e36c09">取余数操作符是 `%`</font>

8.下面代码的输出结果是：<font color="#ff0000">D</font>
a = [1, 3]
b = [2, 4]
a.extend(b)
print(a)
A. `[4, 3, 2, 1]` 
B. `[1, 2, 3, 4]` 
C. `[4, 2, 3, 1]` 
D. `[1, 3, 2, 4]`
==：`extend()` 方法的功能是将一个列表（这里是`b`）中的所有元素，逐一添加到另一个列表（这里是`a`）的**末尾**。==

9.生成一个词云图, 其中单词由 Life is short, you need Python组成, 完成划线处的程序。<font color="#ff0000">A</font>
import wordcloud
txt = "Life is short, you need Python"
w = wordcloud._ _ _ _ _
w.generate(txt)
w.to_file("py.png")

A. `WordCloud()` 
B. `wordcloud()` 
C. `cloud()` 
D. `wordcloud.wordcloud()`
:==`wordcloud` 库中最主要的类叫做 `WordCloud`（注意首字母大写）==<span style="background:rgba(255, 183, 139, 0.55)">要创建一个词云对象，需要实例化这个类，正确的语法是 `wordcloud.WordCloud()`。</span>

10.以下程序的运行结果是 <font color="#ff0000"> D</font>
from turtle import *
fillcolor("red")
begin_fill()
for i in range(5):
    fd(100)
    right(144)
end_fill()

A. 五角星  
B. 五边形  
C. 填充红色的五边形  
D. 填充红色的五角星
:==`right(144)` 是五角星专用转角（180°-36°），`fillcolor("red")` 设置红色填充。==

11.以下选项中不是文件操作函数或方法的是  <font color="#ff0000">B</font>
A. `readlines` 
B. `load` 
C. `writelines`
D. `read`
<font color="#953734">:`load()` 不是文件对象的方法。它通常是 `json` 或 `pickle` 这类库中的一个函数，用来从文件中加载并解析数据，例如 `json.load(file_object)`。</font>
==文件操作==指的是**程序与计算机文件系统交互的过程**，包括：
- 打开文件 **open()**
- 读取文件内容  
  **`read()`**：读取整个文件内容
  **`readline()`**：读取一行内容 
  **`readlines()`**：读取所有行，返回列表
- 写入新内容到文件
  **`write()`**：写入字符串
  **`writelines()`**：写入字符串列表
- 关闭文件 **`close()`**：关闭文件
- 其他重要方法
  **`seek()`**：移动文件指针位置
  **`tell()`**：获取当前文件指针位置
<font color="#d99694">file = open("example.txt", "r")</font>*
*<font color="#d99694">line1 = file.readline()  # 读取第一行</font>*
*<font color="#d99694">line2 = file.readline()  # 读取第二行</font>*
*<font color="#d99694">file.close()</font> 

12.下面代码的输出结果是 <font color="#ff0000">C</font>
print(pow(2, 10))
A. 12 B. 100 C. 1024 D. 20
==：pow(x, y)函数用于计算x的y次方==

13.要计算集合words中所有单词的元音字母总数, 填空处的代码应该是什么?  <font color="#ff0000">B</font>
words = {'apple', 'banana', 'cherry', 'date', 'elderberry', 'fig'}
vowel_count = 0
for word in words:
    for char in word:
        if _______ _ _ _ _ _ :
            vowel_count += 1
print(vowel_count)

A. `char not in 'aeiou'`
B. `char in 'aeiou'` 
C. `char.isalpha() and char.lower() in ['a', 'e', 'i', 'o', 'u']` 
D. `word.startswith(('a', 'e', 'i', 'o', 'u'))`
:*程序需要检查每个字符 `char` 是否是元音字母。
- 选项B `char in 'aeiou'` 是一个非常简洁和高效的判断方式，它检查当前字符是否存在于元音字母字符串中。由于题目给定的单词都是小写，这个方法完全够用。
- 选项A是判断非元音。选项C功能正确但过于复杂。选项D是判断单词的开头，不符合题意。

14.`random.uniform(a, b)` 的作用是 <font color="#ff0000">C</font>
A. 生成一个(a, b)之间的随机数 
B. 生成一个[a, b]之间的随机整数 <font color="#f79646">random.randint(a, b)</font>
C. 生成一个[a, b]之间的随机小数 
D. 生成一个均值为a, 方差为b的正态分布
: random.uniform(a, b) 用于生成一个在 `[a, b]` 区间内的随机**浮点数（小数）**，这个区间是包含a和b的。

15.下面代码的执行结果是   <font color="#ff0000">C</font>
a = 30
b = 1
if a >= 10:
    a = 20
elif a >=20:
    a = 30
elif a >= 30:
    b = a
else:
    b = 0
print("a={},b={}".format(a,b))
A. `a=30, b=30` 
B. `a=10, b=1` 
C. `a=30, b=1`
D. `a=20, b=1`

16.下面代码的输出结果是   <font color="#ff0000">A</font>
s = "The python language is a multimodel language."
print(s.split(' '))
A. `['The', 'python', 'language', 'is', 'a', 'multimodel', 'language.']`
B. `Thepythonlanguageisamultimodellanguage.`
C. 系统报错 
D. `The python language is a multimodel language.`
<font color="#953734">：字符串的 `split()` 方法用于分割字符串。</font>==`s.split(' ')` 表示以**空格**作为分隔符，将原字符串分割成一个**列表**。==<font color="#953734">每个被空格分开的部分都会成为列表中的一个独立元素。</font>

17.下列选项中，属于列表是 <font color="#ff0000">B</font>
A. `a = (1, 'a', [2, 'b'])`
B. `a = [1, 'a', [2, 'b']]` 
C. `a = {1, 'a', {2, 'b'}}` 
D. `a = "1, 'a', [2, 'b']"`
：在Python中，不同的括号定义了不同的数据类型：
- `[]` 方括号定义的是**列表 (List)**。
- `()` 圆括号定义的是**元组 (Tuple)**。
- `{}` 花括号定义的是**集合 (Set)** 或 **字典 (Dictionary)**。
- `""` 引号定义的是**字符串 (String)**。

18.如下程序段不能正确输出 `02468` 的是:()
A.
x=0
for i in range(0,5):
    print(x,end="")
    x=x+2 <font color="#d99694"># 循环5次，每次打印 `x` 后将 `x` 加2，会输出 `02468`</font>
B.
for i in range(0,10,2):
    print(i,end="")<font color="#d99694">#`range(0, 10, 2)` 直接生成序列 `0, 2, 4, 6, 8`，会输出 `02468`</font>
==`range(start, stop, step)`函数生成一个数字序列：==
- ==`start`：起始值（包含）==
- ==`stop`：结束值（不包含）==
- ==`step`：步长（默认为1）==

19.下面代码的输出结果是  <font color="#ff0000">B</font>
```python

for i in range(100, 200):
    s = str(i)
    if i == int(s[0]) ** 3 + int(s[1]) ** 3 + int(s[2]) ** 3:
        print(i)
A. 159   <span style="background:rgba(255, 183, 139, 0.55)"> B. 153</span>    C. 157    D. 152
<font color="#c0504d">：这段代码是在寻找100到199之间的“水仙花数”（或称阿姆斯特朗数），即一个三位数，其各位数字的立方和等于它本身。</font>

``````

20.下列选项中, 会输出1, 2, 3三个数字的是  <font color="#ff0000">C</font>
A.
for i in range(2):
    print(i+1)
B.
for i in range(3):
    print(i)
C.
alist = [0,1,2]
for i in alist:
    print(i+1) <font color="#d99694">#</font> <font color="#d99694">`alist` 是 `[0,1,2]`。`print(i+1)` 会输出 1, 2, 3。</font>
D.
i = 1
while i < 3:
    print(i)
    i = i + 1

21.一个整数, 它加上100后是一个完全平方数, 再加上168又是一个完全平方数, 请问该数是多少? 完成划线处程序。 <font color="#ff0000">A</font>
```python
import math
x = 0
while True:
    x = x + 1
    a = x + 100
    b = x + 100 + 168
    a_sqrt = math.sqrt(a)
    b_sqrt = math.sqrt(b)
    if _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ :
        print(x)
        break
        
```
A. `a == int(a)` and `b == int(b)` 
B. `a != int(a)` or `b != int(b)` 
C. `a == int(a)` or `b == int(b)` 
D. `a != int(a)` and `b != int(b)`
<font color="#953734">： 一个数是完全平方数，意味着它的平方根是一个整数。</font>
- ==`math.sqrt()` 返回的是一个浮点数。判断一个浮点数是否为整数，可以看它和它自己取整后的值是否相等。==<font color="#953734">例如 `5.0 == int(5.0)`。</font>
<font color="#953734">- 因此，需要同时满足 `a_sqrt` 是整数且 `b_sqrt` 是整数。即 `a_sqrt == int(a_sqrt)` and `b_sqrt == int(b_sqrt)`。</font>

22.考虑以下代码片段: `diagonal` 的结果是什么?   <font color="#ff0000">D</font>
```python
matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
diagonal = [matrix[i][i] for i in range(len(matrix))]
```
A. `[1, 2, 3]`
B. `[7, 8, 9]` 
C. `[3, 5, 7]`
D. `[1, 5, 9]`
：你定义的 matrix 是一个**二维列表**（也称嵌套列表）：
```python
matrix = [
    [1, 2, 3],   # 第0行
    [4, 5, 6],   # 第1行
    [7, 8, 9]    # 第2行
]
```
==len(matrix) 是外层列表的长度，即矩阵的“行数”==<font color="#953734">--->`len(matrix)` 是3</font>
- <font color="#953734">`range(len(matrix))` 会生成 `0, 1, 2`。</font>
<font color="#953734">- 每次循环，会从 `matrix` 中取出 `matrix[i][i]` 这个元素。</font>
<font color="#953734">	 当 `i=0` 时，取出 `matrix[0][0]`，即 `1`。</font>
<font color="#953734">	 当 `i=1` 时，取出 `matrix[1][1]`，即 `5`。</font>
<font color="#953734">	 当 `i=2` 时，取出 `matrix[2][2]`，即 `9`。</font>

23.下面代码的输出结果是  <font color="#ff0000">B</font>
```python
vlist = list(range(5))
for e in vlist:
    print(e, end=",")
```
A. `0:1:2:3:4:` 
B. `0,1,2,3,4,` 
C. `01234` 
D. `[0,1,2,3,4]`
<font color="#c0504d">:</font>  ==`vlist` 的值是 `[0, 1, 2, 3, 4]`==
- <font color="#c0504d">`for` 循环会遍历这个列表中的每一个元素 `e`。</font>
- ==`print(e, end=",")` 会打印出元素 `e`，并且在结尾处不打印换行符，而是打印一个逗号 `,`==。
<font color="#c0504d">- 所以，程序会依次打印 `0,` `1,` `2,` `3,` `4,`，最终连在一起就是 `0,1,2,3,4,`</font>

24.阅读下面的程序, 程序最终的执行结果为   <font color="#ff0000">C</font>
```python
a = 0
b = 10
if (a or b) and b:
    print("true")
else:
    print("false")
```
A. 没有任何输出 
B. 程序出现编译错误 
C. 结果为true 
D. 结果为false
:==在Python的布尔运算中，非零数字被视为 `True`，零被视为 `False`==
- **视为`False`的值**：
    - 数字`0`（包括`0.0`）
    - 空序列：`""`、`[]`、`()`、`{}`
    - `None`
    - `False`本身
- **视为`True`的值**：
    - 其他所有值（包括负数、非空字符串/列表等）
- ==`or`运算符的特性：==
    - 从左到右计算    
    - 返回**第一个为真的操作数**，如果没有则返回最后一个
- ==`and`运算符的特性==：
    - 从左到右计算
    - 如果第一个操作数为假，直接返回它
    - 否则返回第二个操作数