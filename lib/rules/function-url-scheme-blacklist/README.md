# function-url-scheme-blacklist

指定禁用的 URL 协议的黑名单。

```css
a { background-image: url('http://www.example.com/file.jpg'); }
/**                        ↑
 *           这个 URL 协议 */
```

[URL 协议]由字母、数字、`+`、`-` 和 `.` 字符组成。它可以出现在 URL 的开头，后跟`:`

此规则忽略：

-   无协议的 URL 参数
-   带变量或变量插值的 URL 参数（`$sass`、`@less`、`--custom-property`、`#{$var}`、`@{var}`、`$(var)`）

## 选项

`array|string|regex`: `["array", "of", /schemes/ or "/regex/"]|"scheme"|/regex/`

给定：

```js
["ftp", "/^http/"]
```

以下模式被视为违规：

```css
a { background-image: url('ftp://www.example.com/file.jpg'); }
```

```css
a { background-image: url('http://www.example.com/file.jpg'); }
```

```css
a { background-image: url('https://www.example.com/file.jpg'); }
```

以下模式*不*被视为违规：

```css
a { background-image: url('data:image/gif;base64,R0lGODlhAQABAIAAAAUEBAAAACwAAAAAAQABAAACAkQBADs='); }
```

```css
a { background-image: url('example.com/file.jpg'); }
```

```css
a { background-image: url('/example.com/file.jpg'); }
```

```css
a { background-image: url('//example.com/file.jpg'); }
```

```css
a { background-image: url('./path/to/file.jpg'); }
```
