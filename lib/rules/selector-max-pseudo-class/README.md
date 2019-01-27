# selector-max-pseudo-class

限制一个选择器中伪类的数量

```css
.foo .bar:first-child:hover {}
/*       ↑           ↑
         ↑           ↑
         1           2 -- this selector contains two pseudo-classes */
```

此规则在计算一个选择器的伪类的数量之前先解析选择器嵌套。[选择器列表](https://www.w3.org/TR/selectors4/#selector-list)中的每个选择器都将单独计算。

`:not()` 伪类的内容也是单独计算的。此规则将其参数视为一个独立的选择器，结果不计入整个选择器的总数。

## 选项

`int`：允许的最大伪类数量。

例如，使用 `1`：

以下模式被视为违规：

```css
a:first-child:focus {}
```

```css
.foo .bar:first-child:hover {}
```

以下模式*不*被视为违规：

```css
a {}
```

```css
a:first-child {}
```

```css
.foo .bar:first-child {}
```

