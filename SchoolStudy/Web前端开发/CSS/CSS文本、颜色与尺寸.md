# CSS 文本、颜色与尺寸 (Text, Color & Dimensions)

**考点**: #相对单位计算  #透明度区别 #字体回退机制

## 1.  CSS 尺寸单位 (Dimensions)

| 类型       | 单位         | 说明          | 考试重点                                     |
| :------- | :--------- | :---------- | :--------------------------------------- |
| **绝对尺寸** | **px**     | 像素 (Pixel)  | 最常用，固定大小，不随浏览器设置变化。                      |
|          | in, cm, mm | 英寸、厘米、毫米    | 网页开发中极少使用，主要用于打印样式。                      |
| **相对尺寸** | **em**     | 相对当前元素的字体大小 | **难点**: 若用于 `font-size`，则相对于**父元素**字体大小。 |
|          | **rem**    | Root em     | 相对于==根元素 (< html >)== 的字体大小。==响应式布局==神器。 |
|          | **%**      | 百分比         | 相对于==父元素==属性的百分比。                        |

## 2. CSS 颜色表示 (Colors)
网页中常用的几种颜色表达方式：

1.  **关键字**: 如 `red`, `blue`, `transparent` (透明)。
2.  **十六进制 (Hex)**: `#RRGGBB`。
    * 简写规则: `#FF0000` -> `#F00` (当每两位的字符相同时可简写)。
    *  RR 红、GG 绿、BB 蓝
	- 每一对是 **00 ~ FF**（0~255）
	- 例子：`#FF0000` 红
		  `#00FF00` 绿
		  `#0000FF` 蓝
	      `#000000` 黑
	      `#FFFFFF` 白
3.  **RGB / RGBA**:
    * `rgb(255, 0, 0)`: 纯红。
    * `rgba(255, 0, 0, 0.5)`: **A (Alpha)** 代表透明度，0~1之间 (<span style="background:rgba(236, 57, 57, 0.55)">0透明，1不透明</span>)。
4.  **HSL / HSLA**: 色相(Hue), 饱和度(Saturation), 亮度(Lightness)。
    * 考点少，但需知道 `hsl(0, 100%, 50%)` 是红色。

###  核心考点：Opacity vs RGBA
* `opacity: 0.5`: <span style="background:rgba(240, 107, 5, 0.2)">整个元素</span>（包括**背景和里面的文字**）都变成半透明。
- ` background-color: rgba(...)`: 只有**背景**变透明，上面的文字不受影响。

## 3. 字体样式 (Typography)

