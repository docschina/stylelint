# function-calc-no-invalid

禁止在 `calc` 函数中使用无效表达式。

```css
.foo {width: calc();}
/**               ↑
 * 空表达式 */
.foo {width: calc(100% 80px);}
/**                   ↑
/* 缺少运算符 */
.foo {width: calc(100% -80px);}
/**                   ↑
/* 缺少运算符 */
.foo {width: calc(100% - - 80px);}
/**                      ↑
/* 非预期的运算符 */
.foo {width: calc(100% -);}
/**                    ↑
/* 非预期的运算符 */
.foo {width: calc(- 100%);}
/**               ↑
/* 非预期的运算符 */
.foo {width: calc(100% / 0);}
/**                    ↑ ↑
/* 除以零 */
.foo {width: calc(100px + 80);}
/**                  ↑  ↑  ↑
/* `解析类型` 无效 */
.foo {width: calc(100% + 80);}
/**                  ↑ ↑  ↑
/* `解析类型` 无效 */
.foo {width: calc(100px - 80);}
/**                  ↑  ↑  ↑
/* `解析类型` 无效 */
.foo {width: calc(100px * 80px);}
/**                  ↑  ↑   ↑
/* `解析类型` 无效 */
.foo {width: calc(100 / 80%);}
/**                 ↑ ↑   ↑
/* `解析类型` 无效 */
```

-   `calc()` 必须接收一个表达式。
-   `calc()` 的参数之间必须有操作符。
-   `calc()` 不能除以 0。
-   [计算结果的类型](https://www.w3.org/TR/css-values-3/#calc-type-checking) 在对应的位置上，该结果的类型必须是有效的。

## 选项

### `true`

以下模式被视为违规：

```css
.foo {width: calc();}
```

```css
.foo {width: calc(100% 80px);}
```

```css
.foo {width: calc(100% - - 80px);}
```

```css
.foo {width: calc(100% / 0);}
```

```css
.foo {width: calc(100px + 80);}
```

以下模式*不*被视为违规：

```css
.foo {width: calc(100% - 80px);}
```

```css
.foo {width: calc(100% - var(--bar));}
```

```css
.foo {width: calc(var(--bar) - var(--baz));}
```
