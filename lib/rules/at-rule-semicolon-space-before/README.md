# at-rule-semicolon-space-before

要求在 @规则的分号之前必须有一个空格或不能有空白符。

```css
@import "components/buttons";
/**                         ↑
 *                这个分号之前的空白符 */
```

## 选项

`string`: `"always"|"never"`

### `"always"`

在分号之前*必须*有一个空格。

以下模式被视为违规：

```css
@import "components/buttons";
```

以下模式*不*被视为违规：

```css
@import "components/buttons" ;
```

### `"never"`

在分号之前*不能*有空格。

以下模式被视为违规：

```css
@import "components/buttons" ;
```

以下模式*不*被视为违规：

```css
@import "components/buttons";
```
