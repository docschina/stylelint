# declaration-block-semicolon-newline-after

要求在声明块的分号之后必须有换行符或不能有空白符。

```css
a {
  color: pink;
  top: 0;    ↑
}            ↑
/**          ↑
 * 这个分号之后的换行符 */
```

此规则忽略：

-   Less mixins 的分号
-   声明块的最后一个分号

使用 `block-closing-brace-*-before` 规则来控制最后一个分号和闭括号之间的空白符。

此规则允许行尾注释后跟换行符。例如：

```css
a {
  color: pink; /* 行尾注释 */
  top: 0;
}
```

[命令行](../../../docs/user-guide/cli.md#自动修复错误)中的 `--fix` 选项可以自动修复此规则报告的所有问题。

## 选项

`string`: `"always"|"always-multi-line"|"never-multi-line"`

### `"always"`

在分号之后*必须*有一个换行符。

以下模式被视为违规：

```css
a { color: pink; top: 0; }
```

```css
a {
  color: pink; /* 包含换行符的
    行尾注释 */
  top: 0;
}
```

以下模式*不*被视为违规：

```css
a {
  color: pink;
  top: 0;
}
```

```css
a {
  color: pink; /* 行尾注释 */
  top: 0;
}
```

### `"always-multi-line"`

在多行规则的分号之后*必须*有一个换行符。

以下模式被视为违规：

```css
a {
  color: pink; top: 0;
}
```

以下模式*不*被视为违规：

```css
a { color: pink; }
```

```css
a { color: pink; top: 0; }
```

```css
a {
  color: pink;
  top: 0;
}
```

### `"never-multi-line"`

在多行规则的分号之后*不能*有空白符。

以下模式被视为违规：

```css
a {
  color: pink;
  top: 0;
}
```

以下模式*不*被视为违规：

```css
a { color: pink; }
```

```css
a { color: pink; top: 0; }
```

```css
a {
  color: pink
  ; top: 0;
}
```
