# selector-attribute-operator-space-before

Require a single space or disallow whitespace before operators within attribute selectors.

```css
[target =_blank]
/**     ↑
 * The space before operator */
```

The `--fix` option on the [command line](../../../docs/user-guide/cli.md#autofixing-errors) can automatically fix all of the problems reported by this rule.

## 选项

`string`: `"always"|"never"`

### `"always"`

There *must always* be a single space before the operator.

以下模式被视为违规：

```css
[target=_blank] {}
```

```css
[target= _blank] {}
```

```css
[target='_blank'] {}
```

```css
[target="_blank"] {}
```

```css
[target= '_blank'] {}
```

```css
[target= "_blank"] {}
```

以下模式*不*被视为违规：

```css
[target] {}
```

```css
[target =_blank] {}
```

```css
[target ='_blank'] {}
```

```css
[target ="_blank"] {}
```

```css
[target = _blank] {}
```

```css
[target = '_blank'] {}
```

```css
[target = "_blank"] {}
```

### `"never"`

There *must never* be a single space before the operator.

以下模式被视为违规：

```css
[target =_blank] {}
```

```css
[target = _blank] {}
```

```css
[target ='_blank'] {}
```

```css
[target ="_blank"] {}
```

```css
[target = '_blank'] {}
```

```css
[target = "_blank"] {}
```

以下模式*不*被视为违规：

```css
[target] {}
```

```css
[target=_blank] {}
```

```css
[target='_blank'] {}
```

```css
[target="_blank"] {}
```

```css
[target= _blank] {}
```

```css
[target= '_blank'] {}
```

```css
[target= "_blank"] {}
```
