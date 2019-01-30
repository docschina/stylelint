# property-no-unknown

禁止未知的属性。

```css
a { heigth: 100%; }
/** ↑
 * 这个属性 */
```

此规则考虑了[CSS 规范和浏览器](https://github.com/betit/known-css-properties#source)中定义的属性。

此规则忽略：

-   变量（`$sass`、`@less`、`--custom-property`）
-   带浏览器引擎前缀的属性（例如，`-moz-align-self`、`-webkit-align-self`）

使用下面描述的选项 `checkPrefixed` 打开带浏览器引擎前缀属性的检查。

## 选项

### `true`

以下模式被视为违规：

```css
a {
  colr: blue;
}
```

```css
a {
  my-property: 1;
}
```

以下模式*不*被视为违规：

```css
a {
  color: green;
}
```

```css
a {
  fill: black;
}
```

```css
a {
  -moz-align-self: center;
}
```

```css
a {
  -webkit-align-self: center;
}
```

```css
a {
  align-self: center;
}
```

## 可选的辅助选项

### `ignoreProperties: ["/regex/", /regex/, "string"]`

给定：

```js
["/^my-/", "custom"]
```

以下模式*不*被视为违规：

```css
a {
  my-property: 10px;
}
```

```css
a {
  my-other-property: 10px;
}
```

```css
a {
  custom: 10px;
}
```

### `checkPrefixed: true | false` (default: `false`)

如果为 `true`，则此规则将检查带浏览器引擎前缀的属性。

例如，使用 `true`：

以下模式*不*被视为违规：

```css
a {
  -webkit-overflow-scrolling: auto;
}
```

```css
a {
  -moz-box-flex: 0;
}
```

以下模式被视为违规：

```css
a {
  -moz-align-self: center;
}
```

```css
a {
  -moz-overflow-scrolling: center;
}
```
