# selector-attribute-operator-whitelist

Specify a whitelist of allowed attribute operators.

```css
[target="_blank"] {}
/**    ↑
 * These operators */
```

## 选项

`array|string`: `["array", "of", "operators"]|"operator"`

Given:

```js
[ "=", "|=" ]
```

The following patterns are considered violations:

```css
[class*="test"] {}
```

```css
[title~="flower"] {}
```

```css
[class^="top"] {}
```

The following patterns are *not* considered violations:

```css
[target] {}
```

```css
[target="_blank"] {}
```

```css
[class|="top"] {}
```
