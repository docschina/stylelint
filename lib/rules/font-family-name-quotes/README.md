# font-family-name-quotes

指定是否应在字体族名称周围使用引号。

```css
a { font-family: "Times New Roman", 'Ancient Runes', serif; }
/**              ↑               ↑  ↑             ↑
 *               这些引号            还有这些引号 */
```

此规则检查 `font` 和 `font-family` 属性。

此规则忽略 `$sass`、`@less` 和 `var(--custom-property)` 变量语法

## 选项

`string`: `"always-where-required"|"always-where-recommended"|"always-unless-keyword"`

*请阅读以下内容以了解这些选项*：

-   `font` 和 `font-family` 属性接受一个简短的特殊**关键字**列表：`inherit`、`serif`、`sans-serif`、`cursive`、`fantasy`、`system-ui` 和 `monospace`。如果您用引号将这些单词包裹起来，浏览器就不会将它们解释为关键字，而是会按照该名称查找字体（例如，将查找 `"sans-serif"` 字体）———— 这几乎*从来不是*您想要的。相反，您使用这些关键字指向内置的通用降级（对吗？）。因此，*以下所有选项都不会针对这些关键字强制执行*。（如果您真的想使用名为 `"sans-serif"` 的字体，请关闭此规则。）
-   [规范中](https://www.w3.org/TR/CSS2/fonts.html#font-family-prop)**推荐** “字体族名称包含空格、数字或连字符以外的标点符号”时使用引号。
-   如果字体族名称不是[有效的 CSS 标识符](https://www.w3.org/TR/CSS2/syndata.html#value-def-identifier)，则**需要**引号。例如，如果字体族名称包含 `$`、`！` 或 `/`，则它需要引号，但如果只是因为它包含空格或（非初始）数字或下划线则无需引号。*您使用的几乎所有字体族名称都**是**有效的 CSS 标识符*。
-   引号应该*永远不*在供应商前缀系统字体周围使用，例如 `-apple-system` 和 `BlinkMacSystemFont`。

有关这些细微之处的更多信息，请阅读 Mathias Bynens 的[“CSS 中的未加引号的字体族名称”](https://mathiasbynens.be/notes/unquoted-font-family)。

**警告：** 此规则目前不理解转义字符，例如 Mathias 描述的转义字符。如果您想使用字体族名称“Hawaii 5-0”，您需要用引号括起来，而不是把它作为 `Hawaii \35 -0` 或 `Hawaii\ 5-0` 转义形式。

### `"always-unless-keyword"`

期望非关键字的每个字体族名称都使用引号。

以下模式被视为违规：

```css
a { font-family: Arial, sans-serif; }
```

```css
a { font-family: Times New Roman, Times, serif; }
```

```css
a { font: 1em Arial, sans-serif; }
```

以下模式*不*被视为违规：

```css
a { font-family: 'Arial', sans-serif; }
```

```css
a { font-family: "Times New Roman", "Times", serif; }
```

```css
a { font: 1em 'Arial', sans-serif; }
```

### `"always-where-required"`

只有在根据上述标准*需要*时才会出现引号，并且在所有其他情况下都不允许引号。

以下模式被视为违规：

```css
a { font-family: "Arial", sans-serif; }
```

```css
a { font-family: 'Times New Roman', Times, serif; }
```

```css
a { font: 1em "Arial", sans-serif; }
```

以下模式*不*被视为违规：

```css
a { font-family: Arial, sans-serif; }
```

```css
a { font-family: Arial, sans-serif; }
```

```css
a { font-family: Times New Roman, Times, serif; }
```

```css
a { font-family: "Hawaii 5-0"; }
```

```css
a { font: 1em Arial, sans-serif; }
```

### `"always-where-recommended"`

只有在根据上述标准*推荐*时才会引用引号，并且在所有其他情况下都不允许引号。（这包括所有*需要*的情况。）

以下模式被视为违规：

```css
a { font-family: Times New Roman, Times, serif; }
```

```css
a { font-family: MyFontVersion6, sake_case_font; }
```

```css
a { font-family: 'Arial', sans-serif; }
```

```css
a { font: 1em Times New Roman, Times, serif; }
```

以下模式*不*被视为违规：

```css
a { font-family: 'Times New Roman', Times, serif; }
```

```css
a { font-family: "MyFontVersion6", "sake_case_font"; }
```

```css
a { font-family: Arial, sans-serif; }
```

```css
a { font: 1em 'Times New Roman', Times, serif; }
```
