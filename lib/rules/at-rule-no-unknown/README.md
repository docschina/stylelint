# at-rule-no-unknown

Disallow unknown at-rules.

```css
    @unknown (max-width: 960px) {}
/** ↑
 * At-rules like this */
```

This rule considers at-rules defined in the CSS Specifications, up to and including Editor's Drafts, to be known.

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

## Optional secondary options

### `ignoreAtRules: ["/regex/", /regex/, "string"]`

Given:

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
