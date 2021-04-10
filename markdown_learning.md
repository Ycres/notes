### 一、标题

- #个数为标题级数

### 二、段落

#### 1、字体

- 一个*或者_为斜体    *a*
- 两个*或者_为加粗   **a**
- 三个\*或者_为加粗斜体   ***a***

#### 2、分割线

- 一行中用三个以上的星号、减号、底线来建立一个分隔线，行内不能有其他东西 
- 连续三个*或者-

---

#### 3、删除线

- 两个波浪线~
- ~~这段要删除~~

#### 4、下划线

- html中的<u>标签

- <u>aaaaaa</u>

#### 5、脚注

- 中括号[^]中加需要标脚注的文字,后面加冒号：[^script example]

- [^script example]:input description

-  [^script example]  前后都需要加上其他符号，否则无法识别

### 三、列表

- 无序列表星号\* 加号\+ 减号\-  后加空格
- 有序列表用数字加上**\.**
  1. for example
  2. for example
- 嵌套在文字前加四个空格/一个tab

### 四、区块

- 用**\>**后加一个空格

  > example

- 嵌套

  > a
  >
  > > b
  > >
  > > > c

### 五、代码

- 代码段用**\`** 包起

  > `print()`

- 代码段用```包起来，可以选择语言

  ```c
  print('abc');
  
  a = 12;
  ```

### 六、链接

#### 1、普通链接

- \[链接名称\]\(链接地址\) [百度](www.baidu.com)
- \<链接地址\> <www.baidu.com>

#### 2、高级链接

- 可以通过变量来设置一个链接，变量赋值在文档末尾进行

- [google][1]

- [1]:www.google.com

  注意区别 **段落** 中的 **脚注**

  [^baidu]: ww.baidu.com

-   [^baidu]

### 七、图片

- \!\[alt属性文本\]\(图片地址\"可选标题\"\)

- ![pytorch图片](F:\pytorch\pytorch.jpg"pytorch")

- [变量图片\]\[变量\]

- [pytorch][1]

- [1]:http://static.runoob.com/images/runoob-logo.png



### 八、表格

- Markdown 制作表格使用 **|** 来分隔不同的单元格，使用 **-** 来分隔表头和其他行。

  | 表头1 | 表头2 |
  | ----- | ----- |
  |       |       |



- > ```
  > |  表头   | 表头  |
  > |  ----  | ----  |
  > | 单元格  | 单元格 |
  > | 单元格  | 单元格 |
  > ```

- | 表头   | 表头   |
  | ------ | ------ |
  | 单元格 | 单元格 |
  | 单元格 | 单元格 |

### 九、高级技巧

#### 1、HTML

- 不在 Markdown 涵盖范围之内的标签，都可以直接在文档里面用 HTML 撰写。
- 目前支持的 HTML 元素有：`<kbd> <b> <i> <em> <sup> <sub> <br>`等
- kbd:<kbd>abc</kbd>    sup:<sup>def</sup> 

#### 2、转义

- 转义字符前加上\

#### 3、公式

- 当你需要在编辑器中插入数学公式时，可以使用两个美元符 $$ 包裹 TeX 或 LaTeX 格式的数学公式来实现。提交后，问答和文章页会根据需要加载 Mathjax 对数学公式进行渲染。

- ```
  $$
  \mathbf{V}_1 \times \mathbf{V}_2 =  \begin{vmatrix} 
  \mathbf{i} & \mathbf{j} & \mathbf{k} \\
  \frac{\partial X}{\partial u} &  \frac{\partial Y}{\partial u} & 0 \\
  \frac{\partial X}{\partial v} &  \frac{\partial Y}{\partial v} & 0 \\
  \end{vmatrix}
  ${$tep1}{\style{visibility:hidden}{(x+1)(x+1)}}
  $$
  ```

- $$
  \mathbf{V}_1 \times \mathbf{V}_2 =  \begin{vmatrix} 
  \mathbf{i} & \mathbf{j} & \mathbf{k} \\
  \frac{\partial X}{\partial u} &  \frac{\partial Y}{\partial u} & 0 \\
  \frac{\partial X}{\partial v} &  \frac{\partial Y}{\partial v} & 0 \\
  \end{vmatrix}
  ${$tep1}{\style{visibility:hidden}{(x+1)(x+1)}}
  $$

#### 4、UML

- ```
  ​```mermaid
  graph LR
  A[方形] -->B(圆角)
      B --> C{条件a}
      C -->|a=1| D[结果1]
      C -->|a=2| E[结果2]
      F[横向流程图]
  ​```
  ```

- ```mermaid
  graph LR
  A[方形] -->B(圆角)
      B --> C{条件a}
      C -->|a=1| D[结果1]
      C -->|a=2| E[结果2]
      F[横向流程图]
  ```

- ```
  ​```mermaid
  graph TD
  A[方形] --> B(圆角)
      B --> C{条件a}
      C --> |a=1| D[结果1]
      C --> |a=2| E[结果2]
      F[竖向流程图]
  ​```
  ```

- ```mermaid
  graph TD
  A[方形] --> B(圆角)
      B --> C{条件a}
      C --> |a=1| D[结果1]
      C --> |a=2| E[结果2]
      C --> |a=3| G{条件a}
      F[竖向流程图]
  ```

- ```flow
  st=>start: 开始框
  op=>operation: 处理框
  cond=>condition: 判断框(是或否?)
  sub1=>subroutine: 子流程
  io=>inputoutput: 输入输出框
  e=>end: 结束框
  st(right)->op(right)->cond
  cond(yes)->io(bottom)->e
  cond(no)->sub1(right)->op
  ```