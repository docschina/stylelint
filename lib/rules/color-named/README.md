# color-named

要求（如果可能）或禁止命名颜色。

```css
a { color: black }
/**        ↑
 * 这个命名颜色 */
```

## 选项

`string`: `"always-where-possible"|"never"`

### `"always-where-possible"`

在可能的情况下,*必须*使用命名颜色。

如果是 16 进制（3、4、6 和 8 位）、`rgb()`、`rgba()`、`hsl()`、`hsla()`、`hwb()` 或 `gray()` 颜色可以表示为命名颜色，此规则将对此指正。

以下模式被视为违规：

```css
a { color: #000; }
```

```css
a { color: #f000; }
```

```css
a { color: #ff000000; }
```

```css
a { color: rgb(0, 0, 0); }
```

```css
a { color: rgb(0%, 0%, 0%); }
```

```css
a { color: rgba(0, 0, 0, 0); }
```

```css
a { color: hsl(0, 0%, 0%); }
```

```css
a { color: hwb(0, 0%, 100%); }
```

```css
a { color: gray(0); }
```

以下模式*不*被视为违规：

```css
a { color: black; }
```

```css
a { color: rgb(10, 0, 0); }
```

```css
a { color: rgb(0, 0, 0, 0.5); }
```

### `"never"`

*不能*使用命名颜色。

以下模式被视为违规：

```css
a { color: black; }
```

```css
a { color: white; }
```

以下模式*不*被视为违规：

```css
a { color: #000; }
```

```css
a { color: rgb(0, 0, 0); }
```

```css
a { color: var(--white); }
```

```scss
a { color: $blue; }
```

```less
a { color: @blue; }
```

## 可选的辅助选项

### `ignore: ["inside-function"]`

忽略函数内的颜色。

例如，使用 `"never"`。

以下模式*不*被视为违规：

```css
a {
  color: map-get($colour, blue);
}
```

```css
a {
  background-image: url(red);
}
```

### `ignoreProperties: ["/regex/", /regex/, "string"]`

例如，使用 `"never"`。

给定：

```js
["/^my-/", "composes"]
```

以下模式*不*被视为违规：

```css
a {
  my-property: red;
}
```

```css
a {
  my-other-property: red;
}
```

```css
a {
  composes: red from './index.css';
}
```
