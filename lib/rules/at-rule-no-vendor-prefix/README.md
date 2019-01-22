# at-rule-no-vendor-prefix

Disallow vendor prefixes for at-rules.

```css
    @-webkit-keyframes { 0% { top: 0; } }
/**  ↑
 * These prefixes */
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

The following patterns are *not* considered violations:

```css
@keyframes { 0% { top: 0; } }
```

```css
@viewport { orientation: landscape; }
```
