# 处理规则

请帮助我们创建、增强和调试 stylelint 规则！

<!-- TOC -->

## 创建新规则

首先，开[一个问题](https://github.com/stylelint/stylelint/issues/new)，阐述您对新规则的想法。

通常我们会对规则的目的、名称、选项和适用性进行一些讨论。

### 收录标准

我们讨论规则是否符合以下以收录入 stylelint 的标准：

-   仅适用于标准 CSS 语法。
-   通用性；不依赖于特定模式。
-   具有清晰明确的完成状态。
-   有一个单一的目的。
-   是独立的，不依赖于其他规则。
-   不包含与其他规则重叠的功能。

否则，它应该是一个插件。但是插件也应该尽量遵守后三个标准。

### 为规则命名

查看[规则用户指南](../user-guide/about-rules.md)以熟悉规则命名约定。

我们一直很注重确保准确一致地命名所有规则。我们在这方面的目标是确保规则易于查找和理解，并防止我们以后想要更改命名。

*我们鼓励显式而非隐式选项来命名规则。* 例如 `color-hex-case: "upper"|"lower"` 而非 `color-hex-uppercase: "always"|"never"`。`color-hex-uppercase: "never"` *隐含*总是小写的语义，而 `color-hex-case: "lower"` 使语义更加*显式*。

### 确立选项

#### 主选项

每个规则*必须具有*一个**主选项**。

-   在 `"color-hex-case": "upper"` 中，主选项是 `"upper"`。
-   在 `"indentation": [2, { "except": ["block"] }]` 中，主选项是 `2`。

如果您的规则可以接受数组作为其主要选项，则必须通过在规则函数上设置属性 `primaryOptionArray = true` 来指定它。例如：

```js
function rule(primary, secondary) {
  return (root, result) => {..}
}
rule.primaryOptionArray = true
export default rule
// 或者，对于插件：stylelint.createPlugin(ruleName, rule)
```

这里有一点需要注意：如果您的规则接受主选项数组，则它也不能接受主选项对象。如果您希望规则接受主选项数组，您应该只允许一个数组，而不是允许各种数据结构。

#### 辅助选项

某些规则需要额外的灵活性来解决各种用例。这些可以使用**可选的辅助选项对象**。

-   在 `"color-hex-case": "upper"` 中，没有辅助选项对象。
-   在 `"indentation": [2, { "except": ["block"] }]` 中, 辅助选项对象是 `{ "except": ["block"] }`。

最典型的次要选项是 `"ignore": []` 和 `"except": []`；但任何数据都可以使用。

如果您不需要忽略或例外，规则的次要选项可以是任何内容。例如，在一些 `selector-*` 规则中使用 `resolveNestedSelectors: true|false` 来改变规则处理嵌套选择器的方式。

##### 关键字 `"ignore"` 和 `"except"`

`"ignore"` 和 `"except"` 接受一组预定义的关键字选项，例如 `["relative", "first-nested", "descendant"]`。

-   当您希望规则简单地跳过特定模式时，请使用 `"ignore"`。
-   当您想要反转特定模式的主要选项时，请使用 `"except"`。

##### 用户定义的 `"ignore*"`

在接受*用户定义的*要忽略的事物列表时，请使用更具体的辅助选项名称。这采取 `"ignore<Things>": []`，例如如果规则检查 @规则并且您想允许用户通过 `"ignoreAtRules": []` 指定要忽略哪些特定的 @规则类型。

### 确立违规消息

消息采用以下形式之一：

-   "预期的 \[某物\] \[在某上下文\]"
-   "非预期的 \[某物\] \[在某上下文\]"

查看其他规则的消息，以了解更多的约定和模式。

### 编写规则

*在编写规则时，请始终查看其他类似规则的约定和模式，以便从模仿开始。*

您将使用简单的 [PostCSS 应用程序接口](https://api.postcss.org/)来导航和分析 CSS 语法树。我们建议使用 `walk` 迭代器（例如 `walkDecls`），而不是使用 `forEach` 来遍历节点。

根据规则不同，我们还建议使用 [postcss-value-parser](https://github.com/TrySound/postcss-value-parser) 和 [postcss-selector-parser](https://github.com/postcss/postcss-selector-parser)。使用这些解析器而不是正则表达式或 `indexOf` 搜索有很多好处（即使它们并不总是最高效的方法）。

stylelint 有许多[实用函数](https://github.com/stylelint/stylelint/tree/master/lib/utils)，它们在现有规则中使用，也可能对您有用。请仔细查看，以便了解可用的内容。（如果您有一个您认为可能通用的新功能，那么让我们把它添加到列表中！）。您肯定希望使用 `validateOptions()`，以便警告用户无效选项。（查看其他规则的选项验证示例将有很大帮助。） 您还应该使用 `isStandardSyntax*` 实用程序来忽略非标准语法。

*默认情况下*, 规则应更严格。用户可以通过使用 `"ignore*:"` 辅助选项使规则更加宽松。

规则不应包含方法论或语言扩展的代码。相反，提供通用的辅助选项，以便用户可以在*配置级别*忽略这些选项。例如，在处理特异性时，规则不应该考虑 `:global` 和 `:local` 伪类（在 CSS 模块语言扩展中引入），而规则应该提供 `ignorePseudoClasses: []` 辅助选项。方法论来的快，去得也快，这种实践可以确保代码库不会被过时的代码所困扰。

仅在规则处理有实际用例*需求*时才添加选项。如果没有需求，即便是为了保持一致性，也不要为规则添加选项。这是为了避免未使用的功能污染工具。

### 添加自动修复

根据规则不同，可以通过使用 [PostCSS 应用程序接口](http://api.postcss.org/)改变 PostCSS AST（抽象语法树）来自动修复违规。

将 `context` 变量添加到规则参数：

```js
function rule(primary, secondary, context) {
  return (root, result) => {..}
}
```

`context` 是一个可以有两个属性的对象：

-   `fix`(boolean)：如果为 `true`，您的规则可以应用自动修复。
-   `newline`(string)：当前检查的文件中使用的换行符。

如果 `context.fix` 为 `true`，那么使用 PostCSS 应用程序接口更改 `root` 并在调用 `report()` 之前返回。

```js
if (context.fix) {
  // 使用 PostCSS 应用程序接口应用修复
  return // 返回并且不报告问题
}

report(...)
```

### 编写测试

每条规则必须附带包含以下内容的测试：

-   所有被视为违规的模式。
-   所有应该*不*被视为违规的模式。

编写 stylelint 测试很容易，所以请*尽可能多地编写*。

#### 清单

请仔细检查此清单，确保测试涵盖每个点。特别是*考虑边缘情况*。这些都是规则中总是出现 bug 和缺点的地方。

##### 最佳实践

-   确保您在多个位置测试错误，而不是每次都在同一个位置。
-   确保使用真实的（如果简单的）CSS，并避免使用省略号。
-   确保默认使用标准 CSS 语法，并且在测试特定的非标准语法时仅交换解析器。
-   从 PostCSS AST 访问原始字符串时，使用 `node.raws` 而不是 `node.raw()`。这将确保字符串与原始字符串完全对应。

##### 通常被忽视的边缘情况

-   您的规则如何处理变量（`$sass`、`@less` 或 `var(--custom-property)`）？
-   您的规则如何处理 CSS 字符串（例如 `content: "anything goes";`）？
-   您的规则如何处理 CSS 注释（例如 `/* anything goes */`）？
-   您的规则如何处理 `url()` 函数, 包括 data URIs（例如 `url(anything/goes.jpg)`）？
-   您的规则如何处理供应商前缀（例如 `@-webkit-keyframes name {}`）？
-   您的规则如何处理字母大小写（例如 `@KEYFRAMES name {}`）？
-   您的规则如何处理伪类与伪元素的*组合*（例如 `a:hover::before`）？
-   您的规则如何处理嵌套（例如 do you resolve `& a {}`, or check it as is?）？
-   您的规则如何处理空白符和标点符号（例如 comparing `rgb(0,0,0)` with `rgb(0, 0, 0)`）？

#### 运行测试

您可以通过以下方式运行测试：

```console
npm test
```

然后，这将运行所有 25,000 多个单元测试，也将检查代码。

您可以使用交互式测试提示来仅针对一组选定的规则（您在开发期间要执行的操作）运行测试。例如，仅针对 `color-hex-case` 和 `color-hex-length` 规则运行测试：

1.  运行 `npm run watch` 以启动交互式测试提示。
2.  按 `p` 按文件名正则表达式模式过滤。
3.  输入 `color-hex-case|color-hex-length`，即每个规则名称用管道符号（`|`）分隔。

### 编写自述文档

每条规则必须附有自述文档，符合以下格式：

1.  规则名称。
2.  单行描述。
3.  原型代码示例。
4.  扩展描述（如有必要）。
5.  选项。
6.  被视为违规的模式示例（针对每个选项值）。
7.  *不*被视为违规的模式示例（对于每个选项值）。
8.  可选选项（如适用）。

查看其他规则的自述文件以了解更多约定模式。这些包括：

-   使用“此规则”来引用该规则，例如 “此规则忽略...”
-   将原型代码示例中的箭头与突出显示的构造的开头对齐。
-   将原型代码示例中的文本尽量对齐。

例如：

```css
 @media screen and (min-width: 768px) {}
/**                 ↑          ↑
  *                  这些名称和值 */
```

#### 单行描述

采取以下形式：

-   “禁止...” (对于 `no` 规则)。
-   “限制...” (对于 `max` 规则)。
-   “要求...” (对于接受 `"always"` 和 `"never"` 选项的规则)。
-   “指定...” (其他所有)。

#### 示例模式

-   使用完整的 CSS 模式，即避免省略号（`...`）
-   默认情况下使用标准 CSS 语法（和 `css` 受控代码块）。
-   使用尽可能少的代码来传达模式，例如如果规则定位于选择器，则使用空规则，例如 `{}`。
-   对于空规则，使用`{}`而不是`{ }`。
-   默认情况下使用 `a` 类型选择器。
-   默认情况下使用 `@media` @规则。
-   默认情况下使用 `color` 属性。
-   使用 *foo*、*bar* 和 *baz* 作为名称，例如 `.foo`、`#bar`、`--baz`

### 完成规则编写

最后一步是在以下位置添加对新规则的引用：

-   [规则 `index.js` 文件](https://github.com/stylelint/stylelint/blob/master/lib/rules/index.js)
-   [规则列表](../user-guide/rules.md)
-   [示例配置](../user-guide/example-config.md)

一旦您有展示的东西，创建一个[拉取请求](https://github.com/stylelint/stylelint/compare)继续讨论。

## 向现有规则添加选项

首先，开[一个问题](https://github.com/stylelint/stylelint/issues/new)，阐述您想添加的选项。我们将在那里讨论它的功能和名称。

一旦我们就方向达成一致，您就可以处理拉取请求。以下是您需要采取的步骤：

1.  运行 `npm run watch` 以启动交互式测试提示。
2.  使用 `p` 命令将活动测试过滤为您正在处理的规则。
3.  更改规则的验证以允许新选项。
4.  向规则添加一些逻辑（尽可能少）以使选项有效。
5.  添加新的单元测试以测试该选项。
6.  添加有关新选项的文档。

## 修复现有规则中的 bug

修复错误通常很容易。这是一个有效的过程：

1.  运行 `npm run watch` 以启动交互式测试提示。
2.  使用 `p` 命令将活动测试过滤为您正在处理的规则。
3.  编写示例错误的失败单元测试。
4.  处理规则，直到这些新测试通过。

就这些！**如果您无法修复 bug，那么在您的测试用例失败的情况下提交拉取请求仍然很有用的。** 这意味着其他人可以直接接手并帮助解决规则的逻辑问题。

## 弃用规则

弃用规则不会经常发生。但是，这两个步骤很重要：

1.  将 `stylelintReference` 链接指向 GitHub 网站上规则自述文档的特定版本，以便始终可以访问它。
2.  添加适当的元数据以将规则标记为已弃用。

## 提高规则的性能

有一种简单的方法可以在任何给定规则上运行基准测试，并为其提供任何有效配置：

```shell
npm run benchmark-rule -- [rule-name] [config]
```

如果 `config` 参数不是字符串或布尔值，它必须是用引号括起来的有效 JSON。

```shell
npm run benchmark-rule -- selector-combinator-space-after never
```

```shell
npm run benchmark-rule -- selector-combinator-space-after always
```

```shell
npm run benchmark-rule -- selector-no-combinator true
```

```shell
npm run benchmark-rule -- block-opening-brace-space-before "[\"always\", {\"ignoreAtRules\": [\"else\"]}]"
```

该脚本加载 Bootstrap 的 CSS（来自其 CDN）并通过配置的规则运行它。

它最终将打印一些简单的统计数据：

```shell
Warnings: 1441
Mean: 74.17598357142856 ms
Deviation: 16.63969674310928 ms
```

您能用这个做什么？ **在编写新规则或重构现有规则时，请使用这些度量来确定代码的效率。**

stylelint 规则会多次重复它的核心逻辑（例如，检查庞大的 CSS 代码库中每个声明的每个值节点）。所以性能值得我们关注并竭尽所能来改进它！

**如果您只想要一个快速的小项目，这是一个很好的贡献方式。** 尝试选择规则并查看是否有任何可以做的事情来加速它。

确保在拉取请求中包含基准测量！
