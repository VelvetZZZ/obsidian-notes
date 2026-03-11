# CSS 盒子模型 (Box Model)

**考点**: 盒子尺寸计算、简写属性、Padding与Margin的区别

## 1. 核心组成 (由内向外)
一个标准的 CSS 盒子包含 4 个部分：
* **Content (内容区)**: 呈现文本或图像的区域，由 `width` 和 `height` 控制。
* **Padding (内边距)**: 内容与边框之间的透明区域。
* **Border (边框)**: 围绕内边距和内容的线条。
* **Margin (外边距)**: 边框外的透明区域，用于隔开相邻元素。
```text
┌──────────────────────────────────────────────┐
│                    margin                    │
│  ┌────────────────────────────────────────┐  │
│  │                 border                 │  │
│  │  ┌──────────────────────────────────┐  │  │
│  │  │              padding             │  │  │
│  │  │  ┌────────────────────────────┐  │  │  │
│  │  │  │           content          │  │  │  │
│  │  │  └────────────────────────────┘  │  │  │
│  │  └──────────────────────────────────┘  │  │
│  └────────────────────────────────────────┘  │
└──────────────────────────────────────────────┘
```

## 2. ⚠️ 盒子尺寸计算 (考试必考公式)
在标准盒子模型 (`box-sizing: content-box`，默认情况) 下：

* **盒子在页面占据的总宽度** = `margin-left` + `border-left` + `padding-left` + **`width`** + `padding-right` + `border-right` + `margin-right`
* **盒子在页面占据的总高度** = `margin-top` + `border-top` + `padding-top` + **`height`** + `padding-bottom` + `border-bottom` + `margin-bottom`

> [!TIP] **注意**: CSS 中设置的 `width` 和 `height` **仅仅** 是指内容区域 (Content) 的宽高，**不包含** Padding 和 Border！这是新手最容易算错的地方。

## 3. 属性简写规则 (顺时针)
`padding` 和 `margin` 的简写方式完全一致，考试常考填空题：

| 写法 | 含义 | 记忆口诀 |
| :--- | :--- | :--- |
| `margin: 10px;` | 上下左右都是 10px | **全包围** |
| `margin: 10px 20px;` | 上下 10px，左右 20px | **上下、左右** |
| `margin: 10px 20px 30px;` | 上 10px，左右 20px，下 30px | **上、左右、下** |
| `margin: 10px 20px 30px 40px;` | 上 10px，右 20px，下 30px，左 40px | **上右下左 (顺时针)** |

## 4.  常见应用技巧
* **水平居中**: 对于块级元素（如 `div`），设置宽度后，使用<span style="background:rgba(236, 57, 57, 0.55)"> `margin: 0 auto;`</span> 可实现<span style="background:rgba(240, 107, 5, 0.2)">水平居中</span>。

* **清除默认边距**:
    ```css
    * {
        margin: 0;
        padding: 0;
    }
    ```

# CSS 边框与表格布局 (Borders & Tables)

**考点**: 边框简写、表格边框合并、单元格对齐

## 1.  盒子模型之：边框 (Border)
边框是盒子模型的“皮肤”。在 CSS 中，设置边框需要三个核心要素：**粗细 (width)**、**样式 (style)**、**颜色 (color)**。

### 1.1 边框简写 (必背!)
考试中写代码，千万不要写 `border-width:..; border-style:..; border-color:..;` 这样太慢了！
**标准简写公式**:
```css
/* border: 宽度 样式 颜色; */
border: 1px solid red;
```
- **顺序**: 顺序通常不严格，但习惯上按上面这个顺序写。
- **单边设置**: `border-top`, `border-bottom`, `border-left`, `border-right`。
## 1.2 常用边框样式 (border-style)
|**值**|**含义**|**样式描述**|
|---|---|---|
|**solid**|实线|最常用，一条实心的线|
|**dashed**|虚线|由短线组成的虚线 (- - -)|
|**dotted**|点线|由圆点组成的点线 (• • •)|
|**double**|双线|两条平行实线 (宽度包含两条线加中间空隙)|
|**none**|无边框|隐藏边框 (常用 `border: 0` 或 `border: none`)|

## 2. 表格独有样式 (Table Styles)

表格是特殊的 HTML 结构，因此有一套专门控制它的 CSS 属性。
### 2.1 边框合并 (border-collapse) —— ⭐⭐⭐ 核心考点

默认情况下，表格的单元格之间是有缝隙的（双线边框）。

- **属性**: `border-collapse`
    
- **取值**:
    
    - `separate`: 默认值，边框分离。
        
    - **`collapse`**: **合并模式**。相邻边框合并为一条，制作“细线表格”必用！。

### 2.2 边框间距 (border-spacing)

- **作用**: 只有在 `border-collapse: separate` (分离模式) 下才有效。控制单元格之间的距离。
    
- **代码**: `border-spacing: 10px;`。

### 2.3 标题位置 (caption-side)

- **作用**: 控制表格标题 `<caption>` 显示在顶部还是底部。
    
- **取值**: `top` (默认), `bottom` (底部)。

### 2.4 垂直对齐 (vertical-align)

- **注意**: `text-align` 控制水平对齐 (左/中/右)，`vertical-align` 控制垂直对齐。
    
- **作用对象**: <span style="background:rgba(236, 57, 57, 0.55)">表格单元格</span> (`td`, `th`) 或<span style="background:rgba(236, 57, 57, 0.55)">行内块元素</span> (`img`, `inline-block`)。
    
- **取值**: `top` (顶端), `middle` (居中), `bottom` (底端)。

---

## 3.  教授的代码实战 (Code Example)

**场景**: 制作一个细线边框、标题在下、文字居中的课程表。
```html
<!DOCTYPE html>
<html>
<head>
    <style>
        /* 1. 设置表格整体 */
        table {
            width: 500px;
            /* 关键点: 合并边框，消灭双线 */
            border-collapse: collapse; 
            /* 标题放在下面 */
            caption-side: bottom;
            margin: 0 auto; /* 表格水平居中 */
        }

        /* 2. 设置单元格 (td, th) */
        td, th {
            /* 盒子模型写法：边框 */
            border: 1px solid blue; 
            height: 40px;
            
            /* 文字水平居中 */
            text-align: center; 
            /* 文字垂直居中 (默认即为middle，写出来为了保险) */
            vertical-align: middle; 
        }

        /* 3. 奇偶行变色 (进阶技巧，PPT未讲但常用) */
        tr:nth-child(even) {
            background-color: #f2f2f2;
        }
    </style>
</head>
<body>

    <table>
        <caption>2026年春季学期课程表</caption>
        <tr>
            <th>节次</th> <th>星期一</th> <th>星期二</th>
        </tr>
        <tr>
            <td>1-2节</td> <td>Web设计</td> <td>高等数学</td>
        </tr>
        <tr>
            <td>3-4节</td> <td>英语</td> <td>体育</td>
        </tr>
    </table>

</body>
</html>
```

