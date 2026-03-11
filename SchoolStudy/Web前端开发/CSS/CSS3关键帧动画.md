# CSS3 关键帧动画 (Keyframe Animations)
**教材章节**: 第3章 CSS样式基础 (动画)
**考点**: @keyframes 语法、简写属性顺序、infinite 与 alternate

## 1.  核心概念：剧本与播放
CSS 动画的制作分为两步：
1.  **写剧本**: 使用 `@keyframes` 定义动画的关键帧（从什么样变到什么样）。
2.  **播放**: 在选择器中调用这个动画（指定演多久、演几次）。

## 2. 第一步：定义动画 (@keyframes)
有两种写法，效果一样，但百分比写法更灵活。

### 写法 A: from...to (简单版)
```css
/* 定义一个叫 "aa" 的动画 */
@keyframes aa {
    from { background: red; }  /* 开始状态 */
    to   { background: blue; } /* 结束状态 */
}
```
### 写法 B: 百分比 (进阶版 - 推荐)
可以设置任意多个节点，适合复杂动画。

```css
@keyframes aa {
    0%   { background: red; }
    25%  { background: yellow; }
    50%  { background: pink; }
    100% { background: black; }
}
```

## 3.  第二步：调用动画 (Animation Properties)

定义好动画后，如果不调用，它是不生效的。我们需要在元素上设置以下属性：

| **属性名**                     | **作用**                     | **说明**                                          |
| --------------------------- | -------------------------- | ----------------------------------------------- |
| `animation-name`            | 动画名称                       | 必须对应 `@keyframes` 定义的名字。                        |
| `animation-duration`        | <font color="#c00000">持续时间 | **(必填)** 动画播完一次要多久 (如 </font>`5s`)。             |
| `animation-timing-function` | 速度曲线                       | `linear` (匀速), `ease` (默认, 慢-快-慢) 等。            |
| `animation-delay`           | 延迟时间                       | 等多久才开始播放。                                       |
| `animation-iteration-count` | **播放次数**                   | `1` (默认), `infinite` (==无限循环播放==)。              |
| `animation-direction`       | **播放方向**                   | `normal` (默认), `alternate` (==往返播放: 去-回-去-回==)。 |

## 4.  终极简写 (Shorthand) —— 考试必背

为了少写代码，我们通常使用简写属性 `animation`。

- 语法公式:
    
    `animation: name duration timing-function delay iteration-count direction;`
    
- **记忆口诀**: **名字 时间 曲线 延迟 次数 方向**
    
- **示例代码**:

```css
  /* 动画名aa, 持续5秒, 慢速开始, 延迟2秒, 播放4次, 往返播放 */
   animation: aa 5s ease-in-out 2s 4 alternate;
 ```


## 5. 教授的代码实战 (Example)

这是一个完整的红变蓝动画案例。


```css
<style>
    /* 1. 定义剧本 */
    @keyframes colorChange {
        from { background: red; }
        to   { background: blue; }
    }

    /* 2. 这里的盒子负责演出 */
    #box {
        width: 200px;
        height: 100px;
        background: red;
        
        /* 简写调用：名为colorChange, 5秒播完, 匀速, 无限循环, 往返(红变蓝,再蓝变红) */
        animation: colorChange 5s linear infinite alternate;
    }
</style>

<div id="box"></div>
```