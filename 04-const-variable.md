# golang 中的变量和常量

上节，我们介绍了 golang 的数据类型，接下来，我们将学习 golang 的变量与常量。如果你还没有

## 一、常量

- golang 使用`const`关键字来修饰常量，常量和变量相对，常量只能读，不能修改
- `const`只能修饰`boolean`、`number`（int 相关类型、浮点类型、complex）和 string。
- 语法：`const identifier [type] = value`，其中`type`可以省略

以下是定义常量的示例方法

```go
// 定义一个字符串常量
const a string = "hello world"
// 定义一个让golang自行推倒类型的字符串常量
const b = "hello world"
// 定义一个浮点数常量
const Pi = 3.1415926
// 通过表达式定义一个常量
const c = 9 / 3
```

### 2. 变量

语法：`var identifier type`
以下是定义变量的示例

```go
// 定义int 类型变量
var a int
// 定义string 类型变量
var b string
// 定义bool 类型变量
var c bool
// 定义int 类型变量同时赋值
var d int = 8
// 定义string 类型变量同时赋值
var e string = "hello world"
```

接下来，我们编写一个程序，使用`os`包中的`Getenv`函数读取当前操作系统的`PATH`环境变量，并打印在终端上，如下代码

```go
package main

import (
	"fmt"
	"os"
)

func main() {
	var path string = os.Getenv("PATH")
	fmt.Println("path:", path)
}
```

对于多个变量，我们可以同时进行定义，如下代码

```go
package main

import (
	"fmt"
)

var (
	a int    = 1
	b string = "hello world"
	c bool
)

func main() {
	fmt.Println(a, b, c)
}
```

如果不对声明的变量进行赋值，它将会有一个默认的值，运行 main 程序，我们看到以下结果

```shell
pan@pandeMBP test2 % go run main.go
1 hello world false
pan@pandeMBP test2 %
```
