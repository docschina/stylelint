# block-opening-brace-newline-before

要求在块的开大括号之前必须有换行符或不能有空白符。

```css
  a
    { color: pink; }
/** ↑
 * 这个大括号之前的换行符 */
```

有关将此规则与 [`block-opening-brace-newline-after`](../block-opening-brace-newline-after/README.md) 一起使用的更多信息，请参阅[常见问题](../../../docs/user-guide/faq.md#如何禁用单行代码块)禁止单行规则。

[命令行](../../../docs/user-guide/cli.md#自动修复错误)中的 `--fix` 选项可以自动修复此规则报告的所有问题。

## 选项

`string`: `"always"|"always-single-line"|"never-single-line"|"always-multi-line"|"never-multi-line"`

### `"always"`

在开大括号之前*必须*有一个换行符。

以下模式被视为违规：

```css
a{ color: pink; }
```

```css
a{ color: pink;
}
```

以下模式*不*被视为违规：

```css
a
{ color: pink; }
```

```css
a
{
color: pink; }
```

```css
a /* foo */
  {
    color: pink;
  }
```

### `"always-single-line"`

在单行块的开大括号之前*必须*有一个换行符。

以下模式被视为违规：

```css
a{ color: pink; }
```

以下模式*不*被视为违规：

```css
a
{ color: pink; }
```

```css
a{
color: pink; }
```

### `"never-single-line"`

在单行块的开大括号之前*不能*有空白符。

以下模式被视为违规：

```css
a { color: pink; }
```

以下模式*不*被视为违规：

```css
a{ color: pink; }
```

```css
a {
color: pink; }
```

### `"always-multi-line"`

在多行块的开大括号之前*必须*有一个换行符。

以下模式被视为违规：

```css
a{
color: pink; }
```

```css
a {
color: pink; }
```

以下模式*不*被视为违规：

```css
a{ color: pink; }
```

```css
a { color: pink; }
```

```css
a
{ color: pink; }
```

```css
a
{
color: pink; }
```

### `"never-multi-line"`

在多行块的开大括号之前*不能*有空白符。

以下模式被视为违规：

```css
a {
color: pink; }
```

以下模式*不*被视为违规：

```css
a { color: pink; }
```

```css
a{
color: pink;}
```
