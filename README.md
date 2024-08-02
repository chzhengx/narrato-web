# Narrato Web

Narrato Web 是一个社交博客网站（类似于 Medium.com），名为 "Narrato"。它使用自定义 API 进行所有请求，包括身份验证。

该应用由 [FSD (Feature-Sliced Design)](https://feature-sliced.design) 架构方法提供支持。

---

[![Netlify Status][netlify-domain]](https://narrato-fsd.netlify.app/)
[![Build workflow][build-domain]](https://github.com/chzhengx/narrato-web/actions/workflows/build.yml)
[![Codecov][codecov-domain]](https://app.codecov.io/gh/chzhengx/narrato-web/branch/master)
[![Code style: prettier][prettier-domain]](https://github.com/prettier/prettier)
[![license][license-domain]](https://github.com/chzhengx/narrato-web/blob/master/LICENSE)

## 功能特性


![依赖关系图][dependency-graph-domain]

**通用功能：**

- 通过 JWT 进行用户认证（登录/注册页面 + 设置页面上的登出按钮）
- CRU- 用户（注册 & 设置页面 - 无需删除）
- CRUD 文章
- CR-D 文章评论（无需更新）
- 获取和显示文章分页列表
- 喜欢文章
- 关注其他用户

**页面结构概述：**

- 首页 (URL: / )
  - 标签列表
  - 从 Feed、Global 或按标签获取的文章列表
  - 文章列表的分页
- 登录/注册页面 (URL: /login, /register )
  - 使用 JWT （将令牌存储在 localStorage）
  - 认证可以轻松切换为基于会话/ Cookie
- 设置页面 (URL: /settings )
- 编辑页面以创建/编辑文章 (URL: /editor, /editor/article-slug-here )
- 文章页面 (URL: /article/article-slug-here )
  - 删除文章按钮（仅对文章作者显示）
  - 从服务器客户端渲染 Markdown
  - 页面底部的评论部分
  - 删除评论按钮（仅对评论作者显示）
- 个人资料页面 (URL: /profile/
, /profile/
/favorites)
  - 显示基本用户信息
  - 从作者创建的文章或作者喜欢的文章中填充文章列表

## 开始使用

项目使用 [Create Vite](https://vitejs.dev/guide/#getting-started) 进行初始化。

在本地运行前端：

1. 克隆代码仓库
2. 运行 `yarn install` 安装所有定义在`package.json` 文件中的依赖项。
3. 运行 `yarn dev` 启动 Vite 开发服务器。

## 脚本

- `yarn dev` - 启动带有热重载的开发服务器。
- `yarn build` - 进行生产构建。生成的文件将位于 dist 文件夹中。
- `yarn preview` - 本地预览生产构建。
- `yarn lint` - 运行 ESLint。
- `yarn lint:perf` - 运行 ESLint 并跟踪各个规则的性能。
- `yarn prettier` - 运行 Prettier 格式化已更改的文件。
- `yarn prettier:all` - 运行 Prettier 格式化所有文件。
- `yarn test:run` - 运行所有测试套件。
- `yarn test:watch` - 运行所有测试套件，并在更改时重新运行测试。
- `yarn test:coverage` - 运行所有测试套件并启用覆盖率报告。
- `yarn test:coverage:open` - 运行所有测试套件并启用覆盖率报告，然后在浏览器中打开覆盖率报告。
- `yarn dep-cruiser:preview` - 创建依赖关系图[^1]。

[![Feature-Sliced Design][shields-fsd-domain]](https://feature-sliced.design/)
[![Vite][shields-vite-domain]](https://vitejs.dev/)
[![React][shields-react-domain]](https://react.dev/)
[![React Router][shields-react-router-domain]](https://reactrouter.com/)
[![React Query][shields-react-query-domain]](https://tanstack.com/query/v4/)
[![Zustand][shields-zustand-domain]](https://zustand-demo.pmnd.rs/)
[![TypeScript][shields-typescript-domain]](https://www.typescriptlang.org/)

[shields-react-router-domain]: https://img.shields.io/badge/React_Router-CA4245?style=for-the-badge&logo=react-router&logoColor=white
[shields-react-query-domain]: https://img.shields.io/badge/-React%20Query-FF4154?style=for-the-badge&logo=react%20query&logoColor=white
[shields-zustand-domain]: https://img.shields.io/badge/zustand-%2320232a.svg?style=for-the-badge&logo=react&logoColor=%2361DAFB
[shields-typescript-domain]: https://img.shields.io/badge/typescript-%23007ACC.svg?style=for-the-badge&logo=typescript&logoColor=white
[shields-fsd-domain]: https://img.shields.io/badge/Feature--Sliced-Design?style=for-the-badge&color=F2F2F2&labelColor=262224&logoWidth=10&logo=data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABQAAAAaCAYAAAC3g3x9AAAACXBIWXMAAALFAAACxQGJ1n/vAAAAAXNSR0IArs4c6QAAAARnQU1BAACxjwv8YQUAAABISURBVHgB7dKxCQAgDETR0w2cws0cys2cwhEUBbsggikCuVekDHwSQFlYo7Q+8KnmtHdFWMdk2cl5wSsbxGSZw8dm8pX9ZHUTMBUgGU2F718AAAAASUVORK5CYII=
[shields-vite-domain]: https://img.shields.io/badge/vite-%23646CFF.svg?style=for-the-badge&logo=vite&logoColor=white
[shields-react-domain]: https://img.shields.io/badge/react-%2320232a.svg?style=for-the-badge&logo=react&logoColor=%2361DAFB
[netlify-domain]: https://api.netlify.com/api/v1/badges/5d5013c3-ec61-4496-8f48-caa7145fb166/deploy-status
[dependency-graph-domain]: ./dependency-graph-preview.svg
[build-domain]: https://github.com/sldk-yuri/realworld-react-fsd/actions/workflows/build.yml/badge.svg
[codecov-domain]: https://codecov.io/gh/sldk-yuri/realworld-react-fsd/branch/master/graph/badge.svg?token=IXE2YRPYK5
[prettier-domain]: https://img.shields.io/badge/code_style-prettier-ff69b4.svg
[license-domain]: https://img.shields.io/badge/license-MIT-green.svg

---

[^1]: 这假设 GraphViz 的 `dot` 命令可用 - 在大多数 Linux 和类似系统中，这将是可用的。如果不可用，请参阅 [GraphViz 的下载页面](https://www.graphviz.org/download/) 获取安装说明。