# block-no-empty

禁止空块。

```css
 a { }
/** ↑
 * 像这样的块 */
```

## 选项

### `true`

以下模式被视为违规：

```css
a {}
```

```css
a { }
```

```css
@media print { a {} }
```

以下模式*不*被视为违规：

```css
a { color: pink; }
```

```css
@media print { a { color: pink; } }
```
