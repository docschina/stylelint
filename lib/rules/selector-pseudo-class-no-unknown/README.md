# selector-pseudo-class-no-unknown

禁止未知的伪类选择器。

```css
    a:hover {}
/**    ↑
 * 这个伪类选择器 */
```

此规则考虑了 CSS 规范中定义的伪类选择器，包括已知的编辑草案。

此规则忽略带浏览器引擎前缀的伪类选择器。

## 选项

### `true`

以下模式被视为违规：

```css
a:unknown {}
```

```css
a:UNKNOWN {}
```

```css
a:hoverr {}
```

以下模式*不*被视为违规：

```css
a:hover {}
```

```css
a:focus {}
```

```css
:not(p) {}
```

```css
input:-moz-placeholder {}
```

## 可选的辅助选项

### `ignorePseudoClasses: ["/regex/", "string"]`

给定：

```js
["/^my-/", "pseudo-class"]
```

以下模式*不*被视为违规：

```css
a:pseudo-class {}
```

```css
a:my-pseudo {}
```

```css
a:my-other-pseudo {}
```
