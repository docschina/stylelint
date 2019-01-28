# color-no-invalid-hex

禁止无效的 16 进制颜色。

```css
a { color: #y3 }
/**        ↑
 * 这个 16 进制颜色 */
```

扩写的 16 进制颜色可以是 6 或 8（带透明通道）位 16 进制字符。它们的简写变体分别是 3 和 4 位字符。

## 选项

### `true`

以下模式被视为违规：

```css
a { color: #00; }
```

```css
a { color: #fff1az; }
```

```css
a { color: #12345aa; }
```

以下模式*不*被视为违规：

```css
a { color: #000; }
```

```css
a { color: #000f; }
```

```css
a { color: #fff1a0; }
```

```css
a { color: #123450aa; }
```
