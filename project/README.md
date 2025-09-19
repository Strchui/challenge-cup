# 基于 B/S 架构的管理信息系统

# 一、摘	要

在信息技术不断推陈出新的背景下, 针对传统人工管理学生信息方式效率低, 提出一种基于前后端分离设计的学生信息管理系统。

本设计前端部分采用基于 Bootstrap 框架设计，采用 Jquery 进行前后端数据的交互和传递，后端功能逻辑的实现采用 Python 的 Flask 框架实现，数据库采用较为轻量的 sqlite3。

本系统设计主要为对学生信息管理的增删改查，同时实现了数据合法性验证功能，操作结果提示功能，批量删除功能，数据显示分页，为登录页面添加验证码验证等相关功能，且进行了响应性设计，支持在不同设备下使用，本程序设计是在 B/S 架构下的较为简单的学生信息管理系统。

## 1.1 关 键 词: 学生信息管理系统，flask，前后端分离，B/S 架构

# 二、ABSTRACT

In the context of the continuous innovation of information technology, in view of the low efficiency of traditional manual management of student information, a student information management system based on the design of front-end and back-end separation is proposed.

The front-end part of this design is designed based on Bootstrap framework, and Jquery is used for the interaction and transmission of front-end and back-end data, the realization of back-end functional logic is realized by Python’s Flask framework, and the database uses sqlite3,which is a relatively lightweight database.

The system design is mainly for the addition, deletion, modification, and checking of student information management. At the same time, it realizes the data legality verification function, the operation result prompt function, the batch deletion function, the data display paging, and the verification code verification for the login page and other related functions.Responsive design is carried out to support the use of different devices. This program design is a relatively simple student information management system under the B/S architecture.
Key words: student information management system,flask,front-end and back-end separation,the B/S architecture

## 2.1 实验目的

理解并掌握动态网页制作相关概念和技术，综合利用所学的 Web 技术，掌握基于 Flask 开发 B/S 架构系统的方法，做到知其然、知其所以然。


## 2.2 实验系统分析

对于常见的学生信息系统而言，我们需要存储学生的许多相关信息，包括学生的学号、姓名、年龄、性别、籍贯、专业，这些数据要求能够按照一定的规则进行操作，同时也要对使用该系统的用户友好，便于其使用。

对于学生信息管理系统，可能需要进行的常见操作有如下几种：

- 从数据库获取学生信息并展示

- 在程序中增加学生学生信息

- 删除单个或多个学生信息

- 修改已存储的某个学生的信息

- 根据条件查找学生的信息

因此，我们需要设计相关的功能，而这些功能的实现均需根据大作业的相关要求，于是我们实现在以上基础功能的前提下，在此基础上根据功能改进和优化系统，具体优化如下：

- 增加数据合法性验证功能，包括客户端验证和服务端验证

- 实现操作结果显示功能，比如添加数据时提示添加成功/添加失败、删除时提示删除成功等

- 实现批量删除功能

- 实现数据显示分页功能

- 为登录页面添加验证码功能

- 适当页面美化工作

## 2.3 实验系统设计环境

### 2.3.1 系统环境配置

本系统设计采用的以及所需的相关环境如下：

表 3.1: 系统环境配置

| 名称 |具体信息 |
|----|----|
| PyCharm |2021.2.3 (Professional Edition) |
| Python |版本：3.8.2 |
| Flask |2.0.2 |
| Flask_Sessionstore |0.4.5 |
| Flask_SQLAlchemy |2.5.1 |
| flask_session_captcha |1.2.0 |
| Jquery |3.6.0 |
| Bootstrap |3.4.1 |
| toastr |2.1.4 |


### 2.3.2 系统设计简介

采用了完全前后端分离的开发模式，templates 文件夹存放页面模板，app.py 为服务器端的逻辑处理，show.js 负责在页面与服务器端之间充当代理。除登陆页面外，系统页面与后端逻辑不进行直接交互。

实验结果总览

以下是我们系统界面的一个简单的展示。

### 2.3.3 登录界面

用户在此页面进行用户名、密码、验证码的填写，验证成功方可登陆系统。（图4.1）

