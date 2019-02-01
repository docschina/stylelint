# media-feature-name-whitelist

指定允许的媒体功能名的白名单。

```css
@media (min-width: 700px) {}
/**     ↑
 * 这个媒体功能名 */
```

此规则忽略范围上下文中的媒体功能名称。

## 选项

`array|string|regex`: `["array", "of", "unprefixed", /media-features/ or "regex"]|"media-feature"|/regex/`

给定：

```js
["max-width", "/^my-/"]
```

以下模式被视为违规：

```css
@media (min-width: 50em) {}
```

```css
@media print and (min-resolution: 300dpi) {}
```

以下模式*不*被视为违规：

```css
@media (max-width: 50em) {}
```

```css
@media (my-width: 50em) {}
```
