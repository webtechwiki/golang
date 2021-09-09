# 1. 包的应用
在介绍语法基础之前，我们先 回顾一下golang 的第一个程序，以及在前面文章中提到的基础知识

```go
package main

import "fmt"

func main() {
	fmt.Println("hello world")
}
```
*  golang中，有且仅有一个main入口函数。
*  同一个包中的函数，可以直接调用。
*  不同包中的函数，通过包名+点+函数名进行调用。
*  包的访问控制：
1. 大写意味着这个函数/变量是可导出的
2. 小写意味着这个函数/变量是私有，包外部不可用

### 2. 知识拓展
* **包别名**
实际上，golang中的包还可以使用别名。接下来，我们相对GOPATH，写一个程序，使用包别名来访问包中的函数。
我们先定义一个文件```learn/test1/mypkg/add.go```，添加以下代码
```go
package mypkg

import "fmt"

const Name = "zhangsan"
const Age = 20

func Test() {
	fmt.Println("call test")
}
```
再定义一个主函数文件```learn/test1/main.go```，添加以下代码
```go
package main

import (
	"fmt"
	pkg "learn/test1/mypkg"
)

func main() {
	fmt.Println("name is ", pkg.Name)
	fmt.Println("age is ", pkg.Age)
	pkg.Test()
}
```

我们通过```pkg```给倒入的包设置了别名，并且在main函数中使用别名来访问mypkg包中的常量和函数，最后在main.go文件所在的目录，打开终端运行结果如下：
```shell
pan@pandeMBP test1 % go run main.go 
name is  zhangsan
age is  20
call test
pan@pandeMBP test1 %
```

* **init函数**


