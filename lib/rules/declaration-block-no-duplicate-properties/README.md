# declaration-block-no-duplicate-properties

禁止声明块的重复属性。

```css
a { color: pink; color: orange; }
/** ↑            ↑
 * 这些重复属性 */
```

此规则忽略变量（`$sass`、`@less`、`--custom-property`）。

## 选项

### `true`

以下模式被视为违规：

```css
a { color: pink; color: orange; }
```

```css
a { color: pink; background: orange; color: orange }
```

以下模式*不*被视为违规：

```css
a { color: pink; }
```

```css
a { color: pink; background: orange; }
```

## 可选的辅助选项

### `ignore: ["consecutive-duplicates"]`

忽略连续的重复属性。

它们可以证明是旧浏览器的有用后备。

以下模式被视为违规：

```css
p {
  font-size: 16px;
  font-weight: 400;
  font-size: 1rem;
}
```

以下模式*不*被视为违规：

```css
p {
  font-size: 16px;
  font-size: 1rem;
  font-weight: 400;
}
```

### `ignore: ["consecutive-duplicates-with-different-values"]`

忽略具有不同值的连续重复属性。

包含重复属性（回退）对于处理旧版浏览器对 CSS 属性的支持非常有用。例如。当 `rem` 不可用时使用 `px` 单位。

以下模式被视为违规：

```css
/* 具有相同值的属性 */
p {
  font-size: 16px;
  font-size: 16px;
  font-weight: 400;
}
```

```css
/* 非连续重复 */
p {
  font-size: 16px;
  font-weight: 400;
  font-size: 1rem;
}
```

以下模式*不*被视为违规：

```css
p {
  font-size: 16px;
  font-size: 1rem;
  font-weight: 400;
}
```

### `ignoreProperties: ["/regex/", "non-regex"]`

忽略特定属性的重复项。

给定：

```js
["color", "/background\-/"]
```

以下模式被视为违规：

```css
a { color: pink; background: orange; background: white; }
```

```css
a { background: orange; color: pink; background: white; }
```

以下模式*不*被视为违规：

```css
a { color: pink; color: orange; background-color: orange; background-color: white; }
```

```css
a { color: pink; background-color: orange; color: orange; background-color: white; }
```
