# selector-attribute-operator-whitelist

指定允许的属性运算符的白名单。

```css
[target="_blank"] {}
/**    ↑
 * 这个运算符 */
```

## 选项

`array|string`: `["array", "of", "operators"]|"operator"`

给定：

```js
[ "=", "|=" ]
```

以下模式被视为违规：

```css
[class*="test"] {}
```

```css
[title~="flower"] {}
```

```css
[class^="top"] {}
```

以下模式*不*被视为违规：

```css
[target] {}
```

```css
[target="_blank"] {}
```

```css
[class|="top"] {}
```
