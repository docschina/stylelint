# function-name-case

Specify lowercase or uppercase for function names.

```css
a { width: calc(5% - 10em); }
/**        ↑
 * These functions */
```

Camel case function names, e.g. `translateX`, are accounted for when the `lower` option is used.

The `--fix` option on the [command line](../../../docs/user-guide/cli.md#autofixing-errors) can automatically fix all of the problems reported by this rule.

## 选项

`string`: `"lower"|"upper"`

### `"lower"`

以下模式被视为违规：

```css
a {
  width: Calc(5% - 10em);
}
```

```css
a {
  width: cAlC(5% - 10em);
}
```

```css
a {
  width: CALC(5% - 10em);
}
```

```css
a {
  background: -WEBKIT-RADIAL-GRADIENT(red, green, blue);
}
```

The following patterns are *not* considered violations:

```css
a {
  width: calc(5% - 10em);
}
```

```css
a {
  background: -webkit-radial-gradient(red, green, blue);
}
```

### `"upper"`

以下模式被视为违规：

```css
a {
  width: Calc(5% - 10em);
}
```

```css
a {
  width: cAlC(5% - 10em);
}
```

```css
a {
  width: calc(5% - 10em);
}
```

```css
a {
  background: -webkit-radial-gradient(red, green, blue);
}
```

The following patterns are *not* considered violations:

```css
a {
  width: CALC(5% - 10em);
}
```

```css
a {
  background: -WEBKIT-RADIAL-GRADIENT(red, green, blue);
}
```

## Optional secondary options

### `ignoreFunctions: ["/regex-as-string/", /regex/, "non-regex"]`

Ignore case of function names.

For example, with `"lower"`.

Given:

```js
["some-function", "/^get.*$/"]
```

以下模式被视为违规：

```css
a {
  color: sOmE-FuNcTiOn();
}
```

```css
a {
  color: some-other-function();
}
```

```css
a {
  color: GetColor();
}
```

```css
a {
  color: GET_COLOR();
}
```

The following patterns are *not* considered violations:

```css
a {
  display: some-function();
}
```


```css
a {
  display: getColor();
}
```

```css
a {
  display: get_color();
}
```
