# length-zero-no-unit

Disallow units for zero lengths.

```css
a { top: 0px; }
/**      ↑↑
 * This zero and this type of length unit */
```

*Lengths* refer to distance measurements. A length is a *dimension*, which is a *number* immediately followed by a *unit identifier*. However, for zero lengths the unit identifier is optional. The length units are: `em`, `ex`, `ch`, `vw`, `vh`, `cm`, `mm`, `in`, `pt`, `pc`, `px`, `rem`, `vmin`, and `vmax`.

The `--fix` option on the [command line](../../../docs/user-guide/cli.md#autofixing-errors) can automatically fix all of the problems reported by this rule.

## 选项

### `true`

以下模式被视为违规：

```css
a { top: 0px }
```

```css
a { top: 0.000em }
```

以下模式*不*被视为违规：

```css
a { top: 0 } /* no unit */
```

```css
a { transition-delay: 0s; } /* dimension */
```

```css
a { top: 2in; }
```

```css
a { top: 1.001vh }
```

## Optional secondary options

### `ignore: ["custom-properties"]`

#### `"custom-properties"`

Ignore units for zero length in custom properties.

The following pattern is *not* considered a violation:

```css
a { --x: 0px; }
```
