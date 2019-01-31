# selector-pseudo-element-colon-notation

指定伪元素适用单冒号还是双冒号表示法。

```css
   a::before { color:pink; }
/** ↑
 * 这个符号 */
```

为伪元素使用 `::` 符号以在伪类（子类现有元素）和伪元素（未在文档树中表现的元素）之间建立区别。

但是，为了与现有样式表兼容，用户代理还接受 CSS 级别 1 和 2 中引入的伪元素前单冒号表示法（即：`:first-line`, `:first-letter`、`:before` 和 `:after`）。

[命令行](../../../docs/user-guide/cli.md#自动修复错误)中的 `--fix` 选项可以自动修复此规则报告的所有问题。

## 选项

`string`: `"single"|"double"`

### `"single"`

适用的伪元素*必须*使用单个冒号表示法。

以下模式被视为违规：

```css
a::before { color: pink; }
```

```css
a::after { color: pink; }
```

```css
a::first-letter { color: pink; }
```

```css
a::first-line { color: pink; }
```

以下模式*不*被视为违规：

```css
a:before { color: pink; }
```

```css
a:after { color: pink; }
```

```css
a:first-letter { color: pink; }
```

```css
a:first-line { color: pink; }
```

```css
input::placeholder { color: pink; }
```

```css
li::marker { font-variant-numeric: tabular-nums; }
```

### `"double"`

适用的伪元素*必须*使用双冒号表示法。

以下模式被视为违规：

```css
a:before { color: pink; }
```

```css
a:after { color: pink; }
```

```css
a:first-letter { color: pink; }
```

```css
a:first-line { color: pink; }
```

以下模式*不*被视为违规：

```css
a::before { color: pink; }
```

```css
a::after { color: pink; }
```

```css
a::first-letter { color: pink; }
```

```css
a::first-line { color: pink; }
```

```css
input::placeholder { color: pink; }
```

```css
li::marker { font-variant-numeric: tabular-nums; }
```
