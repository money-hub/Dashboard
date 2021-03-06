# MoneyDodo代码规范

## 1. 微信小程序代码规范

### 1.1 项目文件规范

**（1）文件及文件夹命名由多个单词组成，采用中划线连接**

**（2）文件及文件夹名称只由小写英文字母、数字、中划线组成，不应包含特殊符号**

**（3）公共组件统一放置在components文件夹中；页面组件统一放置在pages文件夹中**

**（4）同一页面的文件（包括.json，.wxss，.wxml，.js）放置在与pages文件夹下与页面同名的子文件夹中，文件名与页面名一致**

**（5）父组件与子组件间应当以目录结构的方式表现出层级关系，如子组件放置在childrens文件夹中，且childrens文件夹与父组件放置在同一目录下**

### 1.2 JavaScript规范

**（1）使用空格代替tab进行缩进**

使用两个空格代替tab键，对代码进行缩进管理。

**（2）统一省略分号**

每个语句统一省略句尾的分号。

**（3）杜绝var**

使用const或let来声明所有局部变量。如果变量不需要被重新赋值，默认应该使用const。

**（4）使用模板字符串取代连接字符串**

在处理多行字符串时，使用模板字符串代替+号连接字符串

**（5）不要使用eval语句**

**（6）常量的命名规范**

常量命名应该使用全大写格式，并用下划线分割，如：

```
const MAX_LENGTH = 100;
```

**（7）普通变量和函数命名使用Camel-Case，如getUserInfo**

**（8）使用单引号**

只允许使用单引号包裹普通字符串，禁止使用双引号。

### 1.3 wxml规范

**（1）使用空格代替tab进行缩进**

使用两个空格代替tab键，对代码进行缩进管理。

**（2）类名和id统一使用小写字母和中划线分割多个单词**



## 2. 前端代码规范

[Eslint 语法规则](https://cn.eslint.org/docs/rules/)

使用Eslint代码规范检查工具

## 3. 后端代码规范

* [gofmt命令](<https://golang.org/cmd/gofmt/>)

  大部分格式的问题可以通过`gofmt`来解决，`gofmt`自动格式化代码，保证所有的go代码与官方推荐的格式保持一致，所有格式有关问题，都以`gofmt`的结果为准。建议在提交代码库之前先运行以下这个命令。

* 行长

  一行最长不超过80个字符，超过的使用换行展示，尽量保持格式优雅。

* 命名

  * 函数命名规则：驼峰式命名，名字可以长但是得把功能，必要的参数描述清楚，函数名应当是动词或动词短语，如 `postComment`、`deleteComment`。并依` Javabean 标准`加上 get、set、is前缀。例如：`xxx + With + 需要的参数名 + And + 需要的参数名 + …`。
  * 包名命名规则：包名应该为小写单词，不要使用下划线或者混合大小写。
  * 结构体命名规则：结构体名应该是名词或名词短语，如`Comment`、`User`等。
  * 变量命名规则：驼峰式命名，可导出的任何类型必须以大写字母开头。

* import

  对 import 的包进行分组管理，用换行符分割，而且标准库作为分组的第一组。如果你的包引入了三种类型的包，标准库包，程序内部包，第三方包，建议采用如下方式进行组织你的包

  ```go
  import (
      "encoding/json"         //标准包
      "strings"
  
      "myproject/models"      //内部包
      "myproject/utils"
  
      "github.com/go-sql-driver/mysql"    //第三方包
  )
  ```

  引用包时不要使用相对路径。

  ```go
  // 这是不好的导入
  import "../net"
   
  // 这是正确的做法
  import "github.com/repo/proj/src/net"
  ```

* 错误处理

  * 不要在逻辑代码中使用panic
  * error作为函数的值返回，必须对error进行处理
  * 错误描述如果是英文必须为小写，不需要标点结尾
  * 采用独立的错误流进行处理

  不推荐方式：

  ```go
  if err != nil {
    // 错误处理
  } else {
    // 普通代码
  }
  ```

  推荐方式：

  ```go
  if err != nil {
    // 错误处理
    return // 或其余操作
  }
  // 普通代码
  ```

* 参数传递
  * 对于少量数据，不要传递指针
  * 对于大量数据的 `struct` 可以考虑使用指针
  * 传入的参数是 `map`，`slice`，`chan` 不要传递指针，因为` map`，`slice`，`chan` 是引用类型，不需要传递指针的指针

* 单元测试

  * 单元测试文件命名规范：`example_test.go`

  * 测试用例的函数名称必须以`Test`开头，例如：`func TestPostComment`