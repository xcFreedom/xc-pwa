# Markdown 标准语法演示

这是一份 Markdown 标准语法的演示文档，包含常见的格式和元素。

## 1. 标题 (Headers)

# 一级标题
## 二级标题
### 三级标题
#### 四级标题
##### 五级标题
###### 六级标题

## 测试
safasdf
asdf
as


df
asfasdf


sadfasf


| Before | After
| - | - |
|1|3|

## 2. 文本强调 (Emphasis)

**粗体文本** (Bold)
*斜体文本* (Italic)
***粗斜体文本*** (Bold and Italic)
~~删除线文本~~ (Strikethrough)
<u>下划线文本</u> (Underline, HTML tag)

## 3. 列表 (Lists)

### 无序列表 (Unordered List)
* 项目 1
* 项目 2
  * 子项目 2.1
  * 子项目 2.2
    * 子子项目 2.2.1

### 有序列表 (Ordered List)
1. 第一项
2. 第二项
3. 第三项
   1. 子项目 3.1
   2. 子项目 3.2

### 任务列表 (Task List)
- [x] 已完成的任务
- [ ] 待完成的任务
- [ ] 另一个待完成的任务

## 4. 链接与图片 (Links & Images)

[百度一下，你就知道](https://www.baidu.com)
[Google 搜索](https://www.google.com)

以下是一张图片示例（使用给定的链接）：
![image/png](https://www.baidu.com/img/flexible/logo/pc/peak-result.png)

## 5. 引用 (Blockquotes)

> 这是一个块引用。
> 可以包含多行。
>> 也可以嵌套引用。
>>> 第三层嵌套引用。

## 6. 代码 (Code)

### 行内代码
在句子中使用 `console.log('Hello World!');` 行内代码。

### 代码块 (Code Blocks)
```javascript
// 这是一个 JavaScript 代码块
function greet(name) {
  console.log(`Hello, ${name}!`);
}
greet('Markdown');
```

```python
# 这是一个 Python 代码块
def hello_world():
    print("Hello World")
```

## 7. 表格 (Tables)

| 表头 1 | 表头 2 | 表头 3 |
| :--- | :---: | ---: |
| 左对齐 | 居中对齐 | 右对齐 |
| 内容 1 | 内容 2 | 内容 3 |
| 更多内容 | 更多内容 | 更多内容 |

## 8. 分隔线 (Horizontal Rules)

下面是一条分隔线：

---

这是另一条分隔线：

***

## 9. HTML 元素

如果 Markdown 语法不够用，还可以直接使用 HTML 标签：
<div style="text-align: center;">
  <p>这是一段居中的文字。</p>
</div>

## 10. 转义字符 (Escaping)

如果你想显示原始符号而不是格式，请使用反斜杠：
\* 这不是一个列表项
\# 这不是一个标题
\[这也不是一个链接\](http://example.com)
