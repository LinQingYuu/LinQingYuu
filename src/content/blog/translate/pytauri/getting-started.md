---
title: Getting Started
link: translate/pytauri/getting-started
date: 2026-02-14 01:47:47
description: "[PyTauri 文档] 快速开始"
tags:
  - web
  - tauri
  - pytauri
  - docs
  - translate
categories:
  - 翻译
draft: false
---

:::info

如果你想要和 PyTauri 的维护者及用户交流，请考虑加入 PyTauri 的 [Discord 服务器](https://discord.gg/TaXhVp7Shw)。

我们非常希望了解你的入门体验，这样我们就可以尽可能的让每个人都能轻松使用 PyTauri。
:::

## 创建 PyTauri App

:::info

自 0.6 版本起，推荐使用 `create-pytauri-app` 创建一个新的 PyTauri 项目，即使项目仍在开发中。请参考 [uv](https://pytauri.github.io/pytauri/latest/usage/tutorial/getting-started/) 和 [copier](https://copier.readthedocs.io/en/stable/generating/) 的文档，运行如下命令。

```bash
uvx copier copy https://github.com/pytauri/create-pytauri-app .
```

这将以交互式问答的形式初始化项目。

不过，我们仍然建议你阅读整个教程章节，因为它将有助于你理解 PyTauri 的所有细节。
:::

在开始教程之前，我们建议安装以下工具，这些工具被认为是初始化 PyTauri 项目的最佳实践。

在后续教程中，我们将全程使用这些工具。

- [create-tauri-app](https://github.com/tauri-apps/create-tauri-app): v4.5.9
- [uv](https://github.com/astral-sh/uv): v0.5.11
- [tauri-cli](https://www.npmjs.com/package/@tauri-apps/cli) :v2.1.0

:::info

以上指定的版本是编写本教程时使用的版本。你也可以使用其他版本，但用法可能会和本教程的示例不同。

:::

## 完整示例

https://github.com/pytauri/pytauri/tree/main/examples/tauri-app

## 创建一个 Tauri 项目

参考：https://tauri.app/start/create-project/#using-create-tauri-app

:::info

在这个教程中，我们将会使用 pnpm 管理前端。

但是，PyTauri 并不限制你使用的前端框架，你甚至可以使用 URL 让服务器提供前端资源。

:::

```
pnpm create tauri-app

? Project name (tauri-app) ›
? Identifier (com.tauri-app.app) ›
? Choose which language to use for your frontend ›
    ❯ TypeScript / JavaScript  (pnpm, yarn, npm, deno, bun)
? Choose your package manager ›
    ❯ pnpm
? Choose your UI template ›
    ❯ Vanilla
? Choose your UI flavor ›
    ❯ TypeScript
```

你将会看到如下目录结构。

```
└── tauri-app
    ├── README.md
    ├── index.html
    ├── package.json
    ├── src
    │   ├── assets
    │   ├── main.ts
    │   └── styles.css
    ├── src-tauri
    │   ├── Cargo.toml
    │   ├── build.rs
    │   ├── capabilities
    │   ├── icons
    │   ├── src
    │   └── tauri.conf.json
    ├── tsconfig.json
    └── vite.config.ts
```

- /tauri-app: 前端。

- /tauri-app/src-tauri: Rust 和 Python 后端。

## 启动 Tauri App

```bash
cd tauri-app
pnpm install  
pnpm tauri dev  
```

:::info

首次运行将花费一些时间用来编译依赖，后续启动时会比这快得多。

:::

祝贺你，当你看到一个带有网页内容的窗口出现时，就说明你成功的创建了一个 Tauri 应用程序。

## 下一步

下一个章节，我们将演示如何使用 PyTauri 将 Python 集成到 Tauri 应用程序。