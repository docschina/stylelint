# comment-word-blacklist

在注释中指定不允许的单词的黑名单。

```css
 /* words within comments */
/** ↑     ↑      ↑
 *    这三个单词 */
```

**警告：** *选择器和值列表*中的注释目前被忽略。

## 选项

`array|string|regexp`: `["array", "of", "words", /or/, "/regex/"]|"word"|"/regex/"`

如果字符串用 `"/"` 包围（例如 `"/^TODO:/"`），则将其解释为正则表达式。

给定：

```js
["/^TODO:/", "badword"]
```

以下模式被视为违规：

```css
/* TODO: */
```

```css
/* TODO: add fallback */
```

```css
/* some badword */
```

以下模式*不*被视为违规：

```css
/* comment */
```
