# media-feature-colon-space-after

Require a single space or disallow whitespace after the colon in media features.

```css
@media (max-width: 600px) {}
/**              ↑
 * The space after this colon */
```

The `--fix` option on the [command line](../../../docs/user-guide/cli.md#autofixing-errors) can automatically fix all of the problems reported by this rule.

## 选项

`string`: `"always"|"never"`

### `"always"`

There *must always* be a single space after the colon.

以下模式被视为违规：

```css
@media (max-width:600px) {}
```

```css
@media (max-width :600px) {}
```

以下模式*不*被视为违规：

```css
@media (max-width: 600px) {}
```

```css
@media (max-width : 600px) {}
```

### `"never"`

There *must never* be whitespace after the colon.

以下模式被视为违规：

```css
@media (max-width: 600px) {}
```

```css
@media (max-width : 600px) {}
```

以下模式*不*被视为违规：

```css
@media (max-width:600px) {}
```

```css
@media (max-width :600px) {}
```
