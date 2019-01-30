# property-no-vendor-prefix

禁止属性的浏览器引擎前缀。

```css
a { -webkit-transform: scale(1); }
/**  ↑
 * 这个前缀 */
```

此规则并不排斥所有前缀。它使用 [Autoprefixer](https://github.com/postcss/autoprefixer) 的最新数据（来自 [caniuse.com](http://caniuse.com/)）来判断前缀是否违规。*如果您使用了带前缀的属性，而它有一个可被 Autoprefixer 处理的标准的替代品，则此规则会对其作出指正*。但如果您使用一个将被 Autoprefixer 忽略且无法提供的非标准前缀属性（例如 `-webkit-touch-callout`），则此规则将忽略它。

## 选项

### `true`

以下模式被视为违规：

```css
a { -webkit-transform: scale(1); }
```

```css
a { -moz-columns: 2; }
```

以下模式*不*被视为违规：

```css
a { transform: scale(1); }
```

```css
a {
columns: 2; }
```

```css
a { -webkit-touch-callout: none; }
```

## 可选的辅助选项

### `ignoreProperties: ["/regex/", /regex/, "string"]`

给定：

```js
["transform", "columns"]
```

以下模式*不*被视为违规：

```css
a { -webkit-transform: scale(1); }
```

```css
a { -moz-columns: 2; }
```
