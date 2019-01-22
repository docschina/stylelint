# media-feature-parentheses-space-inside

Require a single space or disallow whitespace on the inside of the parentheses within media features.

```css
@media ( max-width: 300px ) {}
/**    ↑                  ↑
 * The space inside these two parentheses */
```

The `--fix` option on the [command line](../../../docs/user-guide/cli.md#autofixing-errors) can automatically fix all of the problems reported by this rule.

## 选项

`string`: `"always"|"never"`

### `"always"`

There *must always* be a single space inside the parentheses.

以下模式被视为违规：

```css
@media (max-width: 300px) {}
```

```css
@media (max-width: 300px ) {}
```

以下模式*不*被视为违规：

```css
@media ( max-width: 300px ) {}
```

### `"never"`

There *must never* be whitespace on the inside the parentheses.

以下模式被视为违规：

```css
@media ( max-width: 300px ) {}
```

```css
@media ( max-width: 300px) {}
```

以下模式*不*被视为违规：

```css
@media (max-width: 300px) {}
```