| 属性              | 说明   | 关键考点 (Tips)                                                                                                                    |
| :-------------- | :--- | :----------------------------------------------------------------------------------------------------------------------------- |
| **font-family** | 字体名称 | 1. 多个字体用<span style="background:rgba(173, 239, 239, 0.55)">逗号</span>隔开 (回退机制)。<br>2. 字体名==包含空格必须加引号== (如 `"Times New Roman"`)。 |
| **font-size**   | 字体大小 | 常用 `px`，也可用 `em` 或 `rem`。                                                                                                      |
| **font-weight** | 字体粗细 | `normal` (400), `bold` (700)。<br>可用数字 100-900 精细控制。                                                                            |
| **font-style**  | 字体风格 | `normal` (正常), `italic` (斜体), `oblique` (倾斜)。                                                                                  |
>[!TIP] 教授的“避坑指南” (Professor's Tips)
>1.**字体全家桶 (Font Family)**：**Fallback (回退)**：`font-family: "Microsoft YaHei", Arial, sans-serif;` 
>**解释**：浏览器会先找“微软雅黑”，没有就找“Arial”，还没有就随便找个系统默认的“无衬线字体” (sans-serif)。
>**考试坑点**：**“sans-serif” 这种通用字体族名永远不要加引号！** 
>2. **继承性陷阱**： `text-` 开头的属性（如 `text-align`）和 `font-` 开头的属性通常可以**继承**。
但是！`<a>` 标签的颜色 (`color`) 是个特例，它通常**不会**继承父元素的颜色（因为它有浏览器默认样式覆盖），必须直接选中 `<a>` 修改。
# CSS 文本排版与 Font 简写 (Advanced Text & Font Shorthand)

**考点**: 文本对齐、缩进单位、font 简写顺序 (必考!)

## 1.  文本排版属性 (Text Layout)

| 属性                  | 说明     | 常用值 & 考试重点                                                                                          |
| :------------------ | :----- | :-------------------------------------------------------------------------------------------------- |
| **text-align**      | 水平对齐方式 | `left` (默认), `right`, `center` (居中), `justify` (两端对齐)。<br>⚠️ **注意**: 仅控制元素**内部**文字或图片的对齐，不能让盒子本身居中。 |
| **text-indent**     | 首行缩进   | **推荐单位**: `em` (字符宽度)。<br>例: `text-indent: 2em;` (标准段落缩进2个字)。                                       |
| **text-decoration** | 文本修饰   | `none` (**最常用**: ==去除链接下划线==), `underline` (下划线), `line-through` (删除线)。                             |
| **text-transform**  | 大小写转换  | `uppercase` (==全大写==), `lowercase` (==全小写==), `capitalize` (==首字母大写==)。                             |
| **line-height**     | 行高     | 控制行间距。常用技巧: **设置行高等于容器高度**，可实现单行文本**垂直居中**。                                                         |

## 2.  Font 属性简写 (The "Mega" Shorthand) —— 核心考点
CSS 允许将所有字体属性合并写在一个 `font` 属性中，但必须严格遵守**顺序**和**必选项**规则。

### 语法公式 (背诵):
`font: [style] [weight] size[/line-height] family;`

### 示例代码:
```css
/* 完整写法: 斜体, 粗体, 字号20px, 行高30px, 字体微软雅黑 */
p {
    font: italic bold 20px/30px "Microsoft YaHei";
}
```

>[!TIP] ⚠️ 考场避坑指南 (Rules of Font):
>1. **必选项**: `font-size` 和 `font-family` **必须写**，且必须放在**最后**两个位置。如果省略这两个中的任何一个，整行代码失效！
>2. **顺序**: 风格(`style`)和粗细(`weight`)必须在字号(`size`)之前。
>3. **斜杠**: 行高(`line-height`)必须紧跟在字号后面，用 `/` 隔开 (如 `16px/1.5`)。


>[!CAUTION] 教授的“辨析时刻” (Concept Check):**“让文字居中”** 和 **“让盒子居中”**
>1. **`text-align: center;`** 
> **作用对象**: 盒子里的**内容** (文字、图片)。 
>  **效果**: 就像你在 Word 里点的“居中对齐”按钮。  
>2. **`margin: 0 auto;`** 
> **作用对象**: **盒子本身** (块级元素)。 
> **效果**: 让这个盒子在它的父容器里左右居中（前提是盒子得有宽度）。


## 3. ✨ 进阶文本特效 (Advanced Effects) —— 加分项

### 3.1 文字阴影 (text-shadow)
* **语法**: `text-shadow: h-shadow v-shadow blur color;`
* **参数**: 水平偏移、垂直偏移、模糊距离、颜色。
* **示例**:
    ```css
    /* 向右移2px，向下移3px，模糊5px，灰色阴影 */
    h1 {
        text-shadow: 2px 3px 5px #ccc; 
    }
    ```

### 3.2 单行文本溢出省略 (必考套路!)
如何让一行过长的文字显示为“...”？这通常需要 **3行代码配合使用**：

```css
.ellipsis {
    white-space: nowrap;      /* 1. 强制不换行 */
    overflow: hidden;         /* 2. 超出部分隐藏 */
    text-overflow: ellipsis;  /* 3. 超出部分显示省略号 (...) */
}
```
### 3.3 强制换行 (Word Wrap)

当遇到很长的英文单词（如URL）撑破盒子时使用：

- **代码**: `word-wrap: break-word;` (允许长单词换行到下一行)。
## 4.自定义字体 (@font-face)

允许在网页中使用用户电脑里没有安装的字体（服务器字体）。

```css
@font-face {
    font-family: "MyCustomFont";   /* 给字体起个名字 */
    src: url("fonts/myfont.ttf");  /* 字体文件路径 */
}

p {
    font-family: "MyCustomFont";   /* 使用刚才定义的字体 */
}
```




