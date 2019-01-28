# at-rule-no-unknown

禁止未知的@规则。

```css
    @unknown (max-width: 960px) {}
/** ↑
 * 像这样的@规则 */
```

此规则考虑了 CSS 规范中定义的@规则，包括已知的编辑草案。

## 选项

### `true`

以下模式被视为违规：

```css
@unknown {}
```

以下模式*不*被视为违规：

```css
@charset "UTF-8";
```

```css
@CHARSET "UTF-8";
```

```css
@media (max-width: 960px) {}
```

```css
@font-feature-values Font One {
  @styleset {}
}
```

## 可选的辅助选项

### `ignoreAtRules: ["/regex/", /regex/, "string"]`

给定：

```js
["/^my-/", "custom"]
```

以下模式*不*被视为违规：

```css
@my-at-rule "x.css";
```

```css
@my-other-at-rule {}
```

```css
@custom {}
```
