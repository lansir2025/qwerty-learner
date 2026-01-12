# Qwerty Learner - 自动部署到 Cloudflare Pages

这是 [Qwerty Learner](https://github.com/RealKai42/qwerty-learner) 的 Fork 版本，配置了自动部署到 Cloudflare Pages。

## 🚀 自动部署说明

本仓库配置了 GitHub Actions，每次推送到 `master` 或 `main` 分支时会自动构建并部署到 Cloudflare Pages。

## ⚙️ 配置步骤

### 1. 设置 GitHub Secrets

为了让 GitHub Actions 能够部署到 Cloudflare Pages，需要在 GitHub 仓库中设置以下 Secrets：

1. 访问您的仓库设置页面：https://github.com/lansir2025/qwerty-learner/settings/secrets/actions
2. 点击 **"New repository secret"** 添加以下两个 Secret：

   **Secret 1: CLOUDFLARE_API_TOKEN**
   - Name: `CLOUDFLARE_API_TOKEN`
   - Value: 您的 Cloudflare API Token
   - 获取方式：
     1. 登录 Cloudflare Dashboard
     2. 进入 "My Profile" > "API Tokens"
     3. 创建一个新的 Token，权限选择 "Cloudflare Pages - Edit"

   **Secret 2: CLOUDFLARE_ACCOUNT_ID**
   - Name: `CLOUDFLARE_ACCOUNT_ID`
   - Value: 您的 Cloudflare Account ID
   - 获取方式：
     1. 登录 Cloudflare Dashboard
     2. 在右侧栏可以看到 "Account ID"

### 2. 触发部署

设置完 Secrets 后，有两种方式触发部署：

**方式 1：推送代码**
```bash
git add .
git commit -m "Update deployment config"
git push origin master
```

**方式 2：手动触发**
1. 访问：https://github.com/lansir2025/qwerty-learner/actions
2. 选择 "Deploy to Cloudflare Pages" 工作流
3. 点击 "Run workflow" 按钮

### 3. 查看部署状态

- GitHub Actions 日志：https://github.com/lansir2025/qwerty-learner/actions
- Cloudflare Pages 部署：https://dash.cloudflare.com/ (Workers & Pages)

## 🌐 访问地址

部署成功后，您的网站将在以下地址可用：
- **生产环境**: https://qwerty-learner-7qn.pages.dev

## 📝 本地开发

```bash
# 安装依赖
npm install

# 启动开发服务器
npm run dev

# 构建生产版本
npm run build
```

## 🔧 技术栈

- React 18
- TypeScript
- Vite
- TailwindCSS
- Cloudflare Pages

## 📄 License

GPL-3.0 License
