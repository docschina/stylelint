# unit-no-unknown

禁止未知的单位。

```css
a { width: 100pixels; }
/**           ↑
 *  这个单位 */
```

此规则考虑了 CSS 规范中定义的单位，包括已知的编辑草案。

## 选项

### `true`

以下模式被视为违规：

```css
a {
  width: 10pixels;
}
```

```css
a {
  width: calc(10px + 10pixels);
}
```

以下模式*不*被视为违规：

```css
a {
  width: 10px;
}
```

```css
a {
  width: 10Px;
}
```

```css
a {
  width: 10pX;
}
```

```css
a {
  width: calc(10px + 10px);
}
```

## 可选的辅助选项

### `ignoreUnits: ["/regex/", /regex/, "string"]`

给定：

```js
["/^my-/", "custom"]
```

以下模式*不*被视为违规：

```css
width: 10custom;
a {
}
```

```css
a {
  width: 10my-unit;
}
```

```css
a {
  width: 10my-other-unit;
}
```

### `ignoreFunctions: ["/regex/", /regex/, "string"]`

给定：

```js
["image-set", "/^my-/", "/^YOUR-/i"]
```

以下模式*不*被视为违规：

```css
a {
  background-image: image-set(
    '/images/some-image-1x.jpg' 1x,
    '/images/some-image-2x.jpg' 2x,
    '/images/some-image-3x.jpg' 3x
  );
}
```

```css
a {
  background-image: my-image-set(
    '/images/some-image-1x.jpg' 1x,
    '/images/some-image-2x.jpg' 2x,
    '/images/some-image-3x.jpg' 3x
  );
}
```

```css
a {
  background-image: YoUr-image-set(
    '/images/some-image-1x.jpg' 1x,
    '/images/some-image-2x.jpg' 2x,
    '/images/some-image-3x.jpg' 3x
  );
}
```
