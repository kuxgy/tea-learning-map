# 哲学入门学习地图 · 静态站点

一个完全自包含的单页静态站点，无构建、无后端、无本地依赖。

## 目录内容

```
dist/
├── index.html   # 唯一页面（CSS / JS / favicon 全部内联）
└── README.md    # 本文件
```

- 单文件 62 KB，gzip 后约 15 KB。
- 字体走 CDN（`miaoda.feishu.cn`），断网时自动回退到系统衬线/黑体，页面不破版。
- 无本地图片、无 JSON 数据、无 fetch/XHR，纯静态。

## 部署方式（任选其一）

### 1. GitHub Pages
1. 新建仓库，把整个 `dist/` 里的文件推上去。
2. 仓库 Settings → Pages → Source 选 `main` 分支根目录。
3. 访问 `https://<用户名>.github.io/<仓库名>/`。

### 2. Netlify / Vercel
- 直接把 `dist/` 文件夹拖到 Netlify Drop（app.netlify.com/drop）即可，秒级拿到 HTTPS 链接。
- Vercel：`vercel deploy` 指向该目录。

### 3. 对象存储（阿里云 OSS / 腾讯云 COS / 七牛）
- 把 `index.html` 上传到 Bucket，开启静态网站托管，默认文档填 `index.html`。

### 4. Nginx / 任意 Web 服务器
```nginx
server {
    listen 80;
    root /path/to/dist;
    index index.html;
    location / { try_files $uri $uri/ /index.html; }
}
```

### 5. 本地预览
直接双击 `index.html` 用浏览器打开即可，无需任何服务器。
