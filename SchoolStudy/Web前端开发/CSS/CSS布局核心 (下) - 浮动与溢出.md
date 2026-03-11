# CSS 布局核心 (下): 浮动与溢出 (Float & Overflow)

**教材章节**: 第9章 页面布局定位 (9.2.3 - 9.2.4)
**考点**: #高度塌陷 #清除浮动 #display：none与visibility：hidden的区别

## 1. 🌊 CSS 浮动 (Float)
**教材 9.2.3 重点**。浮动最初是为了实现“文字环绕图片”的效果，后来被广泛用于网页布局（让块级元素横向排列）。

* **属性**: `float`
* **取值**:
    * `none`: 不浮动 (默认, 标准流, 竖着排).
    * `left`: **左浮动** (元素脱离文档流, 向左靠拢).
    * `right`: **右浮动** (元素脱离文档流, 向右靠拢).

### 必考灾难：高度塌陷 (Height Collapse)
* **现象**: 当父盒子**没有设置高度**，且里面的子盒子**全部浮动**后，<span style="background:#affad1">父盒子的高度会瞬间变成 **0**</span>。
* **后果**: 下面的标准流盒子会跑上来，被浮动盒子压住，导致布局错乱。
* **🚑 解决方案 (清除浮动)**:
    1.  **给父盒子加高度** (简单，但死板).
    2.  **`overflow: hidden` 法 (推荐)**: <span style="background:rgba(236, 57, 57, 0.55)">给父盒子添加 `overflow: hidden;` 属性</span>。这是考试中最常用、代码最少的方法。
    3.  **额外标签法**: 在所有浮动元素的最后加一个空标签 `<div style="clear:both"></div>`。
    4.  **伪元素法 (clearfix)**: (专业写法, 略复杂，了解即可).

---

## 2. 溢出控制 (Overflow)
当盒子里的内容太多，超出了盒子设定的宽高，该怎么办？

| 属性值         | 含义      | 效果描述                               |
| :---------- | :------ | :--------------------------------- |
| **visible** | 可见 (默认) | 内容会**溢出**到盒子外面，覆盖其他内容 (很难看)。       |
| **hidden**  | **隐藏**  | 超出的内容直接**切掉**，看不见 (常用于做圆角头像、清除浮动)。 |
| **scroll**  | 滚动      | 无论内容多少，总是显示滚动条。                    |
| **auto**    | 自动      | **最常用**。只有当内容超出时，才显示滚动条。           |

* **技巧**: 单行文本省略号 (`text-overflow: ellipsis`) 必须配合 `overflow: hidden` 和 `white-space: nowrap` 一起使用。
```css
.box {
    /* 1. 强制一行显示 (如果不写这行，文字会自动换行，就永远不会溢出了) */
    white-space: nowrap; 

    /* 2. 溢出隐藏 (如果不写这行，长文字会直接冲出盒子显示) */
    overflow: hidden; 

    /* 3. 溢出用省略号代替 (主角登场) */
    text-overflow: ellipsis; 
}
```

---

## 3. 可见性控制 (Visibility vs Display) —— ⭐⭐⭐ 经典面试/考试题
我们有两种方法让元素“消失”，但它们的效果截然不同。

| 属性 | 代码 | 特点 | 考试比喻 |
| :--- | :--- | :--- | :--- |
| **display** | `display: none;` | **彻底消失**。<br>元素从页面中移除，**不占位置**，后面的元素会补上来。 | 就像这个人**离职**了，工位被别人占了。 |
| **visibility** | `visibility: hidden;` | **隐身**。<br>元素看不见，但**依然占据原来的位置**和空间。 | 就像这个人**请假**了，人不在但工位还留着。 |

---

## 4. 教授的代码实战 (Code Example)

### 场景：经典的图文混排 + 清除浮动
```html
<style>
    /* 父容器 */
    .news-list {
        width: 500px;
        border: 1px solid black;
        /* 关键点：如果不加这行，边框会缩成一条线（高度塌陷） */
        overflow: hidden; 
    }
    
    .news-item {
        width: 100px;
        height: 100px;
        background: skyblue;
        margin: 10px;
        /* 让盒子横着排 */
        float: left; 
    }
</style>

<div class="news-list">
    <div class="news-item">1</div>
    <div class="news-item">2</div>
    <div class="news-item">3</div>
    </div>
```