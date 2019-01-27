# 处理器

处理器是一些社区包，允许我们检查非样式表文件中样式。

*以下处理器仅用于命令行和 Node.js 环境，不能用于 PostCSS 插件。* (PostCSS 插件将会忽略这些处理器)

-   [stylelint-processor-arbitrary-tags](https://github.com/mapbox/stylelint-processor-arbitrary-tags): 用于检查特定标签中的样式。

stylelint 已经对许多常用的非样式表文件类型进行了内置支持。这意味着你不再需要如下一些处理器：

-   [stylelint-processor-glamorous](https://github.com/zabute/stylelint-processor-glamorous): 用于检查 [glamorous](https://github.com/paypal/glamorous) 以及基于对象字面量的 CSS-in-JS 方案中的样式。
-   [stylelint-processor-markdown](https://github.com/mapbox/stylelint-processor-markdown):  用于检查 Markdown 代码块中的样式（[fenced code blocks](https://help.github.com/articles/creating-and-highlighting-code-blocks/)）。
-   [stylelint-processor-styled-components](https://github.com/styled-components/stylelint-processor-styled-components): 用于检查 [styled-components](https://styled-components.com) 以及基于模板字面量的 CSS-in-JS 方案中的样式。
