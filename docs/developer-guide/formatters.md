# 编写 formatters

formatter 是一个接受参数为*一个数组里面是stylelint结果对象*然后输出string的格式化函数

```js
//一个 stylelint 结果对象
{
  source:  "path/to/file.css", // 文件路径或者PostCSS标识符（例如<input css 1>）
  errored: true, // 如果至少有一个规则是带有"error"-level 严格模式，触发一次警告，为true
  warnings: [ // 违反规则的警告对象数组，每一个对象例如下面这样...
    {
      line: 3,
      column: 12,
      rule: "block-no-empty",
      severity: "error",
      text: "You should not have an empty block (block-no-empty)"
    },
    ..
  ],
  deprecations: [ // 描述警告的对象数组，每一个对象例如下面这样...
    {
      text: "Feature X has been deprecated and will be removed in the next major version.",
      reference: "https://stylelint.io/docs/feature-x.md"
    }
  ],
  invalidOptionWarnings: [ // 非法选项警告对象数组，每一个对象例如下面这样...
    {
      text: "Invalid option X for rule Y",
    }
  ],
  ignored: false //如果文件的路径匹配一个提供的忽略模块,这个为true.
}
```

## `stylelint.formatters`

styelint的核心格式化器 在`stylelint.formatters`中暴露给外界

