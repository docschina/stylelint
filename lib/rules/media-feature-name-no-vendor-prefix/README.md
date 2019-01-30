# media-feature-name-no-vendor-prefix

禁止媒体功能名的浏览器引擎前缀。

```css
@media (-webkit-min-device-pixel-ratio: 1) {}
/**      ↑
 * 这个前缀 */
```

此规则目前只检查 *resolutions* 的前缀

## 选项

### `true`

以下模式被视为违规：

```css
@media (-webkit-min-device-pixel-ratio: 1) {}
```

```css
@media (min--mox-device-pixel-ratio: 1) {}
```

```css
@media (-o-max-device-pixel-ratio: 1/1) {}
```

以下模式*不*被视为违规：

```css
@media (min-resolution: 96dpi) {}
```

```css
@media (max-resolution: 900dpi) {}
```
