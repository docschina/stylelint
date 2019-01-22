# max-nesting-depth

限制允许的嵌套深度。

```css
a { & > b { top: 0; } }
/** ↑
 * 这个嵌套 */
```

此规则的工作原理是检查规则和 @规则实际的“嵌套深度”是否违反指定的最大值。以下是嵌套深度的工作原理：

```css
a {
  & b { /* 嵌套深度 1 */
    & .foo { /* 嵌套深度 2 */
      @media print { /* 嵌套深度 3 */
        & .baz { /* 嵌套深度 4 */
          color: pink;
        }
      }
    }
  }
}
```

请注意，**根级别 @规则将*不会*计入嵌套深度中**，因为大多数用户会理所当然地认为根级别 @规则将是“豁免的”（因为必要）。所以以下两个 `.foo` 规则的嵌套深度均为 2，因此如果您的`最大值`小于或等于 2，它们将通过检查：

```css
a {
  b { /* 1 */
    .foo {} /* 2 */
  }
}

@media print { /* 被忽略 */
  a {
    b { /* 1 */
      .foo {} /* 2 */
    }
  }
}
```

此规则集成 [`stylelint-statement-max-nesting-depth`](https://github.com/davidtheclark/stylelint-statement-max-nesting-depth) 插件（现已弃用）的功能进入 stylelint 核心

## 选项

`int`: 允许的最大嵌套深度。

例如，使用 `2`：

以下模式被视为违规：

```css
a {
  & .foo { /* 1 */
    &__foo { /* 2 */
      & > .bar {} /* 3 */
    }
  }
}
```

```css
a {
  @media print { /* 1 */
    & .foo { /* 2 */
      & .bar {} /* 3 */
    }
  }
}
```

以下模式*不*被视为违规：

```css
a {
  & .foo { /* 1 */
    &__foo {} /* 2 */
  }
}

a .foo__foo .bar .baz {}
```

```css
@media print {
  a {
    & .foo { /* 1 */
      &__foo {} /* 2 */
    }
  }
}
```

## 可选的辅助选项

### `ignore: ["blockless-at-rules"]`

忽略仅包含其他规则并且本身不具有声明块的 @规则。

例如，使用 `1`：

以下模式被视为违规：

@规则有一个声明块。

```css
a {
  &:hover { /* 1 */
    @media (min-width: 500px) { color: pink; } /* 2 */
  }
}
```

```css
a {
  @nest > b { /* 1 */
    .foo { color: pink; } /* 2 */
  }
}
```

以下模式*不*被视为违规：

因为以下所有 `.foo` 规则的嵌套深度都只有1。

```css
a {
  .foo { color: pink; } /* 1 */
}
```

```css
@media print { /* 无论选项如何都被忽略 */
  a {
    .foo { color: pink; } /* 1 */
  }
}
```

```css
a {
  @media print { /* 被忽略，因为它是一个没有自己的声明块的规则 */
    .foo { color: pink; } /* 1 */
  }
}
```

### `ignore: ["pseudo-classes"]`

忽略每个选择器列表项中的第一个选择器是伪类的规则

例如，使用 `1`：

以下模式被视为违规：

```css
.a {
  .b { /* 1 */
    .c { /* 2 */
      top: 0;
    }
  }
}
```

```css
.a {
  &:hover { /* 被忽略 */
    .b { /* 1 */
      .c { /* 2 */
        top: 0;
      }
    }
  }
}
```

```css
.a {
  .b { /* 1 */
    &::selection { /* 2 */
      color: #64FFDA;
    }
  }
}
```

```css
.a {
  .b { /* 1 */
    &:hover, .c { /* 2 */
      top: 0;
    }
  }
}
```

以下模式*不*被视为违规：

As all of the following pseudoclasses rules would have a nesting depth of just 1.

```css
.a {
  .b { /* 1 */
    &:hover { /* 被忽略 */
      top: 0;
    }
  }
}
```

```css
.a {
  .b { /* 1 */
    &:nest {
      &:nest-lvl2 {  /* 被忽略 */
        top: 0;
      }
    }
  }
}
```

```css
.a {
  &:hover {  /* 被忽略 */
    .b { /* 1 */
      top: 0;
    }
  }
}
```

```css
.a {
  &:nest {  /* 被忽略 */
    &:nest-lvl2 {  /* 被忽略 */
      top: 0;
      .b { /* 1 */
        bottom: 0;
      }
    }
  }
}
```

```css
.a {
  .b { /* 1 */
    &:hover, &:focus {  /* 被忽略 */
      top: 0;
    }
  }
}
```

### `ignoreAtRules: ["/regex/", /regex/, "string"]`

忽略指定的 @规则。

例如，使用 `1` 并给定：

```js
["/^my-/", "media"]
```

以下模式*不*被视为违规：

```css
a {
  @media print {      /* 1 */
    b {               /* 2 */
      c { top: 0; }   /* 3 */
    }
  }
}
```

```css
a {
  b {                 /* 1 */
    @media print {    /* 2 */
      c { top: 0; }   /* 3 */
    }
  }
}
```

```css
a {
  @my-at-rule print {  /* 1 */
    b {                /* 2 */
      c { top: 0; }    /* 3 */
    }
  }
}
```

```css
a {
  @my-other-at-rule print {  /* 1 */
    b {                      /* 2 */
      c { top: 0; }          /* 3 */
    }
  }
}
```

以下模式被视为违规：

```css
a {
  @import print {       /* 1 */
    b { top: 0; }       /* 2 */
  }
}
```

```css
a {
  @not-my-at-rule print {   /* 1 */
    b { top: 0; }       /* 2 */
  }
}
```
