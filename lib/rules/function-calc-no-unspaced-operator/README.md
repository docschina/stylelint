# function-calc-no-unspaced-operator

在函数`calc`接收的表达式中，运算符和参数之间必须存在间距。

```css
a { top: calc(1px + 2px); }
/**               ↑
 * 注意上述运算符和参数之间的间距 */
```

在操作符前，必须有一个空格或换行符加缩进。
在运算符之后，必须有一个空格或换行符。

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
