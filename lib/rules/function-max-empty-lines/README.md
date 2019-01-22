# function-max-empty-lines

Limit the number of adjacent empty lines within functions.

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
 *            These lines */
```

The `--fix` option on the [command line](../../../docs/user-guide/cli.md#autofixing-errors) can automatically fix all of the problems reported by this rule.

## 选项

`int`: Maximum number of characters allowed.

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
