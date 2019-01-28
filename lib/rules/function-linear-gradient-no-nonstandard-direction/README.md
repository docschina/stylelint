# function-linear-gradient-no-nonstandard-direction

禁止在 `linear-gradient()` 中调用不符合[标准语法](https://developer.mozilla.org/zh-CN/docs/Web/CSS/linear-gradient#语法)的无效方向值。

```css
.foo { background: linear-gradient(to top, #fff, #000); }
/**                                ↑
 *                  这第一个参数（可选）是“方向” */
```

有效的标准方向值是以下之一：

-   一个角度
-   `to ` 加上一个方位（`to top`、`to bottom`、`to left`、`to right`；`to top right`, `to right top`、`to bottom left` 等等。）

一个常见的错误（匹配过时的非标准语法）是只使用一个前面没有 `to` 的方位。

## 选项

### `true`

以下模式被视为违规：

```css
.foo { background: linear-gradient(top, #fff, #000); }
```

```css
.foo { background: linear-gradient(bottom, #fff, #000); }
```

```css
.foo { background: linear-gradient(left, #fff, #000); }
```

```css
.foo { background: linear-gradient(45, #fff, #000); }
```

```css
.foo { background: linear-gradient(to top top, #fff, #000); }
```

以下模式*不*被视为违规：

```css
.foo { background: linear-gradient(to top, #fff, #000); }
```

```css
.foo { background: linear-gradient(to bottom right, #fff, #000); }
```

```css
.foo { background: linear-gradient(45deg, #fff, #000); }
```

```css
.foo { background: linear-gradient(1.57rad, #fff, #000); }
```

```css
/* 方向默认为 "to bottom" */
.foo { background: linear-gradient(#fff, #000); }
```
