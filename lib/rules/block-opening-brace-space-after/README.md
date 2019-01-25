# block-opening-brace-space-after

要求在块的开大括号之后必须有一个空格或不能有空白符。

```css
  a { color: pink; }
/** ↑
 * 这个大括号之后的空白符 */
```

[命令行](../../../docs/user-guide/cli.md#自动修复错误)中的 `--fix` 选项可以自动修复此规则报告的所有问题。

## 选项

`string`: `"always"|"never"|"always-single-line"|"never-single-line"|"always-multi-line"|"never-multi-line"`

### `"always"`

在开大括号之后*必须*有一个空格。

以下模式被视为违规：

```css
a {color: pink; }
```

```css
a {
color: pink; }
```

以下模式*不*被视为违规：

```css
a { color: pink; }
```

```css
a { color: pink;
}
```

### `"never"`

在开大括号之后*不能*有空白符。

以下模式被视为违规：

```css
a { color: pink; }
```

```css
a {
color: pink; }
```

以下模式*不*被视为违规：

```css
a {color: pink; }
```

```css
a
{color: pink; }
```

### `"always-single-line"`

在单行块的开大括号之后*必须*有一个空格。

以下模式被视为违规：

```css
a {color: pink; }
```

以下模式*不*被视为违规：

```css
a { color: pink; }
```

```css
a {color: pink;
}
```

### `"never-single-line"`

在单行块的开大括号之后*不能*有空白符。

以下模式被视为违规：

```css
a { color: pink; }
```

以下模式*不*被视为违规：

```css
a {color: pink; }
```

```css
a { color: pink;
}
```

### `"always-multi-line"`

在多行块的开大括号之后*必须*有一个空格。

以下模式被视为违规：

```css
a {color: pink;
}
```

以下模式*不*被视为违规：

```css
a {color: pink; }
```

```css
a { color: pink;
}
```

### `"never-multi-line"`

在多行块的开大括号之后*不能*有空白符。

以下模式被视为违规：

```css
a { color: pink;
}
```

以下模式*不*被视为违规：

```css
a { color: pink; }
```

```css
a {color: pink;
}
```
