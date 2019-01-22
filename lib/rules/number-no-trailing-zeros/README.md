# number-no-trailing-zeros

Disallow trailing zeros in numbers.

```css
a { top: 0.5000px; bottom: 1.0px; }
/**         ↑                ↑
 *        These trailing zeros */
```

The `--fix` option on the [command line](../../../docs/user-guide/cli.md#autofixing-errors) can automatically fix some of the problems reported by this rule.

## 选项

### `true`

以下模式被视为违规：

```css
a { top: 1.0px }
```

```css
a { top: 1.01000px }
```

The following patterns are *not* considered violations:

```css
a { top: 1px }
```

```css
a { top: 1.01px }
```