![](https://www.writebug.com/myres/static/uploads/2022/9/13/91d6b85c8f18983c2925fade90fa00cc.writebug)

图 4.1: 登录界面

### 2.3.4 系统界面

登陆系统后，用户在本页面内进行学生信息管理，可以进行信息查找、新增、修改、删除、刷新操作，页面支持分页显示、批量删除、精确/模糊查找。（图4.2）

### 2.3.5 新增学生界面

用户点击新增按钮后，在此页面内填写学生信息，点击保存后新增学生并更新页面。（图4.3）

山东大学（威海）大作业报告

![](https://www.writebug.com/myres/static/uploads/2022/9/13/a4e9720a4d2f3a76a3d7bb3475037e33.writebug)

图 4.2: 系统界面

![](https://www.writebug.com/myres/static/uploads/2022/9/13/6e7108b0b5eb4ca9c843a357ed70afb0.writebug)

图 4.3: 新增学生信息

### 2.3.6 修改信息界面

用户选择一个学生，点击修改按钮后，在此页面内修改学生信息，点击保存后保存修改并更新页面。（图4.4）

![](https://www.writebug.com/myres/static/uploads/2022/9/13/eceee85b711d1e975aaeffaf2cb49dc9.writebug)

图 4.4: 修改学生信息

### 2.3.7 删除学生界面

用户选择一个或多个学生，点击删除按钮后，弹出确认删除提示框，点击删除后删除学生并更新页面（也可以通过全选批量删除）。（图4.5）

![](https://www.writebug.com/myres/static/uploads/2022/9/13/7a72e75890a8feda3d8020b85ec38ae0.writebug)

图 4.5: 删除学生信息

## 2.4 功能点展示及代码分析

### 2.4.1 悬浮表单（模态框）

此页面悬浮于原页面之上，采用 Bootstrap+JavaScript 插件框架中的模态框

Modal 实现。（图5.1）

![](https://www.writebug.com/myres/static/uploads/2022/9/13/b51dc159c5891bb53fcebfd36201f625.writebug)

图 5.1: 悬浮表单展示

我们在使用 Bootstrap 框架时，首先在项目中导入源文件：（图5.2）

![](https://www.writebug.com/myres/static/uploads/2022/9/13/1bbd8fa6b1e2d11f8036abb1564c6ed2.writebug)

图 5.2: 导入源文件内容

模态框前端 HTML 页面代码（图5.3）（截取了部分）：对于（图5.3）红框之中的参数进行一些说明：

![](https://www.writebug.com/myres/static/uploads/2022/9/13/5839a626e8c695afee35cc179d2aeefc.writebug)

图 5.3: 前端页面代码

![](https://www.writebug.com/myres/static/uploads/2022/9/13/66e12a99d28fc9ad1de0cce2b2ddfe3f.writebug)

图 5.4: js 代码控制模态框

```c++
class 中的.modal，用来把 <div> 的内容识别为模态框
```

class 中的.fade当模态框被切换时，它会引起内容淡入淡出

class=”modal-header” modal-header是为模态窗口的头部定义样式的类

class=”close”，用于为模态窗口的关闭按钮设置样式

data-dismiss=”modal”，是一个自定义的 HTML5 data 属性。在这里它被用于关闭模态窗口

aria-hidden=”true” 用于保持模态窗口不可见，直到触发器被触发为止（比如点击在相关的按钮上）

class=”modal-body”，modal-body 是 Bootstrap CSS 的一个 CSS class，用于为模态窗口的主体设置样式。

随后在 show.js当中，通过（图5.4）所示代码控制模态框, 在代码中首先为模态框设置了标题，随后显示模态框。至此，模态框实现完毕。

### 2.4.2 数据完整性验证

以新增学生信息时的情况为例（图5.5）：

![](https://www.writebug.com/myres/static/uploads/2022/9/13/8888b7e0be8eafab275245a0bdba10ad.writebug)

图 5.5: 新增学生信息完整性验证

此模态框用于新增学生信息，在当前页面，每次鼠标焦点离开输入框都会触发数据合法性验证，此处的合法性验证函数在 show.js 内编写，属于前端完整性验证。其对应代码如下图5.6（由于相关的代码包括增加模块，修改模块和搜索模块，代码较长但功能实现类似，此处以增加学生信息时的学号验证为代表进行展示，红框内为其代码）:

验证逻辑较为简单，从前端获取数据后按照定义的正则表达式进行合法性验证，根据验证结果更新前端输入框显示样式和提示信息。

假如前端验证成功，会出现下图5.7的情况，正确的部分均用绿色的提示框进行包装来提示用户符合要求：

![](https://www.writebug.com/myres/static/uploads/2022/9/13/c51e6ae3e7c028be56ad03cd94637612.writebug)

图 5.6: 前端完整性验证

![](https://www.writebug.com/myres/static/uploads/2022/9/13/2bfcb0508b9cb9b598589cb47db10f4a.writebug)

图 5.7: 前端完整性验证成功

此时点击提交，会由函数将表单信息封装传入服务器端，代码实现如下图5.8

![](https://www.writebug.com/myres/static/uploads/2022/9/13/15b3abd4070ad2a2636ef2fac1bfa329.writebug)

图 5.8: 前端数据封装传递后端

函数里采用了 AJAX 技术与服务端进行交互，此处是将前端验证完成的数据封装成 Json 后执行 AJAX 请求，将数据传递给服务器端。随后进入服务端数据合法性验证，代码如下图5.9：

![](https://www.writebug.com/myres/static/uploads/2022/9/13/ca42d82d65245b220b2f30199fa3a3b8.writebug)

图 5.9: 服务端数据合法性验证红色框内为服务端合法性验证，服务器端获取数据后，利用正则表达式再次验证数据合法性，只有这一步验证完全正确之后，数据才会被真正写入数据库，同时更新前端页面、显示提示信息。

这就实现了数据合法性在客户端和服务器端的双重验证，防止了错误信息的提交和 url 里参数的恶意修改。合法性验证在这次的大作业中在用户名/密码验证、增加学生信息验证、修改信息验证、查找关键字验证中都有应用，实现逻辑相似，此处不再一一赘述。

### 2.4.3 操作结果提示

以修改学生信息为例，选择一位学生，点击修改按钮，弹出修改页面

(图5.10), 此时系统已经从后台获取到待修改的学生的原始信息。

![](https://www.writebug.com/myres/static/uploads/2022/9/13/17270ddce957eef81e14aeec58ae2982.writebug)

图 5.10: 修改页面弹出

我们将其年龄改为 -1，使修改后的数据不符合合法性要求，结果如下图5.11：

![](https://www.writebug.com/myres/static/uploads/2022/9/13/fc9d2f82184f2796c4f7288dd50188cd.writebug)

图 5.11: 不符合合法性要求结果

如箭头所指，右上角出现红色提示框，框内信息为“修改的数据不符合数据规则！！！”，同时我们可以发现，红框内的学生信息中的年龄字段也并没有被修改。也就是说，这次的修改是非法的，数据没有任何改动。

我们再次进行修改，将其年龄从 20 岁改为 18 岁，点击提交，结果如下图5.12:

![](https://www.writebug.com/myres/static/uploads/2022/9/13/ee4cad7f62ebf871e81303366bd69127.writebug)

图 5.12: 正确提交结果提示

如箭头所指，右上角出现绿色提示框，框内信息为“修改数据成功”，同时我们可以发现，红框内的学生信息中的年龄字段也以及由 20 改为了 18。也就是说，这次的修改是合法的，数据也进行了改动。

上述功能，是利用 jquery 的通知插件 toastr 实现的。大作业中首先导入了 toastr 插件的开源代码 (图5.13)：

![](https://www.writebug.com/myres/static/uploads/2022/9/13/b7a0ca90bd6695c11965003d21af7de6.writebug)

##### 2.4.3 图 5.13: toastr 插件代码组成

随后在 show.html页面中的代码如下，同时指定提示框显示在右上角

(图5.14)：

![](https://www.writebug.com/myres/static/uploads/2022/9/13/938d79086ec7c0bc16c6e5e7859cd6e2.writebug)

##### 2.4.3 图 5.14: toastr 插件引入

触发提示框的逻辑在 show.js 当中，代码如下5.15：

![](https://www.writebug.com/myres/static/uploads/2022/9/13/639455fe2bb176f769d23e24acbac609.writebug)

图 5.15: 触发提示框逻辑红框内表示显示提示框，提示框具体的样式和内容根据逻辑决定。此处的逻辑是执行 AJAX 请求，将客户端数据传入服务器，如果成功，就显示绿色的成功提示信息，如果请求错误或失败，就显示红色的错误提示信息。

这就是操作结果提示的具体实现方法，在大作业中进行新增学生信息、修改学生信息、删除学生信息操作之后，都会显示对应的提示框，实现逻辑相类似，此处不再一一赘述。

### 2.4.4 显示分页

在系统中，数据的显示支持分页，见图5.16。

![](https://www.writebug.com/myres/static/uploads/2022/9/13/bac2d8444741af841b260a1ebae6f635.writebug)

图 5.16: 支持分页显示

紫色框内为页面导航和显示设置，红框内为显示的学生信息，信息条目数依据紫框的设置而定，图中设置了每页显示 5 条数据，同样也可以设置每页 10 或 20 条数据 (见图5.17)，当页面在第一页时，“上一页”按钮不会出现 (见图5.16)。点击“下一页”按钮跳转到了下一页, 当页面在最后一页时，“下一页” 按钮不会出现。(见图5.18)

![](https://www.writebug.com/myres/static/uploads/2022/9/13/7563adceeeb74e09a2d4523599d36032.writebug)

图 5.17: 每页展示 10 条

图 5.18: 处于最后一页时数据显示分页的功能的实现逻辑如下：

首先在 show.js 中定义函数 getStudentInfo，函数获取页面的设置和输入（查询关键字、页面显示数据数、导航状态等）：

![](https://www.writebug.com/myres/static/uploads/2022/9/13/9e5ccbf40193b85e3b252a1061ab0f98.writebug)

图 5.19: 获取页面基本信息

随后通过 AJax get 请求方法以路由/showinfo从后端请求学生信息和有关分页内容的信息：

![](https://www.writebug.com/myres/static/uploads/2022/9/13/3de20cb4f6bd81a2efd3aee3ba1d0e78.writebug)

##### 2.4.4 图 5.20: AJax get 请求方法

在服务器端脚本 App.py 中定义了对这一请求的处理函数 showinfo，函数中使用了 flask_sqlalchemy。在接收到请求时，函数通过 SQLAlchemy 对象根据请求参数（查询关键字、页面显示数据数、导航状态等）查询数据库，得到分页类 Pagination 的对象。将此对象分解为分页信息和学生信息，一并返回, 代码如下：

```web-idl
# 获取学生信息
@app.route('/showinfo', methods=['GET']) def showinfo():
if not CheckLogin(): # 检查是否登录
    return redirect(url_for('login'))
    
page = int(request.args.get('page', 1)) # 当前页面编号 per_page = 

int(request.args.get('per_page', 5)) # 当前页面显示几条信息

name = str(request.args.get('name', "")) # 用户查询所用的姓名 stuno = 

str(request.args.get('stuno', "")) # 用户查询所用的学号
#通过 SQLAlchemy 对象根据请求参数（查询关键字、页面显示数据数、导航状态等）查询数据库
#返回分页类 Pagination 对象
if name == "" and stuno == "": # 没有查询关键字
    paginate = db.session.query(student_info).join(stu_profession). \
filter(student_info.stu_profession_id == stu_profession.stu_profession_id)
. \
order_by(student_info.stu_id).paginate(page, per_page, error_out=False)
elif name != "" and stuno == "":
paginate = db.session.query(student_info).join(stu_profession). \ filter(student_info.stu_profession_id == stu_profession.stu_profession_id)
. \
filter(student_info.stu_name.like('%%%s%%' % name)). \ order_by(student_info.stu_id).paginate(page, per_page, error_out=False)
elif name == "" and stuno != "":
paginate = db.session.query(student_info).join(stu_profession). \ filter(student_info.stu_profession_id == stu_profession.stu_profession_id)
. \
    filter(student_info.stu_id.like('%%%s%%' % stuno)). \ 
    order_by(student_info.stu_id).paginate(page, per_page, error_out=False)
else:
    paginate = db.session.query(student_info).join(stu_profession). \ 
    filter(student_info.stu_profession_id == stu_profession.stu_profession_id)
    . \
    filter(student_info.stu_name.like('%%%s%%' % name)). \ filter(student_info.stu_id.like('%%%s%%' % stuno)). \ order_by(student_info.stu_id).paginate(page, per_page, error_out=False)
stus = paginate.items # 获取分页得到的学生信息 ret = [] # 存储格式化后的学生信息结果 for stu in stus: # 对获取到的所有学生信息遍历，以对单个学生信息类进行处理 ret.append(student_to_dict(stu)) # 将处理后的结果存储到返回信息中
ret_paginate = {'has_prev': ('yes' if paginate.has_prev else 'no'), ' prev_num': paginate.prev_num,
    'pages': paginate.pages, 'next_num': paginate.next_num, 'total': paginate. total,
    'per_page': per_page, 'page': paginate.page}
# 返回学生信息和有关分页信息
return jsonify({'stuinfo': json.dumps(ret, ensure_ascii=False), 'paginate':
             ret_paginate})

```



show.js 的函数 getStudentInfo 接收到了服务端返回的分页信息和学生信息后，动态生成页面信息，同时更新导航栏信息，最终实现分页页面的显示

u每次页面刷新、翻页、查询都会执行上述过程，实现页面的动态更新。

至此显示分页功能实现完毕。

![](https://www.writebug.com/myres/static/uploads/2022/9/13/7be3767ee6c8eb9b732778f961396812.writebug)

图 5.21: 动态生成页面从代码中可以看到，服务端在获取页面时借助了 flask_sqlalchemy 来辅助实现，此处进行补充说明。在使用 flask_sqlalchemy 之前需要进行配置，指定连接的数据库：

![](https://www.writebug.com/myres/static/uploads/2022/9/13/e3c8c79a2af2e27289013f197d00a175.writebug)

图 5.22: 指定连接的数据

随后创建 SQLAlchemy 对象：

![](https://www.writebug.com/myres/static/uploads/2022/9/13/9bfca2d5b3c4e6933f5a147cc62aa52b.writebug)

##### 2.4.4 图 5.23: 创建 SQLAlchemy 对象

创建对象后，为了实现数据库操作，需要建表。本实验中需要建立两个表：

学生专业表（专业号，专业名）

学生信息表（学号、姓名、性别、年龄、籍贯、专业号）随后在 sqlalchemy 中通过定义类的形式映射上述两个表：

![](https://www.writebug.com/myres/static/uploads/2022/9/13/5d59620c38bbd7239a4379e40e250dde.writebug)

图 5.24: 通过定义类的形式映射上述两个表

在这几步完成之后，showInfo 函数才能使用 SQLAlchemy 对象进行数据库操作并返回分页类对象。

### 2.4.5 批量删除

若要删除学生信息，在单选删除模式下，首先单选一个或多个学生：

![](https://www.writebug.com/myres/static/uploads/2022/9/13/58d3f24debb904816112e73d1ecff9d0.writebug)

![](https://www.writebug.com/myres/static/uploads/2022/9/13/6956a862987ef87dca893902bfd73218.writebug)

图 5.25: 选择删除学生

点击删除按钮后，弹出删除确认页面：

![](https://www.writebug.com/myres/static/uploads/2022/9/13/92ff74758c07c30f7abc0422aff87a8c.writebug)

![](https://www.writebug.com/myres/static/uploads/2022/9/13/ebd89535e3b5b179347d06d347f7148c.writebug)

图 5.26: 删除确认页面

点击删除，弹出提示信息，提示信息为删除学号为“xx”的数据成功，xx 为被选学生的学号, 见图5.27：

![](https://www.writebug.com/myres/static/uploads/2022/9/13/4c5ceefdb5fefa4647e3d3eff6b0aaee.writebug)

图 5.27: 删除成功提示

在批量删除模式下，首先点击全选按钮，全选当前页面的所有学生信息，点击删除按钮删除当前页面所有学生, 见图5.28：

![](https://www.writebug.com/myres/static/uploads/2022/9/13/7bf2ade6712f09983bec6f3c6a7439cf.writebug)

图 5.28: 批量删除操作

弹出删除确认页面, 见图5.29：

点击删除, 右上角弹出删除结果提示框，提示删除了三个学生, 见图5.30：

![](https://www.writebug.com/myres/static/uploads/2022/9/13/aa71a836877f0f54a3303023921ff856.writebug)

图 5.29: 批量删除确认页面

![](https://www.writebug.com/myres/static/uploads/2022/9/13/c6a0ad4265e98ca20dbe0ce149584e2a.writebug)

图 5.30: 批量删除成功提示批量删除的实现逻辑如下：当用户点击多选框时，会触发 show.js 里定义的监听事件 checkAllClick（() 该函数会将当前页面的所有学生信息设为选中状态，同时对每个选中行的样式更改，行背景被改为浅黄色。

![](https://www.writebug.com/myres/static/uploads/2022/9/13/0e69fafcaf4b3bedc3030f94e379d974.writebug)

##### 2.4.5 图 5.31: checkAllClick 事件

随后点击删除按钮时，会触发 show.js 中定义的删除按钮触发事件：

![](https://www.writebug.com/myres/static/uploads/2022/9/13/964fa7c5a5a691fc4fa3d9724592fc83.writebug)

图 5.32: 删除按钮触发事件

如红框内所示，该函数将调出删除确认页面（模态框），并且根据勾选学生的学号生成学号串，加入删除确认信息当中。这一步用于提示用户是否确认删除，随后等待用户下一步指令。如果用户在删除确认页面里点击了“删除”，会触发 show.js 中定义的删除按钮触发事件 delSub 来执行删除学生信息的操作：

![](https://www.writebug.com/myres/static/uploads/2022/9/13/4785892d7bf7e0ff53f96bd410f0e2f5.writebug)

##### 2.4.5 图 5.33: 触发事件 delSub

delSub 函数首先获取所有被选中的学生的学号，存入数组当中。红框中代码对获取到的每个学生学号信息依次进行删除, 采用 get 请求，请求路由为/del/待修改的学生 id。

在服务端脚本 app.py 内定义了处理该请求的函数：

```python
# 删除学生信息，根据单个直接删除id
@app.route('/del/<id>', methods=['GET']) def delete(id):
if not CheckLogin(): return redirect(url_for('login'))
DelDataById("stu_id", id, "student_info") # 如果能正常执行则能正常删除，否则直
```

接报错。

```c++
res = {'code': 200, 'message': '成功添加！'} return res
```

函数根据路由传来的参数，也就是学生的学号，从数据库中删除该学生并返回响应。show.js 中的 delsub 中的 get 请求收到响应后，根据响应的状态，显示删除操作结果的提示。

这就是批量删除的实现方法。

### 2.4.6 登录验证码

当用户进入系统之前，首先需要登陆系统，此时，用户除了需要输入账号密码外，还需要输入验证码：

![](https://www.writebug.com/myres/static/uploads/2022/9/13/34e7561e0525a31689e86ddc64f7fe88.writebug)

图 5.34: 登录验证码界面

只有用户输入正确验证码时，方可登录系统。以下是登陆表单的页面代码：

![](https://www.writebug.com/myres/static/uploads/2022/9/13/a09191427d3db5d26db1beff2764398d.writebug)

- 图 5.35: 登陆表单的页面代码

- 用户名和密码框均使用 input，验证码的实现使用了 flask-session-captcha 包实现。其中这一行代码是验证码所在区域 (图5.36)。

- 服务端在使用 flask-session-captcha 时，首先得定义一些参数，比如使能验证码、定义验证码图片的宽高等等 (见图5.37)。

![](https://www.writebug.com/myres/static/uploads/2022/9/13/78290562fec0fe4c7645f8b2ad0ed971.writebug)

图 5.36: 验证码所在区域

![](https://www.writebug.com/myres/static/uploads/2022/9/13/32a742e18d4d2f005cced53bf1735726.writebug)

##### 2.4.6 图 5.37: flask-session-captcha 配置

当用户输完用户名密码和验证码，按下登录按钮时，以/login 为路由进行 post 请求，服务器端的路由定义如下：

```c++
@app.route('/login', methods=['POST', 'GET']) def login():
if request.method == "GET": # 初始情况下直接加载模板 ret = {'username': '', 'pwd': '', 'hidden': 'none'}
return render_template('login.html', ret=ret)
# 如果是请求，说明用户尝试登录post
# 从数据库获取查询结果
result, _ = GetSql2("select * from users where username='%s'" % request. form['username'])
print(result)
# 用户名、密码、验证码全部验证成功，方可登录，否则登陆失败
if len(result) > 0 and result[0][1] == request.form['pwd'] and captcha.
validate(): # 登陆成
```

功

```python
session["username"] = request.form['username'] # 使用保存用户名session return redirect(url_for('index')) # 重定向到路由"/" else: # 登陆成功用户名和密码不清除,
ret = {'username': request.form['username'], 'pwd': request.form['pwd'],
'hidden': 'block'}
return render_template('login.html', ret=ret)
```

在此路由中，服务端首先根据用户输入的账号在数据库中进行查找，随后将查找的密码与用户输入的密码进行对比，同时，函数 captcha.validate() 将根据含有验证码的表单的输入进行验证。只有密码和验证码验证成功之后方可登录。

此部分便是登录验证码的实现。

## 2.5 系统安全性及异常处理

### 2.5.1 更改 URL 绕过登录

在登陆页面修改 url , 原 url 地址为 127.0.0.1:5000/login, 之后将 login 改成 add 即更改为 127.0.0.1:5000/add, 尝试直接跳过登录进入增加学生信息页面，结果仍然会跳转到 login。

![](https://www.writebug.com/myres/static/uploads/2022/9/13/64d78a1f7ccc08a11c715cb5aee50a8e.writebug)

图 6.1: 更改 URL 绕过登录

可以看到，结果返回了登录页面，URL 也变为了原来的 URL。而这种安全机制的实现，是通过给每个路由的函数当中增加登录验证：

```python
@app.route('/showinfo', methods=['GET']) def showinfo():
if not CheckLogin(): # 在这里检查是否登录 return redirect(url_for('login'))
```

而登陆验证通过 CheckLogin 函数实现，其代码如下：

| # 检查是否登录；def CheckLogin():；if 'username' not in session:；return False |
|----|
| else:；return True |


CheckLogin 函数通过会话机制，检查当前会话当中是否存储了用户名来检查用户是否登录。原因是如果用户成功登录，便会在会话中存储用户的用户名，如下代码 (在函数 login中)：

```python
if len(result) > 0 and result[0][1] == request.form['pwd'] and captcha. validate():
# 登陆成功
session["username"] = request.form['username'] # 使用保存用户名session return redirect(url_for('index')) # 重定向到路由"/" else: # 登陆成功用户名和密码不清除,
```

### 2.5.2 登陆页面输入不合法

包括信息缺省 (图6.2) 和用户名、密码或验证码输入错误 (图6.3)。

![](https://www.writebug.com/myres/static/uploads/2022/9/13/5945a8775b2f6675a761611ab431744b.writebug)

图 6.2: 信息缺省

![](https://www.writebug.com/myres/static/uploads/2022/9/13/0ab6db9a51028ea0456f8a6f9c70c45e.writebug)

图 6.3: 用户名、密码或验证码输入错误

### 2.5.3 输入数据不合法

- 包含客户端合法性验证失败和服务端合法性验证失败两部分。

- 客户端合法性验证失败

- 对于搜索：搜索关键字不合法时，输入框变成红色，无查询结果。如图6.4 对于新增或修改学生界面：输入数据不合法时，会出现提示信息，输入框变成红色。如图6.5

- 服务端合法性验证失败

当客户端数据合法性验证通过时，可以进行保存操作 (如图6.6)，但点击提交，由于新增学生的学号与数据库中学生的学号有重复，因此出现结果 (如图6.7), 右上角会出现操作提示，提醒数据提交失败，数据库也没有更新。

![](https://www.writebug.com/myres/static/uploads/2022/9/13/ca122a3c67bcf259f114e186db51a615.writebug)

图 6.4: 搜索关键字不合法

![](https://www.writebug.com/myres/static/uploads/2022/9/13/517298a66c9ccf0a9816dee08cad88b7.writebug)

图 6.5: 输入数据不合法

![](https://www.writebug.com/myres/static/uploads/2022/9/13/250187577cf674b58201a3962423c08d.writebug)

![](https://www.writebug.com/myres/static/uploads/2022/9/13/f915119c9a6ac3fea7ad8b1483956223.writebug)

图 6.6: 客户端数据合法性验证通过

![](https://www.writebug.com/myres/static/uploads/2022/9/13/1327c5bdc6c557607b2f6acdc6ee4c02.writebug)

图 6.7: 服务端合法性验证失败

### 2.5.4 修改、删除信息时违规操作

包含修改信息时违规操作和删除信息时违规操作两部分。

修改信息时违规操作

当未选择目标就点击修改按钮时，右上角会出现操作提示，提醒用户选择一个学生的信息进行修改：

![](https://www.writebug.com/myres/static/uploads/2022/9/13/de7a011ee82b8e9769a9f22045a7c0c4.writebug)

图 6.8: 未选择目标时点击修改

选择了多个目标进行修改时，右上角会出现操作提示，提醒用户只能选择一个学生的信息进行修改：

![](https://www.writebug.com/myres/static/uploads/2022/9/13/dad48defd5cf4967b23810b585c98504.writebug)

图 6.9: 多个目标时点击修改

删除信息时违规操作

未选择目标就点击删除按钮时，右上角会出现操作提示，提醒用户选择需要删除的学生信息：

![](https://www.writebug.com/myres/static/uploads/2022/9/13/ff74822921749a86dc1b8c0bee3c2580.writebug)

图 6.10: 未选择目标时点击删除

# 三、总结与不足

在此次 web 技术大作业中，我们小组采用了前后端分离的开发模式，使用 html、css、javascript、python 等语言和 Flask、Bootstrap、jQuery 等框架，开发了一个学生信息管理系统，实现了学生信息的管理，完成了数据完整性验证、操作结果提示、显示分页、批量删除、登陆验证码等诸多功能，并且通过会话、提示等方式增强系统的安全性和稳定性。

不过在系统安全性方面存在一定的不足，如没有对用户信息进行加密存储。在系统架构设计上较为简单，系统的并发能力较弱。

在系统开发过程中，我们学习到了新的 web 开发知识，了解并使用了新的开发模式，成员之间互相交流进步，受益匪浅。


# 四、项目分工情况

根据大作业的相关要求，项目的分工合作情况如下表8.1所示：

表 8.1: 项目分工合作情况表

成员学号 成员姓名 成员所在班级 完成功能说明 工作量占比 是否组长

# 五、参考文献

娄革伟, 刘旭亮, 马济乔, 董淑萍, 曹文婷. 基于前后端分离的航天试验设备检测管理系统的设计与实现 [J]. 软件工程,2021,24(12):59-+58.DOI:10.19644/j.cnki.issn2096-1472.2021.012.013.

许勇. 基于前后端分离架构的高校教职工廉洁档案管理系统的设计与实现  华中师范大学,2021.

吴昌政. 基于前后端分离技术的 web 开发框架设计 [D]. 南京邮电大学,2020.DOI:10.27251/d.cnki.gnjdc.2020.000727.

廖祥. 基于前后端分离架构的用户权限控制系统设计与实现 [J]. 软件工程,2020,23(12):24-26.DOI:10.19644/j.cnki.issn2096-1472.2020.12.007.

孙思杰.Web 项目基于前后端分离模式的设计与应用 [J]. 科技创新与应用,2020(27):96-97.

