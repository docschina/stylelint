# unit-case

Specify lowercase or uppercase for units.

```css
    a { width: 10px; }
/**              ↑
 *     These units */
```

The `--fix` option on the [command line](../../../docs/user-guide/cli.md#autofixing-errors) can automatically fix most of the problems reported by this rule.

## 选项

`string`: `"lower"|"upper"`

### `"lower"`

以下模式被视为违规：

```css
a {
  width: 10PX;
}
```

```css
a {
  width: 10Px;
}
```

```css
a {
  width: 10pX;
}
```

```css
a {
  width: 10PIXEL;
}
```

```css
a {
  width: calc(10PX * 2);
}
```

以下模式*不*被视为违规：

```css
a {
  width: 10px;
}
```

```css
a {
  width: calc(10px * 2);
}
```

### `"upper"`

以下模式被视为违规：

```css
a {
  width: 10px;
}
```

```css
a {
  width: 10Px;
}
```

```css
a {
  width: 10pX;
}
```

```css
a {
  width: 10pixel;
}
```

```css
a {
  width: calc(10px * 2);
}
```

以下模式*不*被视为违规：

```css
a {
  width: 10PX;
}
```

```css
a {
  width: calc(10PX * 2);
}
```
