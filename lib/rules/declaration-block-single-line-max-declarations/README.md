# declaration-block-single-line-max-declarations

限制一个单行声明块中声明的数量

```css
a { color: pink; top: 0; }
/** ↑            ↑
 * 这些声明的数量 */
```

## 选项

`int`：允许的最大声明数量。

例如，使用 `1`：

以下模式被视为违规：

```css
a { color: pink; top: 3px; }
```

```css
a,
b { color: pink; top: 3px; }
```

以下模式*不*被视为违规：

```css
a { color: pink; }
```

```css
a,
b { color: pink; }
```

```css
a {
  color: pink;
  top: 3px;
}
```
