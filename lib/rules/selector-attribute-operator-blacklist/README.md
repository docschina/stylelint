# selector-attribute-operator-blacklist

Specify a blacklist of disallowed attribute operators.

```css
[target="_blank"] {}
/**    ↑
 * These operators */
```

## 选项

`array|string`: `["array", "of", "operators"]|"operator"`

Given:

```js
[ "*=" ]
```

以下模式被视为违规：

```css
[class*="test"] {}
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
