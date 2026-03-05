# Ai Shepherd 落地页 — GitHub Pages 部署指引

## 仓库结构

```
/
├── index.html          ← 主落地页
├── privacy/
│   ├── index.html      ← 隐私政策
│   └── terms/
│       └── index.html  ← 使用条款
├── images/             ← 截图和图标
└── CNAME               ← 自定义域名：www.aishepherd.top
```

## 部署步骤

### 方法一：GitHub CLI（推荐）

```bash
# 1. 在 GitHub 创建新仓库（名称建议：aishepherd-website）
gh repo create aishepherd-website --public

# 2. 推送代码
git remote add origin https://github.com/<your-username>/aishepherd-website.git
git branch -M main
git push -u origin main

# 3. 在 GitHub 仓库 Settings → Pages 中：
#    - Source: Deploy from a branch
#    - Branch: main / (root)
#    - 保存后等待 1-2 分钟即可访问
```

### 方法二：手动上传

1. 在 GitHub 创建新公开仓库
2. 将 `aishepherd-github-pages-deploy.zip` 解压
3. 将所有文件上传到仓库根目录
4. 在仓库 Settings → Pages → Source 选择 `main` 分支

## DNS 配置

在您的域名服务商（如 Cloudflare、阿里云）添加以下 DNS 记录：

| 类型 | 名称 | 值 |
|------|------|-----|
| CNAME | www | `<your-username>.github.io` |
| A | @ | `185.199.108.153` |
| A | @ | `185.199.109.153` |
| A | @ | `185.199.110.153` |
| A | @ | `185.199.111.153` |

> 如果使用 Cloudflare，请将 www 的代理状态设为 **DNS only**（灰色云朵），否则 GitHub Pages HTTPS 证书可能无法自动签发。

## 验证

部署成功后，以下 URL 应正常访问：
- `https://www.aishepherd.top` → 主落地页
- `https://www.aishepherd.top/privacy` → 隐私政策
- `https://www.aishepherd.top/privacy/terms` → 使用条款
