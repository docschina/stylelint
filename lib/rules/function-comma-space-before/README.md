# function-comma-space-before

要求在函数的逗号之前必须有一个空格或不能有空白符。

```css
a { transform: translate(1 ,1) }
/**                        ↑
 *               这个逗号之前的空白符 */
```

[命令行](../../../docs/user-guide/cli.md#自动修复错误)中的 `--fix` 选项可以自动修复此规则报告的所有问题。

## 选项

`string`: `"always"|"never"|"always-single-line"|"never-single-line"`

### `"always"`

在逗号之前*必须*有一个空格。

以下模式被视为违规：

```css
a { transform: translate(1,1) }
```

```css
a { transform: translate(1, 1) }
```

以下模式*不*被视为违规：

```css
a { transform: translate(1 ,1) }
```

```css
a { transform: translate(1 , 1) }
```

### `"never"`

在逗号之前*不能*有空白符。

以下模式被视为违规：

```css
a { transform: translate(1 ,1) }
```

```css
a { transform: translate(1 , 1) }
```

以下模式*不*被视为违规：

```css
a { transform: translate(1,1) }
```

```css
a { transform: translate(1, 1) }
```

### `"always-single-line"`

在单行函数的逗号之前*必须*有一个空格。

以下模式被视为违规：

```css
a { transform: translate(1,1) }
```

```css
a { transform: translate(1, 1) }
```

以下模式*不*被视为违规：

```css
a { transform: translate(1 ,1) }
```

```css
a { transform: translate(1 , 1) }
```

```css
a {
  transform: translate(1,
    1)
}
```

### `"never-single-line"`

在单行函数的逗号之前*不能*有空白符。

以下模式被视为违规：

```css
a { transform: translate(1 ,1) }
```

```css
a { transform: translate(1 , 1) }
```

以下模式*不*被视为违规：

```css
a { transform: translate(1,1) }
```

```css
a { transform: translate(1, 1) }
```

```css
a {
  transform: translate(1 ,
    1)
}
```
