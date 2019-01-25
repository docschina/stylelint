# declaration-block-semicolon-newline-before

要求在声明块的分号之前必须有换行符或不能有空白符。

```css
  a {
    color: pink
    ; top: 0;
  } ↑
/** ↑
 * 这个分号之前的换行符 */
```

此规则忽略 Less mixins 的分号。

## 选项

`string`: `"always"|"always-multi-line"|"never-multi-line"`

### `"always"`

在分号之前*必须*有一个换行符。

以下模式被视为违规：

```css
a { color: pink; }
```

```css
a {
  color: pink; top: 0;
}
```

以下模式*不*被视为违规：

```css
a { color: pink
; }
```

```css
a {
  color: pink
  ; top: 0;
}
```

### `"always-multi-line"`

在多行规则的分号之前*必须*有一个换行符。

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
  color: pink
  ; top: 0;
}
```

### `"never-multi-line"`

在多行规则的分号之前*不能*有空白符。

以下模式被视为违规：

```css
a {
  color: pink
  ; top: 0;
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
