# function-url-no-scheme-relative

禁止相对协议 URL。

```css
a { background-image: url('//www.google.com/file.jpg'); }
/**                        ↑
 *  这个相对协议 URL */
```

[相对协议 URL](https://url.spec.whatwg.org/#syntax-url-scheme-relative)是一个以 `//` 开头，后跟主机的 URL。

这条规则忽略了作为变量的 URL 参数（`$sass`、`@less`、`--custom-property`）。

## 选项

### `true`

以下模式被视为违规：

```css
a {
  background: url("//www.google.com/file.jpg");
}
```

以下模式*不*被视为违规：

```css
a {
  background: url("../file.jpg");
}
```

```css
a {
  background: url("http://www.google.com/file.jpg");
}
```

```css
a {
  background: url("/path/to/file.jpg");
}
```
