# block-opening-brace-newline-before

Require a newline or disallow whitespace before the opening brace of blocks.

```css
  a
    { color: pink; }
/** ↑
 * The newline before this brace */
```

Refer to [the FAQ](../../../docs/user-guide/faq.md#how-do-i-disallow-single-line-blocks) for more information on using this rule with [`block-opening-brace-newline-after`](../block-opening-brace-newline-after/README.md) to disallow single-line rules.

The `--fix` option on the [command line](../../../docs/user-guide/cli.md#autofixing-errors) can automatically fix all of the problems reported by this rule.

## 选项

`string`: `"always"|"always-single-line"|"never-single-line"|"always-multi-line"|"never-multi-line"`

### `"always"`

There *must always* be a newline before the opening brace.

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

There *must always* be a newline before the opening brace in single-line blocks.

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

There *must never* be whitespace before the opening brace in single-line blocks.

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

There *must always* be a newline before the opening brace in multi-line blocks.

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

There *must never* be whitespace before the opening brace in multi-line blocks.

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
