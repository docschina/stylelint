# media-feature-name-no-unknown

禁止未知的媒体功能名。

```css
@media (min-width: 700px) {}
/**     ↑
 * 这个媒体功能名 */
```

此规则考虑了 CSS 规范中定义的媒体功能名，包括已知的编辑草案。

此规则忽略：

-   上下文范围中的媒体功能名称
-   带浏览器引擎前缀的媒体功能名称

## 选项

### `true`

以下模式被视为违规：

```css
@media screen and (unknown) {}
```

```css
@media screen and (unknown: 10px) {}
```

以下模式*不*被视为违规：

```css
@media all and (monochrome) {}
```

```css
@media (min-width: 700px) {}
```

```css
@media (MIN-WIDTH: 700px) {}
```

```css
@media (min-width: 700px) and (orientation: landscape) {}
```

```css
@media (-webkit-min-device-pixel-ratio: 2) {}
```

## 可选的辅助选项

### `ignoreMediaFeatureNames: ["/regex/", /regex/, "string"]`

给定：

```js
["/^my-/", "custom"]
```

以下模式*不*被视为违规：

```css
@media screen and (my-media-feature-name) {}
```

```css
@media screen and (custom: 10px) {}
```

```css
@media (min-width: 700px) and (custom: 10px) {}
```
