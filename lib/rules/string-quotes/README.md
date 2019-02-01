# string-quotes

指定字符串使用单引号或双引号。

```css
a[id="foo"] { content: "x"; }
/**  ↑   ↑             ↑ ↑
 * 这些引号和引号 */
```

注释中的引号将被忽略。


```css
/* "这么写没问题" */
/* '这么写也没问题' */
```

@charset 规则中的单引号将被忽略，因为根据 [CSS 规范](https://www.w3.org/TR/CSS2/syndata.html#x57)，在此上下文中使用单引号是不正确的。

```css
@charset "utf-8"
/* 无论配置如何都没问题 */
```

[命令行](../../../docs/user-guide/cli.md#自动修复错误)中的 `--fix` 选项可以自动修复此规则报告的大多数问题。

## 选项

`string`: `"single"|"double"`

### `"single"`

字符串*必须*用单引号包裹。

以下模式被视为违规：

```css
a { content: "x"; }
```

```css
a[id="foo"] {}
```

以下模式*不*被视为违规：

```css
a { content: 'x'; }
```

```css
a[id='foo'] {}
```

```css
a { content: "x'y'z"; }
```

### `"double"`

字符串*必须*用双引号包裹。

以下模式被视为违规：

```css
a { content: 'x'; }
```

```css
a[id='foo'] {}
```

以下模式*不*被视为违规：

```css
a { content: "x"; }
```

```css
a[id="foo"] {}
```

```css
a { content: 'x"y"z'; }
```

## 可选的辅助选项

### `avoidEscape`: `true|false`, defaults to `true`

允许字符串使用单引号或双引号，只要该字符串包含必须以其他方式转义的引号。

例如，使用 `"single", { "avoidEscape" : false }`。

以下模式被视为违规：

```css
a { content: "x'y'z"; }
```

```css
a[id="foo'bar'baz"] {}
```

以下模式*不*被视为违规：

```css
a { content: 'x'; }
```

```css
a[id='foo'] {}
```
