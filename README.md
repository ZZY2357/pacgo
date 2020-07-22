# Pac Go

一个用 Go 写的吃豆人游戏的克隆（用 emoji！）

![screenshot](./screenshot.jpg)

## 介绍

这个项目是一个向人们介绍[Go 编程语言](https://golang.org)的教程。

### 为什么要有一个新的教程？

我们有许多其他不错的教程，但是这个教程的主要目的是有趣且不同地学习
Go。是的，我们需要天天了解 API 和 CRUD，但当我们应对新的东西时，为什么不制作一个游戏呢？

Go 是再次使编程变得有趣的语言之一，而且什么能比编写一个游戏更有趣？兴趣？很好，让我们开始吧！

我们将编写一个终端上的 Pac Man 游戏克隆。在编写游戏时，你会遇到一些能够为探索这个语言的功能奠定基础、有趣的程序需求，包括输入、输出、函数、指针、并发以及些许数学知识。

你还将学到一些关于终端和神奇的转义的更多知识。

### Conference Talks

If you want to have a look at the tutorial in a talk format before trying (about 25 minutes), try one of the links below:

1. [Google Cloud Next UK '19](https://cloud.withgoogle.com/next/uk/sessions?session=DZ224), London, UK (November, 21st 2019)
1. [London Gophers](https://youtu.be/SM8LTMnB4x0), London, UK
1. [GoWayFest 3.0](https://youtu.be/0qvW4kIlS8I), Minsk, Belarus
1. [GothamGo 2019](https://youtu.be/GH0DlCKTppE), New York City, NY, USA

### 参与贡献

这个项目使用 MIT 开源协议进行开源，这意味着你基本上可以对它为所欲为，只需要保留我适当的名誉。：）

如果你想要参与贡献，只需要提个 issue 或者 提交个 pull request。

如果你不知道该为这个项目写些什么，你可以看看还未关闭的 issue
或者看看[待办事项](TODO.md)。

待办事项中的任何内容都为计划的开发步骤，除非另有说明。

### 协议

请参阅 [协议](LICENSE).

### 联系作者

如果你有任何问题，请通过
[daniela.petruzalek@gmail.com](mailto:daniela.petruzalek@gmail.com) 联系我。我的
Twitter 用户名也是 [@danicat83](https://twitter.com/danicat83)。

## 快速上手

### 先决条件

你最好：
- 对程序运行方式有个基本的了解，我们不会介绍这些基础。
- 对终端有个大概的了解（知道怎样使用命令行应用）

当然，如果你不具有上述条件，但是具有好奇心，并且想去尝试，请放开做。

### 兼容警告！！！

本教程已经在 **Linux** 和 **Mac OS X** 环境下进行了测试。对于 Windows
环境您_也许_需要安装一个终端模拟器，比如 [Git BASH](https://gitforwindows.org/)

译注：天朝大陆用户可以从[华为镜像](https://mirrors.huaweicloud.com/git-for-windows/)下载 Git BASH。

请注意，这些代码依赖终端来渲染游戏，这会在不同的配置下呈现不同的结果。

如果你有任何问题，请随时提 issue，以便让我们找到合适的解决方案，同时附上你的操作系统和终端名称和版本。

**注意：** VS Code 的终端目前不能正确地渲染游戏，这是个已知问题。

### 起步

为了起步，请确保你已安装了 Go。

如果你没有，请参照 [golang.org](https://golang.org) 的说明安装。

译注：天朝大陆用户可以使用 Go 语言中文网搭建的[Go 官网镜像](https://docs.studygolang.com/)。

### 如何使用本教程

In every step, including step 0 (this one), we will describe the task in the README.md file followed by the code that does it and an explanation of how it works.

Every step is located in its separate folder except for this one. Look for the folders stepXX for any given step.

We will be editing a file called `main.go`. All the code in this tutorial will reside in this file. A proper program would usually have multiple source code files, but for the sake of simplicity we are keeping this program limited to one source.

The README.md for each step will explain the intent and show the modifications needed to proceed. You should make them in your own `main.go` file.

You can also use the `main.go` in step 00 as a starting point and modify it incrementally when progressing through the steps.

If you get lost, every step has its own `main.go` file with the changes to that step already applied. That also means that if you want to fast track to a given step you can start with the `main.go` from the previous step.

## Step 00: Hello (Game) World

We are going to start by laying the ground a skeleton of what a game program looks like.

Pick a directory to be your work dir (e.g., `tutorial` under your home folder) and create a file called `main.go` with the content below.

Note: Alternatively you can just clone this repository and edit the `main.go` file on its root.

```go
package main

import "fmt"

func main() {
    // initialize game

    // load resources

    // game loop
    for {
        // update screen

        // process input

        // process movement

        // process collisions

        // check game over

        // Temp: break infinite loop
        fmt.Println("Hello, Pac Go!")
        break

        // repeat
    }
}
```

### Running your first Go program

Now that we have a `main.go` file (`.go` is the file extension for Go source code), you can run it by using the command line tool `go`. Just type:

```sh
$ go run main.go
Hello, Pac Go!
```

That's how we run a single file in Go. You can also build it as an executable program with the command `go build`. If you run `go build` it will compile the files in the current directory in a binary with the name of the directory. Then you can run it as a regular program, for example:

```sh
$ go build
$ ./pacgo
Hello, Pac Go!
```

For the purposes of this tutorial we are using only a single file of code (`main.go`), so you may use either `go build` and run the command or just `go run main.go` as it does both automatically.

### Understanding the program

Now let's have a close look of what the program does.

First line is the `package` name. Every valid Go program must have one of these. Also, if you want to make a **runnable** program you must have a package called `main` and a `main` function, which will be the entry point of the program.

We are creating an executable program so we are using `package main` on the top of the file.

Next are the `import` statements. You use those to make code in other packages accessible to your program.

Finally the `main` function. You define function in Go with the keyword `func` followed by its name, its parameters in between a pair of parentheses, followed by the return value and finally the function body, which is contained in a pair of curly brackets `{}`. For example:

```go
func main() {
    // I'm a function body
}
```

This is a function called `main` which takes no parameters and returns nothing. That's the proper definition of a main function in Go, as opposed to the definitions in other languages where the main function may take the command line arguments and/or return an integer value.

We have different ways to deal with the command line arguments and return values in Go, which we will see in [Step 08](step08/README.md).

In the game main function we have some comments (any text after `//` is a comment) that are acting as placeholders for the actual game code. We'll use those to drive each modification in an orderly way.

The most important concept in a game is what is called the game loop. That's basically an infinite loop where all the game mechanics are processed.

A loop in Go is defined with the keyword `for`. The `for` loop can have an initializer, a condition and a post processing step, but all of those are optional. If you omit all you have a loop that never ends:

```go
for {
    // I never end
}
```

We can exit an infinite loop with a `break` statement. We are using it in the sample code to end the infinite loop after printing "Hello, Pac Go!" with the `Println` function from the `fmt` package (comments omitted for brevity):

```go
func main() {
    for {
        fmt.Println("Hello, Pac Go!")
        break
    }
}
```

Of course, in this case the infinite loop with a non-conditional break is pointless, but it will make sense in the next steps!

Congratulations, step 00 is complete!

[Take me to step 01!](step01/README.md)
