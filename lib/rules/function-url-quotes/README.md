# function-url-quotes

要求或禁止 URL 的引号。

```css
a { background: url("x.jpg") }
/**                 ↑     ↑
 *             这些引号 */
```

## 选项

`string`: `"always"|"never"`

### `"always"`

URL *必须*用引号。

以下模式被视为违规：

```css
@import url(foo.css);
```

```css
@document domain(http://www.w3.org/);
```

```css
@font-face { font-family: 'foo'; src: url(foo.ttf); }
```

```css
@-moz-document url-prefix() {}
```

以下模式*不*被视为违规：

```css
a { background: url('x.jpg'); }
```

```css
@import url("foo.css");
```

```css
@document domain('http://www.w3.org/');
```

```css
@font-face { font-family: "foo"; src: url("foo.ttf"); }
```

```css
@-moz-document url-prefix('') {}
```

### `"never"`

URL *不能*用引号。

以下模式被视为违规：

```css
a { background: url('x.jpg'); }
```

```css
@import url("foo.css");
```

```css
@font-face { font-family: "foo"; src: url('foo.ttf'); }
```

以下模式*不*被视为违规：

```css
a { background: url(x.jpg); }
```

```css
@import url(foo.css);
```

```css
@font-face { font-family: 'foo'; src: url(foo.ttf); }
```

## 可选的辅助选项

### `except: ["empty"]`

如果函数没有参数，则反转主选项。

例如，使用 `"always"`。

以下模式*不*被视为违规：

```css
@-moz-document url-prefix() {}
```
