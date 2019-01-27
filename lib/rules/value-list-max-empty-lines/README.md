# value-list-max-empty-lines

限制值列表中相邻空行的数量

```css
a {
  box-shadow:
    inset 0 2px 0 #dcffa6,
                    /* ← */
    0 2px 5px #000; /* ↑ */
}                   /* ↑ */
/**                    ↑
 *                 这个空行 */
```

[命令行](../../../docs/user-guide/cli.md#自动修复错误)中的 `--fix` 选项可以自动修复此规则报告的所有问题。

## 选项

`int`：允许的最大相邻空行数量。

例如，使用 `0`：

以下模式被视为违规：

```css
a {
  padding: 10px

    10px
    10px
    10px
}
```

```css
a {
  padding:
    10px
    10px
    10px

    10px
}
```

```css
a {
  box-shadow: inset 0 2px 0 #dcffa6,

    0 2px 5px #000;
}
```

```css
a {
  box-shadow:
    inset 0 2px 0 #dcffa6,

    0 2px 5px #000;
}
```

以下模式*不*被视为违规：

```css
a {
  padding: 10px 10px 10px 10px
}
```

```css
a {
  padding: 10px
    10px
    10px
    10px
}
```

```css
a {
  padding:
    10px
    10px
    10px
    10px
}
```

```css
a {
  box-shadow: inset 0 2px 0 #dcffa6, 0 2px 5px #000;
}
```

```css
a {
  box-shadow: inset 0 2px 0 #dcffa6,
    0 2px 5px #000;
}
```

```css
a {
  box-shadow:
    inset 0 2px 0 #dcffa6,
    0 2px 5px #000;
}
```
