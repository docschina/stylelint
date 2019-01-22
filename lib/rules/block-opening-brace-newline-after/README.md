# block-opening-brace-newline-after

Require a newline after the opening brace of blocks.

```css
  a {
    ↑ color: pink; }
/** ↑
 * The newline after this brace */
```

This rule allows an end-of-line comment followed by a newline. For example,

```css
a { /* end-of-line comment */
  color: pink;
}
```

Refer to [the FAQ](../../../docs/user-guide/faq.md#how-do-i-disallow-single-line-blocks) for more information on using this rule with [`block-opening-brace-newline-before`](../block-opening-brace-newline-before/README.md) to disallow single-line rules.

The `--fix` option on the [command line](../../../docs/user-guide/cli.md#autofixing-errors) can automatically fix all of the problems reported by this rule.

## 选项

`string`: `"always"|"always-multi-line"|"never-multi-line"`

### `"always"`

There *must always* be a newline after the opening brace.

以下模式被视为违规：

```css
a{ color: pink; }
```

```css
a{ color: pink;
}
```

```css
a{ /* end-of-line comment
  with a newline */
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
a { /* end-of-line comment */
  color: pink;
}
```

### `"always-multi-line"`

There *must always* be a newline after the opening brace in multi-line blocks.

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

There *must never* be whitespace after the opening brace in multi-line blocks.

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
