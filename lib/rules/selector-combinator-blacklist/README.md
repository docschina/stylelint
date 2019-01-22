# selector-combinator-blacklist

Specify a blacklist of disallowed combinators.

```css
  a + b {}
/** ↑
 * These combinators */
```

This rule normalizes the whitespace descendant combinator to be a single space.

This rule ignores [reference combinators](https://www.w3.org/TR/selectors4/#idref-combinators) e.g. `/for/`.

## 选项

`array|string`: `["array", "of", "combinators"]|"combinator"`

Given:

```js
[">", " "]
```

以下模式被视为违规：

```css
a > b {}
```

```css
a b {}
```

```css
a
b {}
```

The following patterns are *not* considered violations:

```css
a + b {}
```

```css
a ~ b {}
```
