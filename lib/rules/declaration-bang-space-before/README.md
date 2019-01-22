# declaration-bang-space-before

Require a single space or disallow whitespace before the bang of declarations.

```css
a { color: pink !important; }
/**             ↑
 * The space before this exclamation mark */
```

The `--fix` option on the [command line](../../../docs/user-guide/cli.md#autofixing-errors) can automatically fix all of the problems reported by this rule.

## 选项

`string`: `"always"|"never"`

### `"always"`

There *must always* be a single space before the bang.

以下模式被视为违规：

```css
a { color: pink!important; }
```

```css
a { color: pink  ! important; }
```

以下模式*不*被视为违规：

```css
a { color: pink !important; }
```

```css
a { color:pink ! important; }
```

### `"never"`

There *must never* be whitespace before the bang.

以下模式被视为违规：

```css
a { color : pink !important; }
```

以下模式*不*被视为违规：

```css
a { color: pink!important; }
```

```css
a { color: pink! important; }
```
