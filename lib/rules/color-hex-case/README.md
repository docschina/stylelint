# color-hex-case

Specify lowercase or uppercase for hex colors.

```css
a { color: #fff }
/**        ↑
 * These hex colors */
```

The `--fix` option on the [command line](../../../docs/user-guide/cli.md#autofixing-errors) can automatically fix all of the problems reported by this rule.

## 选项

`string`: `"lower"|"upper"`

### `"lower"`

以下模式被视为违规：

```css
a { color: #FFF; }
```

The following patterns are *not* considered violations:

```css
a { color: #000; }
```

```css
a { color: #fff; }
```

### `"upper"`

以下模式被视为违规：

```css
a { color: #fff; }
```

The following patterns are *not* considered violations:

```css
a { color: #000; }
```

```css
a { color: #FFF; }
```
