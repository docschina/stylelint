# selector-list-comma-space-before

Require a single space or disallow whitespace before the commas of selector lists.

```css
   a ,b { color: pink; }
/**  ↑
 * The space before this comma */
```

The `--fix` option on the [command line](../../../docs/user-guide/cli.md#autofixing-errors) can automatically fix all of the problems reported by this rule.

## 选项

`string`: `"always"|"never"|"always-single-line"|"never-single-line"`

### `"always"`

There *must always* be a single space before the commas.

以下模式被视为违规：

```css
a,b { color: pink; }
```

```css
a, b { color: pink; }
```

The following patterns are *not* considered violations:

```css
a ,b { color: pink; }
```

```css
a , b { color: pink; }
```

### `"never"`

There *must never* be whitespace before the commas.

以下模式被视为违规：

```css
a ,b { color: pink; }
```

```css
a , b { color: pink; }
```

The following patterns are *not* considered violations:

```css
a,b { color: pink; }
```

```css
a, b { color: pink; }
```

### `"always-single-line"`

There *must always* be a single space before the commas in single-line selector lists.

以下模式被视为违规：

```css
a,b { color: pink; }
```

The following patterns are *not* considered violations:

```css
a,
b { color: pink; }
```

### `"never-single-line"`

There *must never* be a single space before the commas in single-line selector lists.

以下模式被视为违规：

```css
a ,b { color: pink; }
```

The following patterns are *not* considered violations:

```css
a ,
b { color: pink; }
```
