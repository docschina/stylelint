# block-opening-brace-newline-after

要求在块的开大括号之后必须有换行符。

```css
  a {
    ↑ color: pink; }
/** ↑
 * 这个大括号之后的换行符 */
```

此规则允许行尾注释后跟换行符。例如：

```css
a { /* 行尾注释 */
  color: pink;
}
```

有关将此规则与[`block-opening-brace-newline-before`](../block-opening-brace-newline-before/README.md) 一起使用的更多信息，请参阅[常见问题](../../../docs/user-guide/faq.md#如何禁用单行代码块)禁止单行规则。

[命令行](../../../docs/user-guide/cli.md#自动修复错误)中的 `--fix` 选项可以自动修复此规则报告的所有问题。

## 选项

`string`: `"always"|"always-multi-line"|"never-multi-line"`

### `"always"`

在开大括号之后*必须*有一个换行符。

以下模式被视为违规：

```css
a{ color: pink; }
```

```css
a{ color: pink;
}
```

```css
a{ /* 包含换行符的
    行尾注释 */
  color: pink;
}
```

以下模式*不*被视为违规：

```css
a {
color: pink; }
```

```css
a
{
color: pink; }
```

```css
a { /* 行尾注释 */
  color: pink;
}
```

### `"always-multi-line"`

在多行块的开大括号之后*必须*有一个换行符。

以下模式被视为违规：

```css
a{color: pink;
}
```

以下模式*不*被视为违规：

```css
a { color: pink; }
```

```css
a {
color: pink; }
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
