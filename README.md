# 哈萨克斯坦 11 天旅行手册

单个 HTML 文件，零外部依赖，手机打开快、离线也能看。

## 部署到 Cloudflare Workers（通过 GitHub 自动发布）

### 必须在电脑上做的步骤

#### 1. 创建 GitHub 仓库
- 登录 github.com → New repository
- 仓库名：`kazakhstan-trip`
- 设为 **Public**
- 不要勾选 "Add a README file"
- 点击 Create repository

#### 2. 把文件 push 到仓库
```bash
git clone https://github.com/你的用户名/kazakhstan-trip.git
cd kazakhstan-trip
# 把 public/index.html、wrangler.toml、README.md 放进去
git add .
git commit -m "旅行手册初始版本"
git push
```

#### 3. 在 Cloudflare 连接 GitHub 并开启自动部署
- 登录 [Cloudflare Dashboard](https://dash.cloudflare.com)
- 左侧菜单 → Workers & Pages
- 点击 Create → 选择 Connect to Git
- 授权 GitHub → 选择 `kazakhstan-trip` 仓库
- 构建配置：
  - Framework preset: None
  - Build command: （留空）
  - Deploy command: `npx wrangler deploy`
  - Root directory: `/`
- 点击 Save and Deploy

部署完成后你会得到一个 `kazakhstan-trip.你的子域名.workers.dev` 的公开网址。

之后每次 `git push`，Cloudflare 会自动重新部署。

## 文件结构
```
kazakhstan-trip/
├── public/
│   └── index.html    ← 旅行手册页面（零外部依赖）
├── wrangler.toml     ← Cloudflare Workers 配置
└── README.md         ← 本文件
```
