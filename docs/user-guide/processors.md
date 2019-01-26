## 处理器
处理器是一些社区包，允许我们从非样式表文件中抽取样式来进行 `Stylelint`.

*以下处理器仅用于 `CLI` 和 `Node.js API` 环境，不能用于 `PostCSS` 插件。* (`PostCSS` 插件将会忽略这些处理器)

-   [stylelint-processor-arbitrary-tags](https://github.com/mapbox/stylelint-processor-arbitrary-tags): 用于在指定的标签中执行Lint。

stylelint 已经对许多公共的非样式表文件进行了内置支持。这意味着你不再需要如下一些处理器：

-   [stylelint-processor-glamorous](https://github.com/zabute/stylelint-processor-glamorous): 用于检查[glamorous](https://github.com/paypal/glamorous)以及基于对象字面量的CSS-in-JS方案中的样式。
```
var divStyle = { 
  width: '50px',
  height '50px'
};
```
-   [stylelint-processor-markdown](https://github.com/mapbox/stylelint-processor-markdown):  用于检查 Markdown 代码块中的样式（[fenced code blocks](https://help.github.com/articles/creating-and-highlighting-code-blocks/)）.

-   [stylelint-processor-styled-components](https://github.com/styled-components/stylelint-processor-styled-components): 用于检查[styled-components](https://styled-components.com)以及基于模板字符串的CSS-in-JS方案中的样式。
```js
export default styled.div`
  width: '50px',
  height '50px'
`
```
