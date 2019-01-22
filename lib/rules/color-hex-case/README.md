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

以下模式*不*被视为违规：

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

以下模式*不*被视为违规：

```css
a { color: #000; }
```

```css
a { color: #FFF; }
```
