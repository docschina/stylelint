# color-hex-length

Specify short or long notation for hex colors.

```css
a { color: #fff }
/**        ↑
 * These hex colors */
```

The `--fix` option on the [command line](../../../docs/user-guide/cli.md#autofixing-errors) can automatically fix all of the problems reported by this rule.

## 选项

`string`: `"short"|"long"`

### `"short"`

以下模式被视为违规：

```css
a { color: #ffffff; }
```

```css
a { color: #ffffffaa; }
```

以下模式*不*被视为违规：

```css
a { color: #fff; }
```

```css
a { color: #fffa; }
```

```css
a { color: #a4a4a4; }
```

### `"long"`

以下模式被视为违规：

```css
a { color: #fff; }
```

```css
a { color: #fffa; }
```

以下模式*不*被视为违规：

```css
a { color: #ffffff; }
```

```css
a { color: #ffffffaa; }
```
