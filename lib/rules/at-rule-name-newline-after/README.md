# at-rule-name-newline-after

Require a newline after at-rule names.

```css
    @media
   /*↑*/  (max-width: 600px) {}
/**  ↑
 * 这个 @规则名之后的换行符 */
```

## 选项

`string`: `"always"|"always-multi-line"`

### `"always"`

在 @规则名之后*必须*有一个换行符。

以下模式被视为违规：

```css
@charset "UTF-8";
```

```css
@media (min-width: 700px) and
  (orientation: landscape) {}
```

以下模式*不*被视为违规：

```css
@charset
  "UTF-8";
```

```css
@import
  "x.css" screen and
 (orientation:landscape);
```

```css
@media
  (min-width: 700px) and (orientation: landscape) {}
```

```css
@media
  (min-width: 700px) and
  (orientation: landscape) {}
```

### `"always-multi-line"`

具有多行参数时，@规则名之后*必须*有一个换行符。

以下模式被视为违规：

```css
@import "x.css" screen and
 (orientation:landscape);
```

```css
@media (min-width: 700px) and
 (orientation: landscape) {}
```

以下模式*不*被视为违规：

```css
@charset "UTF-8";
```

```css
@charset
  "UTF-8";
```

```css
@import "x.css" screen and (orientation:landscape);
```

```css
@media (min-width: 700px) and (orientation: landscape) {}
```

```css
@media
  (min-width: 700px) and
  (orientation: landscape) {}
```
