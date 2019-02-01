# selector-pseudo-element-blacklist

指定禁用的伪元素选择器的黑名单。

```css
 a::before {}
/** ↑
 * 这个伪元素选择器 */
```

此规则忽略：

-   CSS2 伪元素，即以单个冒号为前缀的元素
-   使用变量插值的选择器，例如 `::#{$variable} {}`

## 选项

`array|string|regex`: `["array", "of", "unprefixed", "pseudo-elements" or "regex"]|"pseudo-element"|/regex/`

给定：

```js
["before", "/^my-/i"]
```

以下模式被视为违规：

```css
a::before {}
```

```css
a::my-pseudo-element {}
```

```css
a::MY-OTHER-pseudo-element {}
```


以下模式*不*被视为违规：

```css
a::after {}
```

```css
a::not-my-pseudo-element {}
```
