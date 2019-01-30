# value-no-vendor-prefix

禁止值的浏览器引擎前缀。

```css
a { display: -webkit-flex; }
/**          ↑
 *  这个前缀 */
```

此规则仅针对*标准*值的前缀进行指正，而不针对*专有*或*未知*值。

## 选项

### `true`

以下模式被视为违规：

```css
a { display: -webkit-flex; }
```

```css
a { max-width: -moz-max-content; }
```

```css
a { background: -webkit-linear-gradient(bottom, #000, #fff); }
```

以下模式*不*被视为违规：

```css
a { display: flex; }
```

```css
a { max-width: max-content; }
```

```css
a { background: linear-gradient(bottom, #000, #fff); }
```

## 可选的辅助选项

### `ignoreValues: ["string"]`

给定：

```js
["grab", "max-content"]
```

以下模式*不*被视为违规：

```css
cursor: -webkit-grab;
```

```css
.foo { max-width: -moz-max-content; }
```
