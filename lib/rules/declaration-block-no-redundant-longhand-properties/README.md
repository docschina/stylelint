# declaration-block-no-redundant-longhand-properties

禁止可合并为一个简写属性的扩写属性。

```css
  a {
    padding-top: 1px;
    padding-right: 2px;
    padding-bottom: 3px;
    padding-left: 4px; }
/** ↑
 *  这些简写属性 */
```

上面示例中的扩写属性可以更简洁地写为：

```css
a {
  padding: 1px 2px 3px 4px;
}
```

只有您的扩写属性等效于设置了*所有*简写属性时，此规则才会指正。

当可以使用以下简写属性时，此规则才会指正：

-   `margin`
-   `padding`
-   `background`
-   `font`
-   `border`
-   `border-top`
-   `border-bottom`
-   `border-left`
-   `border-right`
-   `border-width`
-   `border-style`
-   `border-color`
-   `list-style`
-   `border-radius`
-   `transition`
-   `animation`
-   `border-block-end`
-   `border-block-start`
-   `border-image`
-   `border-inline-end`
-   `border-inline-start`
-   `column-rule`
-   `columns`
-   `flex`
-   `flex-flow`
-   `grid`
-   `grid-area`
-   `grid-column`
-   `grid-gap`
-   `grid-row`
-   `grid-template`
-   `outline`
-   `text-decoration`
-   `text-emphasis`
-   `mask`

**请注意** 如果属性可以根据规范进行简写，**无论任何单个浏览器的行为如何**，它都被认为是多余的。例如，由于 Internet Explorer 的 Flexbox 实现，[可能无法使用简写属性 `flex`](https://github.com/philipwalton/flexbugs#flexbug-8)，但是，扩写形式仍然被视为违规。

Flexbox 相关的属性可以使用 `ignoreShorthands: ["/flex-/"]` 忽略（见下文）。

## 选项

### `true`

以下模式被视为违规：

```css
a {
  margin-top: 1px;
  margin-right: 2px;
  margin-bottom: 3px;
  margin-left: 4px;
}
```

```css
a {
  font-style: italic;
  font-variant: normal;
  font-weight: bold;
  font-stretch: normal;
  font-size: 14px;
  line-height: 1.2;
  font-family: serif;
}
```

```css
a {
  -webkit-transition-property: top;
  -webkit-transition-duration: 2s;
  -webkit-transition-timing-function: ease;
  -webkit-transition-delay: 0.5s;
}
```

以下模式*不*被视为违规：

```css
a {
  margin: 1px 2px 3px 4px;
}
```

```css
a {
  font: italic normal bold normal 14px/1.2 serif;
}
```

```css
a {
  -webkit-transition: top 2s ease 0.5s;
}
```

```css
a {
  margin-top: 1px;
  margin-right: 2px;
}
```

```css
a {
  margin-top: 1px;
  margin-right: 2px;
  margin-bottom: 3px;
}
```

## 可选的辅助选项

### `ignoreShorthands: ["/regex/", /regex/, "string"]`

给定：

```js
["padding", "/border/"]
```

以下模式*不*被视为违规：

```css
a {
  padding-top: 20px;
  padding-right: 10px;
  padding-bottom: 30px;
  padding-left: 10px;
}
```

```css
a {
  border-top-width: 1px;
  border-bottom-width: 1px;
  border-left-width: 1px;
  border-right-width: 1px;
}
```

```css
a {
  border-top-width: 1px;
  border-bottom-width: 1px;
  border-left-width: 1px;
  border-right-width: 1px;
}
```

```css
a {
  border-top-color: green;
  border-top-style: double;
  border-top-width: 7px;
}
```
