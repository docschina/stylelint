# selector-attribute-operator-blacklist

指定禁用的属性运算符的黑名单。

```css
[target="_blank"] {}
/**    ↑
 * 这个运算符 */
```

## 选项

`array|string`: `["array", "of", "operators"]|"operator"`

给定：

```js
[ "*=" ]
```

以下模式被视为违规：

```css
[class*="test"] {}
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
