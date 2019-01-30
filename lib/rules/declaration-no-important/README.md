# declaration-no-important

禁止声明的 `!important`。

```css
a { color: pink !important; }
/**             ↑
 * 这个 !important */
```

如果您期望总是使用 `!important`，例如您正在编写[用户样式](https://userstyles.org/)，您可以使用[`postcss-safe-important`](https://github.com/crimx/postcss-safe-important)*安全的*添加。

## 选项

### `true`

以下模式被视为违规：

```css
a { color: pink !important; }
```

```css
a { color: pink ! important; }
```

```css
a { color: pink!important; }
```

以下模式*不*被视为违规：

```css
a { color: pink; }
```
