# selector-no-vendor-prefix

禁止选择器的浏览器引擎前缀。

```css
input::-moz-placeholder {}
/**     ↑
 * 这个前缀 */
```

此规则并不排斥所有前缀。它使用 [Autoprefixer](https://github.com/postcss/autoprefixer) 的最新数据（来自 [caniuse.com](http://caniuse.com/)）来判断前缀是否违规。*如果您使用了带前缀的选择器，而它有一个可被 Autoprefixer 处理的标准的替代品，则此规则会对其作出指正*。但如果您使用一个将被 Autoprefixer 忽略且无法提供的非标准前缀选择器，则此规则将忽略它。

## 选项

### `true`

以下模式被视为违规：

```css
input::-moz-placeholder {}
```

```css
:-webkit-full-screen a {}
```

以下模式*不*被视为违规：

```css
input::placeholder {}
```

```css
:full-screen a {}
```

## 可选的辅助选项

### `ignoreSelectors: ["/regex/", "non-regex"]`

忽略选择器的浏览器引擎前缀。

给定：

```js
["::-webkit-input-placeholder", "/-moz-.*/"]
```

以下模式*不*被视为违规：

```css
input::-webkit-input-placeholder {
  color: pink;
}

input::-moz-placeholder {
  color: pink;
}
```
