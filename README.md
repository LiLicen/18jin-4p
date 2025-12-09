# KFC 疯狂星期四 V我50 小页

本仓库包含三个文件，开箱即用：
- `index.html`：主页，含按钮跳转收款页 + 直接展示二维码。
- `zhifu.html`：支付页，随机趣味口号 + 二维码展示与下载。
- `qrcode.jpg`：收款二维码图片（需替换成你的二维码，文件名保持不变）。

## 本地预览
直接双击 `index.html`，或在项目目录启动本地服务器：
```bash
python -m http.server 8000
# 浏览器打开 https://lilicen.github.io/kfc-v50/
```

## 部署到 GitHub Pages
1. 创建公共仓库（示例名：`kfc-v50`）。  
2. 将三个文件放在仓库根目录，提交并推送到 `main`：
   ```bash
   git add index.html zhifu.html qrcode.jpg
   git commit -m "init: kfc v50 page"
   git push -u origin main
   ```
3. 仓库 Settings → Pages：  
   - Source 选 `Deploy from a branch`  
   - Branch 选 `main`，目录选 `/root`  
   - 保存，等待生成访问链接，形如 `https://USERNAME.github.io/kfc-v50/`
4. 分享链接：  
   - 主页：`https://USERNAME.github.io/kfc-v50/index.html`  
   - 支付页：`https://USERNAME.github.io/kfc-v50/zhifu.html`

## 更换二维码
把你的收款二维码图片替换为 `qrcode.jpg`（文件名不变，与 HTML 同级）。刷新页面即可。

## 手机端访问

### 方法一：GitHub Pages（推荐，任何设备都能访问）
按照上面的“部署到 GitHub Pages”步骤，部署后直接用手机浏览器打开链接即可。

### 方法二：本地服务器（同一 WiFi 下，最简单）

**Windows 用户：**
1. 双击 `start-server.bat` 文件
2. 脚本会自动显示你的 IP 地址和访问链接
3. 手机连接同一 WiFi，打开显示的链接即可

**Mac/Linux 用户：**
1. 在终端运行：`chmod +x start-server.sh && ./start-server.sh`
2. 脚本会自动显示你的 IP 地址和访问链接
3. 手机连接同一 WiFi，打开显示的链接即可

**手动启动（如果没有脚本）：**
```bash
# Python 3
python -m http.server 8000

# 或 Node.js
npx http-server -p 8000
```
然后查看电脑 IP 地址：
- Windows: `ipconfig` 查看 IPv4 地址
- Mac/Linux: `ifconfig` 或 `ip addr`
手机浏览器打开：`https://lilicen.github.io/kfc-v50/
### 方法三：使用内网穿透工具（推荐用于分享）
- **ngrok**：`ngrok http 8000`，会生成一个公网链接
- **localtunnel**：`npx localtunnel --port 8000`
- **frp**：需要自己搭建服务器

### 方法四：上传到云存储
- 阿里云 OSS / 腾讯云 COS：开启静态网站托管，绑定域名
- 七牛云 / 又拍云：上传文件，获取访问链接

## 移动端优化
- ✅ 已优化触摸区域（按钮最小 48px 高度）
- ✅ 响应式设计，自动适配手机屏幕
- ✅ 禁用点击高亮，提升体验
- ✅ 二维码自动缩放，手机扫码更方便

## 常见问题
- **图片不显示**：确认文件名/大小写正确且与 HTML 同级；强制刷新(Ctrl+F5)。
- **按钮链接**：默认跳转 `zhifu.html`，如需改成其他收款链接，修改 `index.html` 中 `paymentUrl` 变量即可。
- **手机无法访问**：检查防火墙是否允许 8000 端口，确保手机和电脑在同一 WiFi 网络。
- **二维码太小**：手机端会自动放大，长按二维码可保存到相册。

