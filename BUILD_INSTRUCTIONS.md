# Jekyll 构建说明

## 问题描述

当在自托管运行器上构建 Jekyll 网站时，可能会遇到以下错误：

```
The current runner (ubuntu-24.04-x64) was detected as self-hosted because the platform does not match a GitHub-hosted runner image (or that image is deprecated and no longer supported).
In such a case, you should install Ruby in the $RUNNER_TOOL_CACHE yourself, for example using https://github.com/rbenv/ruby-build
```

## 解决方案

我们提供了多个工作流文件来解决这个问题：

### 1. jekyll.yml (已更新)
主要的工作流文件，现在支持自托管运行器。

### 2. jekyll-fix.yml (推荐)
专门为修复自托管运行器问题而创建的工作流。

### 3. jekyll-self-hosted.yml
使用 rbenv 来安装和管理 Ruby 版本。

### 4. jekyll-ruby-build.yml
使用 ruby-build 直接安装 Ruby 到 GitHub Actions 工具缓存目录。

## 使用方法

### 方法 1: 使用更新的主工作流 (推荐)
1. 现在 `jekyll.yml` 已经更新，支持自托管运行器
2. 直接推送代码到 master 分支即可触发构建

### 方法 2: 使用专门的工作流
1. 在 GitHub 仓库的 Actions 页面中，选择 `jekyll-fix.yml` 工作流
2. 点击 "Run workflow" 按钮
3. 选择 "master" 分支
4. 点击 "Run workflow"

### 方法 3: 手动触发
如果自动触发失败，可以：
1. 进入 GitHub Actions 页面
2. 选择任意一个工作流文件
3. 点击 "Run workflow" 手动触发

## 工作流特点

- **自动检测**: 自动识别是自托管还是 GitHub 托管的运行器
- **条件执行**: 只在自托管运行器上执行 Ruby 安装步骤
- **兼容性**: 同时支持 GitHub 托管和自托管运行器
- **遵循建议**: 按照错误信息中的建议使用 ruby-build

## 文件说明

- `.ruby-version`: 指定 Ruby 版本为 3.1.4
- `Gemfile`: 已更新以包含 Ruby 版本要求
- `jekyll.yml`: 主要工作流文件（已更新）
- `jekyll-fix.yml`: 专门修复自托管运行器问题的工作流
- `jekyll-self-hosted.yml`: 使用 rbenv 的工作流
- `jekyll-ruby-build.yml`: 使用 ruby-build 的工作流

## 注意事项

- 确保您的自托管运行器有足够的权限来安装软件包
- 首次运行可能需要较长时间来安装 Ruby
- 如果遇到权限问题，可能需要调整 sudo 权限设置
- 建议先尝试 `jekyll-fix.yml` 工作流，因为它专门针对这个问题进行了优化 