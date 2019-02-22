# JavaScript

## 加入位置:

- 标签直接加入 : `<script type="text/javascript"></script>`
- 标签引入外部链接 : `<script type="text/javascript" src="tests.js"></script>`
- 控件添加 `onclick` : ` <input type="text" onclick="alert('单击');"/>`
- 链接href指定 : `<a href="javascript:alert('单击链接');">链接</a>`

## 基本语法

- 用分号来结束语句是可选的。(浏览器自动猜测补全)
- JavaScript 对大小写是敏感的。
- JavaScript 会忽略多余的空格&缩进。
- 可以在文本字符串中使用反斜杠对代码行进行换行。
- 注释:`\\`和`\* *\`。
- 变量:变量是弱类型的
    - 变量必须以字母开头
    - 变量也能以 $ 和 _ 符号开头（不过我们不推荐这么做）
    - 变量名称对大小写敏感（y 和 Y 是不同的变量）
    - 使用 var 关键词来声明变量
    - 重新声明 JavaScript 变量，该变量的值不会丢失
- 数据类型
  - 字符串(String)
  - 数字(Number)
  - 布尔(Boolean)
  - 数组(Array)
  - 对象:对象属性有两种寻址方式
    - `name = person.lastname;`
    - `name = person["lastname"];`
  - Undefined 这个值表示变量不含有值;用 null 来清空变量。
  - 使用关键词 "new" 来声明其类型：
