# color-no-hex

禁止 16 进制颜色。

```css
a { color: #333 }
/**        ↑
 * 这个 16 进制颜色 */
```

## 选项

### `true`

以下模式被视为违规：

```css
a { color: #000; }
```

```css
a { color: #fff1aa; }
```

```css
a { color: #123456aa; }
```

无效的 16 进制值也会导致违规：

```css
a { color: #foobar; }
```

```css
a { color: #0000000000000000; }
```

以下模式*不*被视为违规：

```css
a { color: black; }
```

```css
a { color: rgb(0, 0, 0); }
```

```css
a { color: rgba(0, 0, 0, 1); }
```
