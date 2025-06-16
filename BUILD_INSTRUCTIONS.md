# Jekyll 构建说明

## 问题描述

当在自托管运行器上构建 Jekyll 网站时，可能会遇到以下错误：

```
The current runner (ubuntu-24.04-x64) was detected as self-hosted because the platform does not match a GitHub-hosted runner image (or that image is deprecated and no longer supported).
In such a case, you should install Ruby in the $RUNNER_TOOL_CACHE yourself, for example using https://github.com/rbenv/ruby-build
```

## 解决方案

我们提供了两个新的工作流文件来解决这个问题：

### 1. jekyll-self-hosted.yml
使用 rbenv 来安装和管理 Ruby 版本。

### 2. jekyll-ruby-build.yml
使用 ruby-build 直接安装 Ruby 到 GitHub Actions 工具缓存目录。

## 使用方法

1. **选择合适的工作流文件**：
   - 如果您使用的是自托管运行器，建议使用 `jekyll-ruby-build.yml`
   - 如果您使用的是 GitHub 托管的运行器，可以继续使用原来的 `jekyll.yml`

2. **启用新的工作流**：
   - 在 GitHub 仓库的 Actions 页面中，选择新的工作流文件
   - 或者重命名现有的工作流文件，使用新的配置

3. **手动触发构建**：
   - 在 Actions 页面点击 "Run workflow" 按钮
   - 选择 "master" 分支
   - 点击 "Run workflow"

## 文件说明

- `.ruby-version`: 指定 Ruby 版本为 3.1.4
- `Gemfile`: 已更新以包含 Ruby 版本要求
- `jekyll-self-hosted.yml`: 使用 rbenv 的工作流
- `jekyll-ruby-build.yml`: 使用 ruby-build 的工作流

## 注意事项

- 确保您的自托管运行器有足够的权限来安装软件包
- 首次运行可能需要较长时间来安装 Ruby
- 如果遇到权限问题，可能需要调整 sudo 权限设置 