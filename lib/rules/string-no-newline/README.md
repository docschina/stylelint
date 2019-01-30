# string-no-newline

禁止字符串中的(未转义)换行符。

```css
a {
  content: "first
    second";     ↑
}                ↑
/**              ↑
 * 这里的换行符 */
```

[规范](https://www.w3.org/TR/CSS2/syndata.html#strings)说：“字符串不能直接包含换行符。要在字符串中包含换行符，请使用表示 ISO-10646（U+000A）中换行符的转义符，例如 ‘\A’ 或 ‘\00000a’。” 还说：“出于美观或其他原因，可以将字符串断为几行，但在这种情况下，换行本身必须使用反斜杠（\\）进行转义。”

## 选项

### `true`

以下模式被视为违规：

```css
a {
  content: "first
    second";
}
```

```css
[title="something
is probably wrong"] {}
```

```css
a {
  font-family: "Times
    New
    Roman";
}
```

以下模式*不*被视为违规：

```css
a {
  content: "first\Asecond";
}
```

```css
a {
  content: "first\\nsecond";
}
```

```css
[title="nothing\
  is wrong"] {}
```

```css
a {
  font-family: "Times New Roman";
}
```
