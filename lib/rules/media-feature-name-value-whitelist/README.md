# media-feature-name-value-whitelist

指定允许的媒体功能名和值对的白名单。

```css
@media screen and (min-width: 768px) {}
/**                ↑          ↑
 *    这些功能和值 */
```

此规则忽略范围和布尔上下文中的媒体功能。

## 选项

```js
{
  "unprefixed-media-feature-name": ["array", "of", "values"],
  "/unprefixed-media-feature-name/": ["/regex/", "non-regex", /real-regex/]
}
```

如果在对象中找到媒体功能名称，则仅允许其列入白名单的值。如果对象中未包含媒体功能名称，则什么都可以。

如果名称或值被 `/` 包围（例如 `"/width$/"`），则它被解释为正则表达式。例如 `/width$/` 将匹配 `max-width` 和 `min-width`。

给定：

```json
{
  "min-width": ["768px", "1024px"],
  "/resolution/": ["/dpcm$/"]
}
```

以下模式被视为违规：

```css
@media screen and (min-width: 1000px) {}
```

```css
@media screen and (min-resolution: 2dpi) {}
```

以下模式*不*被视为违规：

```css
@media screen and (min-width: 768px) {}
```

```css
@media screen and (min-width: 1024px) {}
```

```css
@media screen and (orientation: portrait) {}
```

```css
@media screen and (min-resolution: 2dpcm) {}
```

```css
@media screen and (resolution: 10dpcm) {}
```
