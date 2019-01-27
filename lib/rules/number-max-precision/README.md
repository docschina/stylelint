# number-max-precision

限制数字中允许的小数位数

```css
a { top: 3.245634px; }
/**           ↑
 * 这些小数位 */
```

## 选项

`int`：允许的最大小数位数。

例如，使用 `2`：

以下模式被视为违规：

```css
a { top: 3.245px; }
```

```css
a { top: 3.245634px; }
```

```css
@media (min-width: 3.234em) {}
```

以下模式*不*被视为违规：

```css
a { top: 3.24px; }
```

```css
@media (min-width: 3.23em) {}
```

## 可选的辅助选项

### `ignoreUnits: ["/regex/", /regex/, "string"]`

忽略具有指定单位的值的数字精度。

例如，使用 `2`。

给定：

```js
["/^my-/", "%"]
```

以下模式被视为违规：

```css
a { top: 3.245px; }
```

```css
a { top: 3.245634px; }
```

```css
@media (min-width: 3.234em) {}
```

以下模式*不*被视为违规：

```css
a { top: 3.245%; }
```

```css
@media (min-width: 3.23em) {}
```

```css
a {
  width: 10.5432%;
}
```

```css
a { top: 3.245my-unit; }
```

```css
a {
  width: 10.989my-other-unit;
}
```
