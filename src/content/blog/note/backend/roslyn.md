---
title: C# 开发笔记：初识源生成器
date: 2026-06-30 12:50:42
updated: 2026-06-30 13:09:26
categories:
  - [后端笔记]
tags:
  - 后端笔记
  - 源生成器
  - 元编程
  - 预处理
draft: true
catalog: true
---
## 元编程是什么

!!什么是元编程？好吃吗？!!

元编程（Meta-Programming），是一种强大的技术。与传统编程不同的是，元编程是将代码视作数据，并允许代码进行处理、修改、生成等一系列操作。

## 为什么需要这些？

元编程最大的好处就是可以将一些重复性高的工作（例如 DTO 声明，属性映射，MVVM）交由机器执行，从而将人解放出来专注于实现机器不能处理的业务逻辑。

一个经典的例子就是 Spring Boot，其大量利用注解和反射对代码进行修改!!并创造了面向注解编程!!

## .NET Roslyn Source Generator

虽然 Spring Boot 面向注解编程非常高级好用，但是 Spring Boot 也有自己的缺点，因为其元编程是建立在反射上扫描注解和代码生成的。

而众所周知反射是有开销的，所以大量类扫描的开销可想而知。 !!这也就是为什么只有公司用这个，因为人家的服务器是一天 24 小时运转的。!!

既然反射有开销，那有什么办法解决呢？

当然有，既然反射有运行时开销，那么我们可以丢到编译期完成。 !!反正编译本身就比较吃 CPU 和时间，把 Source Generator 丢到编译期跑也不会死。!!

<!--
using System.Text;
using Microsoft.CodeAnalysis;

namespace SourceGenerators;

[Generator]
public class ProgramMainSourceGenerator: IIncrementalGenerator
{
    public void Initialize(IncrementalGeneratorInitializationContext context)
    {
        var sb = new StringBuilder();
        sb.AppendLine("namespace ConsoleApp;");
        sb.AppendLine("");
        sb.AppendLine("public partial class Program{");
        sb.AppendLine("    ");
        sb.AppendLine("    public static void Main(string[] args) => System.Console.WriteLine(\"Hello Tsukishiro Mei!\");");
        sb.AppendLine("}");
        context.RegisterPostInitializationOutput(sourceGeneratorContext =>
        {
            sourceGeneratorContext.AddSource("Program.g.cs", sb.ToString());
        });
    }
}

namespace ConsoleApp;

public partial class Program;

-->