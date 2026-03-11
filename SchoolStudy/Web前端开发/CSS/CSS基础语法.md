# CSS 基础语法 (CSS Basics)
**教材章节**: #第3章CSS样式基础
**考点类型**: 单选、填空、手写代码规范

## 1. 核心定义
* **全称**: <span style="background:#fff88f">Cascading Style Sheets </span>(层叠样式表)。
* **作用**: 实现网页 **结构(HTML)** 与 **表现(CSS)** 的分离。
    * *HTML*: 骨架 (内容)
    * *CSS*: 皮肤 (样式、布局)

## 2. 语法结构 (必须背诵默写)
CSS 规则由两个主要部分构成：**选择器** + **一条或多条声明**。

```css
选择器 {
    属性1: 属性值1;
    属性2: 属性值2;
}
```
- **选择器 (Selector)**: 指向需要改变样式的 HTML 元素 (如 `p`, `h1`, `.class-name`)。
    
- **声明 (Declaration)**: 包含 `属性: 值`。
    
    - 每条声明以英文分号 `;` 结尾。
        
    - 属性和值之间用英文冒号 `:` 分隔。

## 3. ⚠️ 易错点 (考试避坑指南)

1. **大小写**:
    
    - CSS <span style="background:rgba(240, 200, 0, 0.2)">选择器</span><span style="background:rgba(236, 57, 57, 0.55)">严格区分大小写</span>（尤其是类名和ID）。
        
    - <span style="background:rgba(240, 200, 0, 0.2)">属性和值</span>通常不区分，但<span style="background:rgba(236, 57, 57, 0.55)">建议统一小写</span>。
        
2. **复合词值**:
    
    - 如果属性值<span style="background:rgba(240, 200, 0, 0.2)">包含空格</span>（如字体），<span style="background:rgba(236, 57, 57, 0.55)">必须加引号</span>。
        
    - 例: `font-family: "Arial Black";` ✅
        
3. **单位空格**:
    
    - <span style="background:rgba(240, 200, 0, 0.2)">数值和单位</span>之间<span style="background:rgba(236, 57, 57, 0.55)">严禁空格</span>。
        
    - 例: `width: 20px;` ✅ | `width: 20 px;` ❌ (错误!)
    
4. **注释写法**:
    
    - 语法: `/* 注释内容 */`
        
    - 注意: CSS 不支持 `//` 注释，那是 JS 的写法，考试写错不得分。
    

## 4. 示例代码


```css
/* 设置段落样式 */
p {
    font-weight: bold;      /* 粗体 */
    font-size: 30px;        /* 字号30像素 */
    font-family: "SimHei";  /* 字体黑体 */
}
```

---