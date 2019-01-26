# declaration-colon-space-after

要求在声明块的冒号之后必须有一个空格或不能有空白符。

```css
a { color: pink }
/**      ↑
 * 这个冒号之后的空白符 */
```

[命令行](../../../docs/user-guide/cli.md#自动修复错误)中的 `--fix` 选项可以自动修复此规则报告的所有问题。

## 选项

`string`: `"always"|"never"|"always-single-line"`

### `"always"`

在冒号之后*必须*有一个空格。

以下模式被视为违规：

```css
a { color :pink }
```

```css
a { color:pink }
```

以下模式*不*被视为违规：

```css
a { color : pink }
```

```css
a { color: pink }
```

### `"never"`

在冒号之后*不能*有空白符。

以下模式被视为违规：

```css
a { color:pink }
```

```css
a { color :pink }
```

以下模式*不*被视为违规：

```css
a { color :pink }
```

```css
a { color:pink }
```

### `"always-single-line"`

*如果声明的值为单行*，则冒号之后*必须*有一个空格。

以下模式被视为违规：

```css
a {
  box-shadow:0 0 0 1px #5b9dd9, 0 0 2px 1px rgba(30, 140, 190, 0.8);
}
```

以下模式*不*被视为违规：

```css
a {
  box-shadow: 0 0 0 1px #5b9dd9, 0 0 2px 1px rgba(30, 140, 190, 0.8);
}
```

```css
a {
  box-shadow:
    0 0 0 1px #5b9dd9,
    0 0 2px 1px rgba(30, 140, 190, 0.8);
}
```

```css
a {
  box-shadow:0 0 0 1px #5b9dd9,
    0 0 2px 1px rgba(30, 140, 190, 0.8);
}
```
