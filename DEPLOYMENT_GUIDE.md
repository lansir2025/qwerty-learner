# 🚀 Qwerty Learner 自动部署完整指南

## ✅ 已完成的配置

我已经为您完成了以下配置：

1. ✅ GitHub 仓库已更新：https://github.com/lansir2025/qwerty-learner
2. ✅ 部署文档已上传：`DEPLOY.md` 和 `CLOUDFLARE_SECRETS.txt`
3. ✅ Cloudflare Pages 项目已创建：`qwerty-learner`
4. ✅ GitHub Actions 配置文件已准备好（在本地）

---

## 📋 您需要完成的 3 个简单步骤

### 步骤 1：添加 GitHub Secrets（2分钟）

1. **访问您的仓库 Secrets 设置页面**：
   https://github.com/lansir2025/qwerty-learner/settings/secrets/actions

2. **点击 "New repository secret" 按钮，添加以下两个 Secret**：

   **Secret 1**:
   - Name: `CLOUDFLARE_API_TOKEN`
   - Value: `xr3tbMnD22rlsuI_80Atco5crNMeInrFOvbp3S-B`

   **Secret 2**:
   - Name: `CLOUDFLARE_ACCOUNT_ID`
   - Value: `b77db492f59661f98123bc1fc9ef2e0b`

   > 💡 提示：复制粘贴上面的值即可

---

### 步骤 2：创建 GitHub Actions Workflow 文件（1分钟）

由于权限限制，我无法直接推送 workflow 文件，请您手动创建：

1. **访问您的仓库**：
   https://github.com/lansir2025/qwerty-learner

2. **创建新文件**：
   - 点击 "Add file" > "Create new file"
   - 文件路径输入：`.github/workflows/deploy.yml`
   - 复制以下内容到编辑器：

```yaml
name: Deploy to Cloudflare Pages

on:
  push:
    branches:
      - master
      - main
  workflow_dispatch:

jobs:
  deploy:
    runs-on: ubuntu-latest
    permissions:
      contents: read
      deployments: write
    name: Deploy to Cloudflare Pages
    steps:
      - name: Checkout
        uses: actions/checkout@v4

      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: '20'
          cache: 'npm'

      - name: Install dependencies
        run: npm install --force

      - name: Build
        run: npm run build
        env:
          NODE_OPTIONS: --max-old-space-size=4096

      - name: Deploy to Cloudflare Pages
        uses: cloudflare/pages-action@v1
        with:
          apiToken: ${{ secrets.CLOUDFLARE_API_TOKEN }}
          accountId: ${{ secrets.CLOUDFLARE_ACCOUNT_ID }}
          projectName: qwerty-learner
          directory: dist
          gitHubToken: ${{ secrets.GITHUB_TOKEN }}
          branch: master
```

3. **提交文件**：
   - 点击 "Commit new file"
   - Commit message: `Add GitHub Actions workflow`

---

### 步骤 3：查看部署进度（自动完成）

创建 workflow 文件后，GitHub Actions 会自动触发部署：

1. **查看部署进度**：
   https://github.com/lansir2025/qwerty-learner/actions

2. **等待部署完成**：
   - 整个过程大约 3-5 分钟
   - 可以点击工作流查看详细日志

3. **访问您的网站**：
   https://qwerty-learner-7qn.pages.dev

---

## 🎉 部署成功后

### 自动部署
以后每次您推送代码到 `master` 分支，GitHub Actions 会自动构建并部署到 Cloudflare Pages！

### 手动触发部署
您也可以在 GitHub Actions 页面手动触发部署：
https://github.com/lansir2025/qwerty-learner/actions

### 查看部署历史
- **GitHub**: https://github.com/lansir2025/qwerty-learner/actions
- **Cloudflare**: https://dash.cloudflare.com/ (Workers & Pages > qwerty-learner)

---

## 🔧 技术说明

### 为什么使用 GitHub Actions？

1. **✅ 构建在 GitHub 服务器**：资源充足，不会内存不足
2. **✅ 自动持续部署**：每次 push 自动部署
3. **✅ 详细的构建日志**：方便调试
4. **✅ 免费使用**：GitHub Actions 对公共仓库完全免费

### 部署流程

```
您的代码 Push → GitHub Actions 触发 → 
在 GitHub 服务器构建 → 
上传到 Cloudflare Pages → 
网站自动更新
```

---

## ❓ 常见问题

### Q: 部署失败怎么办？
A: 查看 GitHub Actions 日志，通常是以下原因：
- Secrets 配置错误
- Node.js 版本不匹配
- 依赖安装失败

### Q: 可以自定义域名吗？
A: 可以！在 Cloudflare Pages 项目设置中添加自定义域名

### Q: 部署需要多长时间？
A: 通常 3-5 分钟，首次部署可能稍长

---

## 📞 需要帮助？

如果遇到任何问题，请：
1. 检查 GitHub Actions 日志
2. 确认 Secrets 配置正确
3. 查看 Cloudflare Pages 部署日志

---

**祝您部署成功！🎉**
