# GitHub 个人主页配置指南

本文档将帮助你配置和个性化你的 GitHub 主页。

## 📋 前置步骤

### 1. 创建同名仓库

1. 在 GitHub 上创建一个新仓库
2. 仓库名必须与你的 GitHub 用户名完全相同（例如：如果你的用户名是 `tetsuya`，仓库名也应该是 `tetsuya`）
3. 添加一个 README.md 文件
4. 将本仓库的内容克隆或推送到你的仓库

### 2. 替换占位符

在 `README.md` 文件中，将所有 `YOUR_USERNAME` 替换为你的实际 GitHub 用户名。

## 🔧 功能配置

### 1. 贪吃蛇动画

**已自动配置** ✅

- 工作流文件：`.github/workflows/snake.yml`
- 自动每 2 小时更新一次
- 首次使用需要手动运行一次：`Actions` → `Generate Snake Animation` → `Run workflow`

### 2. Metrics 统计信息

**需要手动配置** ⚠️

1. 创建 GitHub Personal Access Token：
   - 访问：`Settings` → `Developer settings` → `Personal access tokens` → `Tokens (classic)`
   - 点击 `Generate new token (classic)`
   - 勾选 `public_repo` 权限（至少需要 `public_access`）
   - 生成并复制 token（只显示一次，请妥善保管）

2. 在仓库中添加 Secret：
   - 访问你的仓库：`Settings` → `Secrets and variables` → `Actions`
   - 点击 `New repository secret`
   - 名称：`METRICS_TOKEN`
   - 值：粘贴刚才复制的 token
   - 点击 `Add secret`

3. 创建 Environment（可选但推荐）：
   - 访问：`Settings` → `Environments`
   - 点击 `New environment`
   - 名称：`production`
   - 点击 `Configure environment`

4. 修改工作流文件：
   - 编辑 `.github/workflows/metrics.yml`
   - 将 `YOUR_USERNAME` 替换为你的 GitHub 用户名

5. 手动运行一次工作流：
   - `Actions` → `Metrics` → `Run workflow`

### 3. GitHub 3D 统计

**已自动配置** ✅

- 工作流文件：`.github/workflows/profile-3d.yml`
- 自动每天更新一次
- 首次使用需要手动运行一次：`Actions` → `GitHub-Profile-3D-Contrib` → `Run workflow`

**注意**：如果遇到权限错误，确保在仓库设置中启用了 Actions 的写权限：
- `Settings` → `Actions` → `General` → `Workflow permissions`
- 选择 `Read and write permissions`

### 4. 博客文章同步（可选）

**需要手动配置** ⚠️

1. 确保你的博客有 RSS 功能
2. 编辑 `.github/workflows/blog-post-workflow.yml`
3. 将 `feed_list` 的值替换为你的博客 RSS 链接
4. 可选：调整 `max_post_count` 等参数
5. 在 `README.md` 中确保有以下注释：
   ```markdown
   <!-- BLOG-POST-LIST:START -->
   <!-- BLOG-POST-LIST:END -->
   ```
6. 手动运行一次工作流

### 5. 社交统计（可选）

如果你有 LeetCode、知乎、B站等账号，可以添加相应的统计卡片：

1. 访问：https://github.com/songquanpeng/stats-cards
2. 查看支持的平台和配置方法
3. 在 `README.md` 中添加相应的代码

### 6. 访客统计

**已自动配置** ✅

- 只需将 `README.md` 中的 `YOUR_USERNAME` 替换为你的用户名即可
- 可以自定义颜色：修改 `left_color` 和 `right_color` 参数

## 🎨 自定义主题

### GitHub 统计卡片主题

在 `README.md` 中，你可以修改 `theme` 参数来更改主题：

可用主题：
- `default`
- `dark`
- `radical`
- `merko`
- `gruvbox`
- `tokyonight`（当前使用）
- `onedark`
- `cobalt`
- `synthwave`
- `highcontrast`
- `dracula`

### GitHub 活动图主题

在活动统计图的 URL 中修改 `theme` 参数：
- `tokyo-night`（当前使用）
- `github`
- `github-dark`
- `github-compact`
- 等等

## 📝 个性化内容

### 1. 关于我部分

编辑 `README.md` 中的"关于我"部分，填写你的个人信息。

### 2. 技术栈

根据你的实际技能，添加或删除技术栈徽章。徽章来自 [Shields.io](https://shields.io/)。

### 3. 联系方式

更新联系方式部分，包括：
- Email
- 个人网站
- LinkedIn
- Twitter
- 其他社交媒体

## 🚀 部署步骤

1. **克隆或创建仓库**：
   ```bash
   git clone https://github.com/YOUR_USERNAME/YOUR_USERNAME.git
   cd YOUR_USERNAME
   ```

2. **替换所有占位符**：
   - 在 `README.md` 中替换所有 `YOUR_USERNAME`
   - 在 `.github/workflows/metrics.yml` 中替换 `YOUR_USERNAME`

3. **提交并推送**：
   ```bash
   git add .
   git commit -m "Initial commit: Add GitHub profile README"
   git push origin main
   ```

4. **配置 Secrets 和 Environment**（参考上面的 Metrics 配置）

5. **手动运行工作流**：
   - 访问 `Actions` 标签页
   - 运行每个工作流一次以生成初始内容

6. **等待生成完成**：
   - 通常需要几分钟
   - 检查 `Actions` 标签页查看运行状态

## 🔍 验证

完成配置后，访问你的 GitHub 主页（`https://github.com/YOUR_USERNAME`），你应该能看到：

- ✅ 各种统计卡片
- ✅ 贪吃蛇动画（可能需要等待首次运行完成）
- ✅ Metrics 统计图（需要配置 token）
- ✅ 3D 贡献图（需要等待首次运行完成）
- ✅ 访客统计
- ✅ 活动统计图

## ❓ 常见问题

### Q: 贪吃蛇动画不显示？
A: 确保工作流已成功运行，并且生成了 `output` 分支。检查 `Actions` 标签页查看是否有错误。

### Q: Metrics 统计不显示？
A: 
1. 检查是否创建了 `METRICS_TOKEN` secret
2. 检查 token 是否有正确的权限
3. 检查工作流是否成功运行
4. 确保 `github-metrics.svg` 文件已生成

### Q: 3D 统计图不显示？
A: 
1. 确保工作流已成功运行
2. 检查 `profile-3d-contrib` 目录是否已创建
3. 确保仓库的 Actions 权限设置为"Read and write"

### Q: 如何更新内容？
A: 大部分内容会自动更新（通过定时任务），你也可以手动运行工作流来立即更新。

## 📚 参考资源

- [GitHub Profile README 官方文档](https://docs.github.com/en/account-and-profile/setting-up-and-managing-your-github-profile/customizing-your-profile/managing-your-profile-readme)
- [awesome-github-profile-readme](https://github.com/abhisheknaiidu/awesome-github-profile-readme)
- [github-readme-stats](https://github.com/anuraghazra/github-readme-stats)
- [metrics](https://github.com/lowlighter/metrics)

## 🎉 完成！

现在你的 GitHub 主页应该已经美化了！记得定期更新内容，保持主页的活跃度。

祝你玩得开心！ 🚀

