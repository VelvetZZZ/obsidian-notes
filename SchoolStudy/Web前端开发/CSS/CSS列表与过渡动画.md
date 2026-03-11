## 1. 列表样式 (List Styling)
HTML 中的列表 (`<ul>`, `<ol>`) 默认都有“小黑点”或数字。CSS 允许我们修改或去掉它们。

| 属性                      | 说明   | 常用值 & 考试重点                                                               |
| :---------------------- | :--- | :----------------------------------------------------------------------- |
| **list-style-type**     | 标记类型 | `none` (**最常用**: 去掉小圆点)。<br>`disc` (实心圆), `circle` (空心圆), `square` (方块)。 |
| **list-style-image**    | 图片标记 | `url("image.png")` (用图片代替圆点)。                                            |
| **list-style-position** | 标记位置 | `outside` (默认，在文本框外)。<br>`inside` (在文本框内，和文字对齐)。                         |

###  简写属性 (Shorthand)
* **语法**: `list-style: type position image;`
* **高频代码**: 导航栏通常是用 `<ul>` 做的，第一步永远是：
    ```css
    li {
        list-style: none; /* 去掉前面的小圆点 */
    }
    ```

---
## 2. CSS3 过渡 (Transitions) —— ⭐⭐⭐ 核心考点
**定义**: 允许元素从一种样式**平滑**地改变为另一种样式（而不是瞬间突变）。常配合 `:hover` 使用。

### 2.1 四大核心属性

| 属性名 | 作用 | 说明 |
| :--- | :--- | :--- |
| **transition-property** | **谁变动?** | 指定要执行动画的属性 (如 `width`, `background`, `all`)。 |
| **transition-duration** | **变多久?** | **(必填)** 持续时间，单位 `s` 或 `ms`。如果不写，默认为0，无动画。 |
| **transition-timing-function** | **怎么变?** | 速度曲线。<br>`linear` (匀速), `ease` (慢-快-慢), `ease-in` (慢速开始)。 |
| **transition-delay** | **等多久?** | 延迟时间。在动画开始前等待的秒数。 |

### 2.2 简写神器 (必背顺序)
为了节省代码，我们通常只写一行 `transition` 属性。

* **语法公式**:
    `transition: property duration timing-function delay;`
* **记忆口诀**: **“谁变？多久？咋变？等多久？”**
* **铁律**:
    1.  如果有两个时间值，**第一个**是<span style="background:rgba(236, 57, 57, 0.55)">持续时间</span> (`duration`)，**第二个**是<span style="background:rgba(236, 57, 57, 0.55)">延迟时间</span> (`delay`)。
    2.  `duration` 是必须写的，否则没效果。

###  代码实战 (Code Example)
**场景**: 鼠标移上去，盒子宽度变宽，且背景变红。
```css
div {
    width: 100px;
    background: blue;
    /* 简写: 宽度变化，持续5秒，慢速开始慢速结束，延迟1秒执行 */
    transition: width 5s ease-in-out 1s; 
}

div:hover {
    width: 300px;
}
```