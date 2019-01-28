# at-rule-no-vendor-prefix

禁止@规则的浏览器引擎前缀。

```css
    @-webkit-keyframes { 0% { top: 0; } }
/**  ↑
 * 这个前缀 */
```

## 选项

### `true`

以下模式被视为违规：

```css
@-webkit-keyframes { 0% { top: 0; } }
```

```css
@-ms-viewport { orientation: landscape; }
```

以下模式*不*被视为违规：

```css
@keyframes { 0% { top: 0; } }
```

```css
@viewport { orientation: landscape; }
```
