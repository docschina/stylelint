# 规则

规则确定了代码检查工具寻找和指正的内容。默认情况下，所有规则都处于关闭状态，并且没有任何规则的默认值。规则遵循一致的命名约定，并且设计为彼此协同工作，您可以在[“关于规则”](about-rules.md)部分中阅读更多相关信息。

内置规则适用于标准 CSS 语法，除了 `indentation` 规则之外，所有规则都将忽略包含非标准语法的结构，例如变量插值和混合。

除了这些规则之外，还有[插件](plugins.md)，它们是社区构建的规则，支持方法论、工具集、*非标准* CSS 功能或非常具体的用例。不要忘记查看[插件](plugins.md)列表以获取更多检查方法。

## 规则列表

以下是 stylelint 中的所有内置规则，首先[按类别](../../VISION.md)，然后按[*事物*](http://apps.workflower.fi/vocabs/css/en)分组。

-   [可能错误](#可能错误)
-   [限制语言功能](#限制语言功能)
-   [风格问题](#风格问题)

### 可能错误

#### 颜色

-   [`color-no-invalid-hex`](../../lib/rules/color-no-invalid-hex/README.md)：禁止无效的 16 进制颜色。

#### 字体族

-   [`font-family-no-duplicate-names`](../../lib/rules/font-family-no-duplicate-names/README.md)：禁止重复的字体族名称。
-   [`font-family-no-missing-generic-family-keyword`](../../lib/rules/font-family-no-missing-generic-family-keyword/README.md)：禁止在字体族名称列表中缺少通用字体族关键字。

#### 函数

-   [`function-calc-no-invalid`](../../lib/rules/function-calc-no-invalid/README.md)：禁止在 `calc` 函数中使用无效表达式。
-   [`function-calc-no-unspaced-operator`](../../lib/rules/function-calc-no-unspaced-operator/README.md)：禁止在 `calc` 函数中使用没有间隔的运算符。
-   [`function-linear-gradient-no-nonstandard-direction`](../../lib/rules/function-linear-gradient-no-nonstandard-direction/README.md)：禁止在 `linear-gradient()` 中调用不符合标准语法的无效方向值。

#### 字符串

-   [`string-no-newline`](../../lib/rules/string-no-newline/README.md)：禁止字符串中的(未转义)换行符。

#### 单位

-   [`unit-no-unknown`](../../lib/rules/unit-no-unknown/README.md)：禁止未知的单位。

#### 属性

-   [`property-no-unknown`](../../lib/rules/property-no-unknown/README.md)：禁止未知的属性。

#### 关键帧声明

-   [`keyframe-declaration-no-important`](../../lib/rules/keyframe-declaration-no-important/README.md)：禁止关键帧声明的 `!important`。

#### 声明块

-   [`declaration-block-no-duplicate-properties`](../../lib/rules/declaration-block-no-duplicate-properties/README.md)：禁止声明块的重复属性。
-   [`declaration-block-no-shorthand-property-overrides`](../../lib/rules/declaration-block-no-shorthand-property-overrides/README.md)：禁止简写属性覆盖相关的扩写属性。

#### 块

-   [`block-no-empty`](../../lib/rules/block-no-empty/README.md)：禁止空块。

#### 选择器

-   [`selector-pseudo-class-no-unknown`](../../lib/rules/selector-pseudo-class-no-unknown/README.md)：禁止未知的伪类选择器。
-   [`selector-pseudo-element-no-unknown`](../../lib/rules/selector-pseudo-element-no-unknown/README.md)：禁止未知的伪元素选择器。
-   [`selector-type-no-unknown`](../../lib/rules/selector-type-no-unknown/README.md)：禁止未知的类型选择器。

#### 媒体功能

-   [`media-feature-name-no-unknown`](../../lib/rules/media-feature-name-no-unknown/README.md)：禁止未知的媒体功能名。

####@规则

-   [`at-rule-no-unknown`](../../lib/rules/at-rule-no-unknown/README.md)：禁止未知的@规则。

#### 注释

-   [`comment-no-empty`](../../lib/rules/comment-no-empty/README.md)：禁止空注释。

#### 一般/表

-   [`no-descending-specificity`](../../lib/rules/no-descending-specificity/README.md)：禁止在具有较高优先级的选择器后出现被其覆盖的较低优先级的选择器。
-   [`no-duplicate-at-import-rules`](../../lib/rules/no-duplicate-at-import-rules/README.md)：禁止在样式表中使用重复的 `@import` 规则。
-   [`no-duplicate-selectors`](../../lib/rules/no-duplicate-selectors/README.md)：禁止样式表中的重复选择器。
-   [`no-empty-source`](../../lib/rules/no-empty-source/README.md)：禁止空源码。
-   [`no-extra-semicolons`](../../lib/rules/no-extra-semicolons/README.md)：禁止额外的分号（可自动修复）。
-   [`no-invalid-double-slash-comments`](../../lib/rules/no-invalid-double-slash-comments/README.md)：禁止 CSS 不支持并可能导致意外结果的双斜杠注释（`//...`）。

### 限制语言功能

#### 颜色

-   [`color-named`](../../lib/rules/color-named/README.md)：要求（如果可能）或禁止命名颜色。
-   [`color-no-hex`](../../lib/rules/color-no-hex/README.md)：禁止 16 进制颜色。

#### 函数

-   [`function-blacklist`](../../lib/rules/function-blacklist/README.md)：指定禁用的函数的黑名单。
-   [`function-url-no-scheme-relative`](../../lib/rules/function-url-no-scheme-relative/README.md)：禁止相对协议 URL。
-   [`function-url-scheme-blacklist`](../../lib/rules/function-url-scheme-blacklist/README.md)：指定禁用的 URL 协议的黑名单。
-   [`function-url-scheme-whitelist`](../../lib/rules/function-url-scheme-whitelist/README.md)：指定允许的 URL 协议的白名单。
-   [`function-whitelist`](../../lib/rules/function-whitelist/README.md)：指定允许的函数的白名单。

#### 关键帧

-   [`keyframes-name-pattern`](../../lib/rules/keyframes-name-pattern/README.md)：指定关键帧名的模式。

#### 数字

-   [`number-max-precision`](../../lib/rules/number-max-precision/README.md)：限制数字中允许的小数位数

#### 时间

-   [`time-min-milliseconds`](../../lib/rules/time-min-milliseconds/README.md)：指定时间值的最小毫秒数。

#### 单位

-   [`unit-blacklist`](../../lib/rules/unit-blacklist/README.md)：指定禁用的单位的黑名单。
-   [`unit-whitelist`](../../lib/rules/unit-whitelist/README.md)：指定允许的单位的白名单。

#### 简写属性

-   [`shorthand-property-no-redundant-values`](../../lib/rules/shorthand-property-no-redundant-values/README.md)：禁止简写属性的冗余值（可自动修复）。

#### 值

-   [`value-no-vendor-prefix`](../../lib/rules/value-no-vendor-prefix/README.md)：禁止值的浏览器引擎前缀。

#### 自定义属性

-   [`custom-property-pattern`](../../lib/rules/custom-property-pattern/README.md)：指定自定义属性的模式。

#### 属性

-   [`property-blacklist`](../../lib/rules/property-blacklist/README.md)：指定禁用的属性的黑名单。
-   [`property-no-vendor-prefix`](../../lib/rules/property-no-vendor-prefix/README.md)：禁止属性的浏览器引擎前缀。
-   [`property-whitelist`](../../lib/rules/property-whitelist/README.md)：指定允许的属性的白名单。

#### 声明

-   [`declaration-block-no-redundant-longhand-properties`](../../lib/rules/declaration-block-no-redundant-longhand-properties/README.md)：禁止可合并为一个简写属性的扩写属性。
-   [`declaration-no-important`](../../lib/rules/declaration-no-important/README.md)：禁止声明的 `!important`。
-   [`declaration-property-unit-blacklist`](../../lib/rules/declaration-property-unit-blacklist/README.md)：指定声明内禁用的属性和单位对的黑名单。
-   [`declaration-property-unit-whitelist`](../../lib/rules/declaration-property-unit-whitelist/README.md)：指定声明内允许的属性和单位对的白名单。
-   [`declaration-property-value-blacklist`](../../lib/rules/declaration-property-value-blacklist/README.md)：指定声明内禁用的属性和值对的黑名单。
-   [`declaration-property-value-whitelist`](../../lib/rules/declaration-property-value-whitelist/README.md)：指定声明内允许的属性和值对的白名单。

#### 声明块

-   [`declaration-block-single-line-max-declarations`](../../lib/rules/declaration-block-single-line-max-declarations/README.md)：限制一个单行声明块中声明的数量

#### 选择器

-   [`selector-attribute-operator-blacklist`](../../lib/rules/selector-attribute-operator-blacklist/README.md)：指定禁用的属性运算符的黑名单。
-   [`selector-attribute-operator-whitelist`](../../lib/rules/selector-attribute-operator-whitelist/README.md)：指定允许的属性运算符的白名单。
-   [`selector-class-pattern`](../../lib/rules/selector-class-pattern/README.md)：指定类选择器的模式。
-   [`selector-combinator-blacklist`](../../lib/rules/selector-combinator-blacklist/README.md)：指定禁用的组合选择器的黑名单。
-   [`selector-combinator-whitelist`](../../lib/rules/selector-combinator-whitelist/README.md)：指定允许的组合选择器的白名单。
-   [`selector-id-pattern`](../../lib/rules/selector-id-pattern/README.md)：指定 ID 选择器的模式。
-   [`selector-max-attribute`](../../lib/rules/selector-max-attribute/README.md)：限制一个选择器中属性选择器的数量
-   [`selector-max-class`](../../lib/rules/selector-max-class/README.md)：限制一个选择器中类的数量
-   [`selector-max-combinators`](../../lib/rules/selector-max-combinators/README.md)：限制一个选择器中组合选择器的数量
-   [`selector-max-compound-selectors`](../../lib/rules/selector-max-compound-selectors/README.md)：限制一个选择器中复合选择器的数量
-   [`selector-max-empty-lines`](../../lib/rules/selector-max-empty-lines/README.md)：限制选择器中相邻空行的数量
-   [`selector-max-id`](../../lib/rules/selector-max-id/README.md)：限制一个选择器中 ID 选择器的数量
-   [`selector-max-pseudo-class`](../../lib/rules/selector-max-pseudo-class/README.md)：限制一个选择器中伪类的数量
-   [`selector-max-specificity`](../../lib/rules/selector-max-specificity/README.md)：限制选择器的优先级。
-   [`selector-max-type`](../../lib/rules/selector-max-type/README.md)：限制一个选择器中类型选择器的数量
-   [`selector-max-universal`](../../lib/rules/selector-max-universal/README.md)：限制一个选择器中通用选择器的数量
-   [`selector-nested-pattern`](../../lib/rules/selector-nested-pattern/README.md)：指定嵌套规则的选择器的模式。
-   [`selector-no-qualifying-type`](../../lib/rules/selector-no-qualifying-type/README.md)：禁止用类型选择器来限定一个选择器。
-   [`selector-no-vendor-prefix`](../../lib/rules/selector-no-vendor-prefix/README.md)：禁止选择器的浏览器引擎前缀。
-   [`selector-pseudo-class-blacklist`](../../lib/rules/selector-pseudo-class-blacklist/README.md)：指定禁用的伪类选择器的黑名单。
-   [`selector-pseudo-class-whitelist`](../../lib/rules/selector-pseudo-class-whitelist/README.md)：指定允许的伪类选择器的白名单。
-   [`selector-pseudo-element-blacklist`](../../lib/rules/selector-pseudo-element-blacklist/README.md)：指定禁用的伪元素选择器的黑名单。
-   [`selector-pseudo-element-whitelist`](../../lib/rules/selector-pseudo-element-whitelist/README.md)：指定允许的伪元素选择器的白名单。

#### 媒体功能

-   [`media-feature-name-blacklist`](../../lib/rules/media-feature-name-blacklist/README.md)：指定禁用的媒体功能名的黑名单。
-   [`media-feature-name-no-vendor-prefix`](../../lib/rules/media-feature-name-no-vendor-prefix/README.md)：禁止媒体功能名的浏览器引擎前缀。
-   [`media-feature-name-value-whitelist`](../../lib/rules/media-feature-name-value-whitelist/README.md)：指定允许的媒体功能名和值对的白名单。
-   [`media-feature-name-whitelist`](../../lib/rules/media-feature-name-whitelist/README.md)：指定允许的媒体功能名的白名单。

#### 自定义媒体

-   [`custom-media-pattern`](../../lib/rules/custom-media-pattern/README.md)：指定自定义媒体查询名的模式。

####@规则

-   [`at-rule-blacklist`](../../lib/rules/at-rule-blacklist/README.md)：指定禁用的@规则的黑名单。
-   [`at-rule-no-vendor-prefix`](../../lib/rules/at-rule-no-vendor-prefix/README.md)：禁止@规则的浏览器引擎前缀。
-   [`at-rule-whitelist`](../../lib/rules/at-rule-whitelist/README.md)：指定允许的@规则的白名单。

#### 注释

-   [`comment-word-blacklist`](../../lib/rules/comment-word-blacklist/README.md)：指定在注释中禁用的单词的黑名单。

#### 一般/表

-   [`max-nesting-depth`](../../lib/rules/max-nesting-depth/README.md)：限制允许的嵌套深度。
-   [`no-unknown-animations`](../../lib/rules/no-unknown-animations/README.md)：禁止未知的动画。

### 风格问题

#### 颜色

-   [`color-hex-case`](../../lib/rules/color-hex-case/README.md)：指定 16 进制颜色的大小写（可自动修复）。
-   [`color-hex-length`](../../lib/rules/color-hex-length/README.md)：指定 16 进制颜色的简写或扩写（可自动修复）。

#### 字体族

-   [`font-family-name-quotes`](../../lib/rules/font-family-name-quotes/README.md)：指定是否应在字体族名称周围使用引号。

#### 字体粗细

-   [`font-weight-notation`](../../lib/rules/font-weight-notation/README.md)：要求 `font-weight` 使用数字或命名（如果可能）值。此外，当需要命名值时，要求名称有效。

#### 函数

-   [`function-comma-newline-after`](../../lib/rules/function-comma-newline-after/README.md)：要求在函数的逗号之后必须有换行符或不能有空白符（可自动修复）。
-   [`function-comma-newline-before`](../../lib/rules/function-comma-newline-before/README.md)：要求在函数的逗号之前必须有换行符或不能有空白符（可自动修复）。
-   [`function-comma-space-after`](../../lib/rules/function-comma-space-after/README.md)：要求在函数的逗号之后必须有一个空格或不能有空白符（可自动修复）。
-   [`function-comma-space-before`](../../lib/rules/function-comma-space-before/README.md)：要求在函数的逗号之前必须有一个空格或不能有空白符（可自动修复）。
-   [`function-max-empty-lines`](../../lib/rules/function-max-empty-lines/README.md)：限制函数中相邻空行的数量（可自动修复）
-   [`function-name-case`](../../lib/rules/function-name-case/README.md)：指定函数名的大小写（可自动修复）。
-   [`function-parentheses-newline-inside`](../../lib/rules/function-parentheses-newline-inside/README.md)：要求在函数的括号内侧必须有换行符或不能有空白符（可自动修复）。
-   [`function-parentheses-space-inside`](../../lib/rules/function-parentheses-space-inside/README.md)：要求在函数的括号内侧必须有一个空格或不能有空白符（可自动修复）。
-   [`function-url-quotes`](../../lib/rules/function-url-quotes/README.md)：要求或禁止 URL 的引号。
-   [`function-whitespace-after`](../../lib/rules/function-whitespace-after/README.md)：要求或禁止函数之后的空白符（可自动修复）。

#### 数字

-   [`number-leading-zero`](../../lib/rules/number-leading-zero/README.md)：要求或禁止小于 1 的小数有一个前导零（可自动修复）。
-   [`number-no-trailing-zeros`](../../lib/rules/number-no-trailing-zeros/README.md)：禁止数量的尾随零（可自动修复）。

#### 字符串

-   [`string-quotes`](../../lib/rules/string-quotes/README.md)：指定字符串使用单引号或双引号（可自动修复）。

#### 长度

-   [`length-zero-no-unit`](../../lib/rules/length-zero-no-unit/README.md)：禁止零长度的单位（可自动修复）。

#### 单位

-   [`unit-case`](../../lib/rules/unit-case/README.md)：指定单位的大小写（可自动修复）。

#### 值

-   [`value-keyword-case`](../../lib/rules/value-keyword-case/README.md)：指定关键字值的大小写（可自动修复）。

#### 值列表

-   [`value-list-comma-newline-after`](../../lib/rules/value-list-comma-newline-after/README.md)：要求在值列表的逗号之后必须有换行符或不能有空白符（可自动修复）。
-   [`value-list-comma-newline-before`](../../lib/rules/value-list-comma-newline-before/README.md)：要求在值列表的逗号之前必须有换行符或不能有空白符。
-   [`value-list-comma-space-after`](../../lib/rules/value-list-comma-space-after/README.md)：要求在值列表的逗号之后必须有一个空格或不能有空白符（可自动修复）。
-   [`value-list-comma-space-before`](../../lib/rules/value-list-comma-space-before/README.md)：要求在值列表的逗号之前必须有一个空格或不能有空白符（可自动修复）。
-   [`value-list-max-empty-lines`](../../lib/rules/value-list-max-empty-lines/README.md)：限制值列表中相邻空行的数量（可自动修复）

#### 自定义属性

-   [`custom-property-empty-line-before`](../../lib/rules/custom-property-empty-line-before/README.md)：要求或禁止在自定义属性之前的空行（可自动修复）。

#### 属性

-   [`property-case`](../../lib/rules/property-case/README.md)：指定属性的大小写（可自动修复）。

#### 声明

-   [`declaration-bang-space-after`](../../lib/rules/declaration-bang-space-after/README.md)：要求在声明的叹号之后必须有一个空格或不能有空白符（可自动修复）。
-   [`declaration-bang-space-before`](../../lib/rules/declaration-bang-space-before/README.md)：要求在声明的叹号之前必须有一个空格或不能有空白符（可自动修复）。
-   [`declaration-colon-newline-after`](../../lib/rules/declaration-colon-newline-after/README.md)：要求在声明块的冒号之后必须有换行符或不能有空白符（可自动修复）。
-   [`declaration-colon-space-after`](../../lib/rules/declaration-colon-space-after/README.md)：要求在声明块的冒号之后必须有一个空格或不能有空白符（可自动修复）。
-   [`declaration-colon-space-before`](../../lib/rules/declaration-colon-space-before/README.md)：要求在声明块的冒号之前必须有一个空格或不能有空白符（可自动修复）。
-   [`declaration-empty-line-before`](../../lib/rules/declaration-empty-line-before/README.md)：要求或禁止在声明之前的空行（可自动修复）。

#### 声明块

-   [`declaration-block-semicolon-newline-after`](../../lib/rules/declaration-block-semicolon-newline-after/README.md)：要求在声明块的分号之后必须有换行符或不能有空白符（可自动修复）。
-   [`declaration-block-semicolon-newline-before`](../../lib/rules/declaration-block-semicolon-newline-before/README.md)：要求在声明块的分号之前必须有换行符或不能有空白符。
-   [`declaration-block-semicolon-space-after`](../../lib/rules/declaration-block-semicolon-space-after/README.md)：要求在声明块的分号之后必须有一个空格或不能有空白符（可自动修复）。
-   [`declaration-block-semicolon-space-before`](../../lib/rules/declaration-block-semicolon-space-before/README.md)：要求在声明块的分号之前必须有一个空格或不能有空白符（可自动修复）。
-   [`declaration-block-trailing-semicolon`](../../lib/rules/declaration-block-trailing-semicolon/README.md)：要求或禁止声明块的一个尾随分号（可自动修复）。

#### 块

-   [`block-closing-brace-empty-line-before`](../../lib/rules/block-closing-brace-empty-line-before/README.md)：要求或禁止在块的闭大括号之前空行（可自动修复）。
-   [`block-closing-brace-newline-after`](../../lib/rules/block-closing-brace-newline-after/README.md)：要求在块的闭大括号之后必须有换行符或不能有空白符（可自动修复）。
-   [`block-closing-brace-newline-before`](../../lib/rules/block-closing-brace-newline-before/README.md)：要求在块的闭大括号之前必须有换行符或不能有空白符（可自动修复）。
-   [`block-closing-brace-space-after`](../../lib/rules/block-closing-brace-space-after/README.md)：要求在块的闭大括号之后必须有一个空格或不能有空白符。
-   [`block-closing-brace-space-before`](../../lib/rules/block-closing-brace-space-before/README.md)：要求在块的闭大括号之前必须有一个空格或不能有空白符（可自动修复）。
-   [`block-opening-brace-newline-after`](../../lib/rules/block-opening-brace-newline-after/README.md)：要求在块的开大括号之后必须有换行符（可自动修复）。
-   [`block-opening-brace-newline-before`](../../lib/rules/block-opening-brace-newline-before/README.md)：要求在块的开大括号之前必须有换行符或不能有空白符（可自动修复）。
-   [`block-opening-brace-space-after`](../../lib/rules/block-opening-brace-space-after/README.md)：要求在块的开大括号之后必须有一个空格或不能有空白符（可自动修复）。
-   [`block-opening-brace-space-before`](../../lib/rules/block-opening-brace-space-before/README.md)：要求在块的开大括号之前必须有一个空格或不能有空白符（可自动修复）。

#### 选择器

-   [`selector-attribute-brackets-space-inside`](../../lib/rules/selector-attribute-brackets-space-inside/README.md)：要求在属性选择器的中括号内侧必须有一个空格或不能有空白符（可自动修复）。
-   [`selector-attribute-operator-space-after`](../../lib/rules/selector-attribute-operator-space-after/README.md)：要求在属性选择器中的运算符之后必须有一个空格或不能有空白符（可自动修复）。
-   [`selector-attribute-operator-space-before`](../../lib/rules/selector-attribute-operator-space-before/README.md)：要求在属性选择器中的运算符之前必须有一个空格或不能有空白符（可自动修复）。
-   [`selector-attribute-quotes`](../../lib/rules/selector-attribute-quotes/README.md)：要求或禁止属性值的引号。
-   [`selector-combinator-space-after`](../../lib/rules/selector-combinator-space-after/README.md)：要求在组合选择器之后必须有一个空格或不能有空白符（可自动修复）。
-   [`selector-combinator-space-before`](../../lib/rules/selector-combinator-space-before/README.md)：要求在组合选择器之前必须有一个空格或不能有空白符（可自动修复）。
-   [`selector-descendant-combinator-no-non-space`](../../lib/rules/selector-descendant-combinator-no-non-space/README.md)：禁止后代选择器使用非空格字符（可自动修复）。
-   [`selector-pseudo-class-case`](../../lib/rules/selector-pseudo-class-case/README.md)：指定伪类选择器的大小写（可自动修复）。
-   [`selector-pseudo-class-parentheses-space-inside`](../../lib/rules/selector-pseudo-class-parentheses-space-inside/README.md)：要求在伪类选择器的括号内侧必须有一个空格或不能有空白符（可自动修复）。
-   [`selector-pseudo-element-case`](../../lib/rules/selector-pseudo-element-case/README.md)：指定伪元素选择器的大小写。
-   [`selector-pseudo-element-colon-notation`](../../lib/rules/selector-pseudo-element-colon-notation/README.md)：指定伪元素适用单冒号还是双冒号表示法（可自动修复）。
-   [`selector-type-case`](../../lib/rules/selector-type-case/README.md)：指定类型选择器的大小写（可自动修复）。

#### 选择器列表

-   [`selector-list-comma-newline-after`](../../lib/rules/selector-list-comma-newline-after/README.md)：要求在选择器列表的逗号之后必须有换行符或不能有空白符（可自动修复）。
-   [`selector-list-comma-newline-before`](../../lib/rules/selector-list-comma-newline-before/README.md)：要求在选择器列表的逗号之前必须有换行符或不能有空白符（可自动修复）。
-   [`selector-list-comma-space-after`](../../lib/rules/selector-list-comma-space-after/README.md)：要求在选择器列表的逗号之后必须有一个空格或不能有空白符（可自动修复）。
-   [`selector-list-comma-space-before`](../../lib/rules/selector-list-comma-space-before/README.md)：要求在选择器列表的逗号之前必须有一个空格或不能有空白符（可自动修复）。

#### 规则

-   [`rule-empty-line-before`](../../lib/rules/rule-empty-line-before/README.md)：要求或禁止在规则之前的空行（可自动修复）。

#### 媒体功能

-   [`media-feature-colon-space-after`](../../lib/rules/media-feature-colon-space-after/README.md)：要求在媒体功能的冒号之后必须有一个空格或不能有空白符（可自动修复）。
-   [`media-feature-colon-space-before`](../../lib/rules/media-feature-colon-space-before/README.md)：要求在媒体功能的冒号之前必须有一个空格或不能有空白符（可自动修复）。
-   [`media-feature-name-case`](../../lib/rules/media-feature-name-case/README.md)：指定媒体功能名的大小写（可自动修复）。
-   [`media-feature-parentheses-space-inside`](../../lib/rules/media-feature-parentheses-space-inside/README.md)：要求在媒体功能的括号内侧必须有一个空格或不能有空白符（可自动修复）。
-   [`media-feature-range-operator-space-after`](../../lib/rules/media-feature-range-operator-space-after/README.md)：要求在媒体功能的范围运算符之后必须有一个空格或不能有空白符（可自动修复）。
-   [`media-feature-range-operator-space-before`](../../lib/rules/media-feature-range-operator-space-before/README.md)：要求在媒体功能的范围运算符之前必须有一个空格或不能有空白符（可自动修复）。

#### 媒体查询列表

-   [`media-query-list-comma-newline-after`](../../lib/rules/media-query-list-comma-newline-after/README.md)：要求在媒体查询列表的逗号之后必须有换行符或不能有空白符（可自动修复）。
-   [`media-query-list-comma-newline-before`](../../lib/rules/media-query-list-comma-newline-before/README.md)：要求在媒体查询列表的逗号之前必须有换行符或不能有空白符。
-   [`media-query-list-comma-space-after`](../../lib/rules/media-query-list-comma-space-after/README.md)：要求在媒体查询列表的逗号之后必须有一个空格或不能有空白符（可自动修复）。
-   [`media-query-list-comma-space-before`](../../lib/rules/media-query-list-comma-space-before/README.md)：要求在媒体查询列表的逗号之前必须有一个空格或不能有空白符（可自动修复）。

####@规则

-   [`at-rule-empty-line-before`](../../lib/rules/at-rule-empty-line-before/README.md)：要求或禁止在@规则之前的空行（可自动修复）。
-   [`at-rule-name-case`](../../lib/rules/at-rule-name-case/README.md)：指定@规则名的大小写（可自动修复）。
-   [`at-rule-name-newline-after`](../../lib/rules/at-rule-name-newline-after/README.md)：要求在@规则名之后必须有换行符。
-   [`at-rule-name-space-after`](../../lib/rules/at-rule-name-space-after/README.md)：要求在@规则名之后必须有一个空格（可自动修复）。
-   [`at-rule-semicolon-newline-after`](../../lib/rules/at-rule-semicolon-newline-after/README.md)：要求在@规则的分号之后必须有换行符（可自动修复）。
-   [`at-rule-semicolon-space-before`](../../lib/rules/at-rule-semicolon-space-before/README.md)：要求在@规则的分号之前必须有一个空格或不能有空白符。

#### 注释

-   [`comment-empty-line-before`](../../lib/rules/comment-empty-line-before/README.md)：要求或禁止在注释之前的空行（可自动修复）。
-   [`comment-whitespace-inside`](../../lib/rules/comment-whitespace-inside/README.md)：要求或禁止注释标记内侧的空白符（可自动修复）。

#### 一般/表

-   [`indentation`](../../lib/rules/indentation/README.md)：指定缩进（可自动修复）。
-   [`linebreaks`](../../lib/rules/linebreaks/README.md)：指定 unix 或 windows 换行符（可自动修复）。
-   [`max-empty-lines`](../../lib/rules/max-empty-lines/README.md)：限制相邻空行的数量。
-   [`max-line-length`](../../lib/rules/max-line-length/README.md)：限制行的长度。
-   [`no-eol-whitespace`](../../lib/rules/no-eol-whitespace/README.md)：禁止行尾空白符（可自动修复）。
-   [`no-missing-end-of-source-newline`](../../lib/rules/no-missing-end-of-source-newline/README.md)：禁止缺少源码结尾换行符（可自动修复）。
-   [`no-empty-first-line`](../../lib/rules/no-empty-first-line/README.md)：禁止空第一行（可自动修复）。

