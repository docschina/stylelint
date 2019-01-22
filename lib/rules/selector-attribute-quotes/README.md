# selector-attribute-quotes

Require or disallow quotes for attribute values.

```css
[target="_blank"] {}
/**     ↑      ↑
 * These quotes */
```

## 选项

`string`: `"always"|"never"`

### `"always"`

Attribute values *must always* be quoted.

以下模式被视为违规：

```css
[title=flower] {}
```

```css
[class^=top] {}
```

The following patterns are *not* considered violations:

```css
[title] {}
```

```css
[target="_blank"] {}
```

```css
[class|="top"] {}
```

```css
[title~='text'] {}
```

```css
[data-attribute='component'] {}
```

### `"never"`

Attribute values *must never* be quoted.

以下模式被视为违规：

```css
[target="_blank"] {}
```

```css
[class|="top"] {}
```

```css
[title~='text'] {}
```

```css
[data-attribute='component'] {}
```

The following patterns are *not* considered violations:

```css
[title] {}
```

```css
[title=flower] {}
```

```css
[class^=top] {}
```
