# block-closing-brace-space-after

要求在块的闭大括号之后必须有一个空格或不能有空白符。

```css
a { color: pink; }
/**              ↑
 * 这个大括号之后的空白符 */
```

此规则允许在块的闭括号之后使用尾随分号。例如，

```css
:root {
  --toolbar-theme: {
    background-color: hsl(120, 70%, 95%);
  };
/* ↑
 * 这个分号 */
}
```

## 选项

`string`: `"always"|"never"|"always-single-line"|"never-single-line"|"always-multi-line"|"never-multi-line"`

### `"always"`

在闭大括号之后*必须*有一个空格。

以下模式被视为违规：

```css
a { color: pink; }b { color: red; }
```

```css
a { color: pink; }
b { color: red; }
```

以下模式*不*被视为违规：

```css
a { color: pink; } b { color: red; }
```

### `"never"`

在闭大括号之后*不能*有空白符。

以下模式被视为违规：

```css
a { color: pink; } b { color: red; }
```

```css
a { color: pink; }
b { color: red; }
```

以下模式*不*被视为违规：

```css
a { color: pink; }b { color: red; }
```

```css
a { color: pink;
}b { color: red; }
```

### `"always-single-line"`

在单行块的闭大括号之后*必须*有一个空格。

以下模式被视为违规：

```css
a { color: pink; }b { color: red; }
```

以下模式*不*被视为违规：

```css
a { color: pink; } b { color: red; }
```

```css
a { color: pink;
}b { color: red; }
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

在多行块的闭大括号之后*必须*有一个空格。

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
} b { color: red; }
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
