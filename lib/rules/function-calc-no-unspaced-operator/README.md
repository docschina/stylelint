# function-calc-no-unspaced-operator

禁止在 `calc` 函数中使用没有间隔的运算符。

```css
a { top: calc(1px + 2px); }
/**               ↑
 *       运算符周围的空白符 */
```

在运算符前，必须有一个空格或换行符加缩进。在运算符之后，必须有一个空格或换行符。

## 选项

### `true`

以下模式被视为违规：

```css
a { top: calc(1px+2px); }
```

```css
a { top: calc(1px+ 2px); }
```

以下模式*不*被视为违规：

```css
a { top: calc(1px + 2px); }
```

```css
a { top: calc(calc(1em * 2) / 3); }
```

```css
a {
  top: calc(var(--foo) +
    var(--bar));
}
```

```css
a {
  top: calc(var(--foo)
    + var(--bar));
}
```
