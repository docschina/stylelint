# selector-pseudo-element-no-unknown

禁止未知的伪元素选择器。

```css
    a::before {}
/**    ↑
 * 这个伪元素选择器 */
```

此规则考虑了 CSS 规范中定义的伪元素选择器，包括已知的编辑草案。

此规则忽略带浏览器引擎前缀的伪元素选择器。

## 选项

### `true`

以下模式被视为违规：

```css
a::pseudo {}
```

```css
a::PSEUDO {}
```

```css
a::element {}
```

以下模式*不*被视为违规：

```css
a:before {}
```

```css
a::before {}
```

```css
::selection {}
```

```css
input::-moz-placeholder {}
```

## 可选的辅助选项

### `ignorePseudoElements: ["/regex/", "string"]`

给定：

```js
["/^my-/", "pseudo-element"]
```

以下模式*不*被视为违规：

```css
a::pseudo-element {}
```

```css
a::my-pseudo {}
```

```css
a::my-other-pseudo {}
```
