# block-closing-brace-newline-after

要求在块的闭大括号之后必须有换行符或不能有空白符。

```css
a { color: pink; }
a { color: red; }↑
/**              ↑
 * 这个大括号之后的换行符 */
```

此规则允许用空格分隔的行尾注释, 只要注释不包含换行符即可。例如,

```css
a {
  color: pink;
} /* 行尾注释 */
```

此规则允许在块的闭大括号之后使用尾随分号。例如，

```css
:root {
  --toolbar-theme: {
    background-color: hsl(120, 70%, 95%);
  };
/* ↑
 * 这个分号 */
}
```

[命令行](../../../docs/user-guide/cli.md#自动修复错误)中的 `--fix` 选项可以自动修复此规则报告的所有问题。

## 选项

`string`: `"always"|"always-single-line"|"never-single-line"|"always-multi-line"|"never-multi-line"`

### `"always"`

在闭大括号之后*必须*有一个换行符。

以下模式被视为违规：

```css
a { color: pink; }b { color: red; }
```

```css
a { color: pink;
} b { color: red; }
```

以下模式*不*被视为违规：

```css
a { color: pink; }
b { color: red; }
```

### `"always-single-line"`

在单行块的闭大括号之后*必须*有一个换行符。

以下模式被视为违规：

```css
a { color: pink; } b { color: red; }
```

以下模式*不*被视为违规：

```css
a { color: pink;
} b { color: red; }
```

```css
a { color: pink; }
b { color: red; }
```

### `"never-single-line"`

在单行块的闭大括号之后*不能*有空白符。

以下模式被视为违规：

```css
a { color: pink; } b { color: red; }
```

以下模式*不*被视为违规：

```css
a { color: pink; }b { color: red; }
```

```css
a { color: pink;
} b { color: red; }
```

### `"always-multi-line"`

在多行块的闭大括号之后*必须*有一个换行符。

以下模式被视为违规：

```css
a { color: pink;
}b { color: red; }
```

以下模式*不*被视为违规：

```css
a { color: pink; }b { color: red; }
```

```css
a { color: pink;
}
b { color: red; }
```

### `"never-multi-line"`

在多行块的闭大括号之后*不能*有空白符。

以下模式被视为违规：

```css
a { color: pink;
} b { color: red; }
```

以下模式*不*被视为违规：

```css
a { color: pink; } b { color: red; }
```

```css
a { color: pink;
}b { color: red; }
```

## 可选的辅助选项

### `ignoreAtRules: ["/regex/", "non-regex"]`

忽略指定的 @规则。

例如，使用 `"always"` 或 `"always-multi-line"`。

给定：

```js
["if", "else"]
```

以下模式*不*被视为违规：

```css
@if ($var) {
  color: pink;
} @else if ($var2) {
  color: red;
} @else {
  color: blue;
}
```

```css
@if ($var) { color: pink; } @else { color: blue; }
```
