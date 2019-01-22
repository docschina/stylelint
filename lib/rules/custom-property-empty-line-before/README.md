# custom-property-empty-line-before

Require or disallow an empty line before custom properties.

```css
a {
  top: 10px;
                          /* ← */
  --foo: pink;            /* ↑ */
}                         /* ↑ */
/**                          ↑
 *                   This line */
```

The `--fix` option on the [command line](../../../docs/user-guide/cli.md#autofixing-errors) can automatically fix all of the problems reported by this rule. We recommend to enable [`indentation`](../indentation/README.md) rule for better autofixing results with this rule.

## 选项

`string`: `"always"|"never"`

### `"always"`

以下模式被视为违规：

```css
a {
  top: 10px;
  --foo: pink;
  --bar: red;
}
```

以下模式*不*被视为违规：

```css
a {
  top: 10px;

  --foo: pink;

  --bar: red;
}
```

### `"never"`

以下模式被视为违规：

```css
a {
  top: 10px;

  --foo: pink;

  --bar: red;
}
```

```css
a {

  --foo: pink;
  --bar: red;
}
```

以下模式*不*被视为违规：

```css
a {
  top: 10px;
  --foo: pink;
  --bar: red;
}
```

```css
a {
  --foo: pink;
  --bar: red;
}
```

## Optional secondary options

### `except: ["after-comment", "after-custom-property", "first-nested"]`

#### `"after-comment"`

Reverse the primary option for custom properties that come after a comment.

Shared-line comments do not trigger this option.

例如，使用 `"always"`：

以下模式被视为违规：

```css
a {

  --foo: pink;
  /* comment */

  --bar: red;
}
```

```css
a {

  --foo: pink; /* comment */
  --bar: red;
}
```

以下模式*不*被视为违规：

```css
a {

  --foo: pink;
  /* comment */
  --bar: red;
}
```

```css
a {

  --foo: pink; /* comment */

  --bar: red;
}
```

#### `"after-custom-property"`

Reverse the primary option for custom properties that come after another custom property.

Shared-line comments do not affect this option.

例如，使用 `"always"`：

以下模式被视为违规：

```css
a {

  --foo: pink;

  --bar: red;
}
```

```css
a {

  --foo: pink; /* comment */

  --bar: red;
}
```

以下模式*不*被视为违规：

```css
a {

  --foo: pink;
  --bar: red;
}
```

```css
a {

  --foo: pink; /* comment */
  --bar: red;
}
```

#### `"first-nested"`

Reverse the primary option for custom properties that are nested and the first child of their parent node.

例如，使用 `"always"`：

以下模式被视为违规：

```css
a {

  --foo: pink;

  --bar: red;
}
```

以下模式*不*被视为违规：

```css
a {
  --foo: pink;

  --bar: red;
}
```

### `ignore: ["after-comment", "first-nested", "inside-single-line-block"]`

#### `"after-comment"`

Ignore custom properties that are preceded by comments.

例如，使用 `"always"`：

以下模式*不*被视为违规：

```css
a {
  /* comment */
  --foo: pink;
}
```

#### `"first-nested"`

Ignore custom properties that are nested and the first child of their parent node.

例如，使用 `"always"`：

以下模式*不*被视为违规：

```css
a {
  --foo: pink;

  --bar: red;
}
```

#### `"inside-single-line-block"`

Ignore custom properties that are inside single-line blocks.

例如，使用 `"always"`：

以下模式*不*被视为违规：

```css
a { --foo: pink; --bar: red; }
```
