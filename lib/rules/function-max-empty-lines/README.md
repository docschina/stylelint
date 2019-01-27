# function-max-empty-lines

限制函数中相邻空行的数量

```css
a {
  transform:
    translate(
                /* ← */
      1,        /* ↑ */
                /* ← */
      1         /* ↑ */
                /* ← */
    );          /* ↑ */
}               /* ↑ */
/**                ↑
 *              这些行 */
```

[命令行](../../../docs/user-guide/cli.md#自动修复错误)中的 `--fix` 选项可以自动修复此规则报告的所有问题。

## 选项

`int`：允许的最大相邻空行数量。

例如，使用 `0`：

以下模式被视为违规：

```css
a {
  transform:
    translate(

      1,
      1
    );
}
```

```css
a {
  transform:
    translate(
      1,

      1
    );
}
```

```css
a {
  transform:
    translate(
      1,
      1

    );
}
```

以下模式*不*被视为违规：

```css
a {
  transform:
    translate(
      1,
      1
    );
}
```
