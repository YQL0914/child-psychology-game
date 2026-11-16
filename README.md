# 儿童心理游戏-情绪探险岛 · child-psychology-game Emotion Island

和森林里的小伙伴一起认识感受，练习应对。暂面向 6—10 岁儿童与陪伴者设计，原生静态网页，无依赖、无账号、不上传儿童选择。

[在线体验](https://yql0914.github.io/child-psychology-game/) · [项目说明书](docs/项目说明书.md) · [源码仓库](https://github.com/YQL0914/child-psychology-game)

**心理教育原型，非诊断或治疗服务。** 已有方法研究不能证明本产品有效。尚未完成有资质人员的逐句审核、儿童可用性试用和临床验证。年龄与体验时长不是确证适用范围。

## 已实现

- 三个完整故事：加入同伴游戏、积木倒下、日常玩耍后的告别。
- 六步可跳过导览，多选感受与身体信号、应对反馈、回顾、线下自愿练习。
- 家长陪伴指南、理论来源及限制、使用说明和隐私页。
- 三张本地故事插图、SVG 表情脸、参考页面的浅青与深蓝配色、大字大按钮、响应式布局、键盘操作、减少动态偏好支持。
- 选择只在页面内存保留；退出、刷新或切换故事清空。跳过清空该步，返回上一步保留本关选择。

## 本地运行

使用 Python 3 启动静态服务（ES modules 需要 HTTP，不能直接双击 HTML）：

```sh
python -m http.server 4173 --bind 127.0.0.1
```

浏览器打开 <http://127.0.0.1:4173> 。Node 24+ 用于检查，无需 npm install：

```sh
npm test
npm run check
```

可选真实浏览器回归检查（需已有 Playwright 和 Chrome，不属于产品运行依赖）：

```sh
node tests/browser-check.mjs
```

若 Playwright 不在本项目模块查找路径，可通过 `PLAYWRIGHT_MODULE` 指定已有安装的 `index.mjs` 绝对路径；`PREVIEW_URL` 可覆盖默认预览地址。截图保存在已忽略的 `screenshots/`。本机若全局 `npm` 命令损坏，可直接运行 `node --test tests/game.test.mjs`，或使用 Node 安装目录中的 `npm.cmd`。

## 发布 GitHub Pages

本项目已使用 **GitHub Pages** 发布，采用 **Deploy from a branch** 方式，无须创建 GitHub Release，也无须单独部署服务器。

- **在线体验**：[情绪探险岛](https://yql0914.github.io/child-psychology-game/)
- **源码仓库**：[YQL0914/child-psychology-game](https://github.com/YQL0914/child-psychology-game)
- **当前发布设置**：仓库 **Settings → Pages → Build and deployment**，Source 为 `Deploy from a branch`，Branch 为 `main`，Folder 为 `/(root)`。

后续更新操作：

1. 将代码、页面和 `assets/` 等资源按原有目录结构提交至 `main` 分支。
2. GitHub Pages 根据 `main` 分支根目录中的文件自动构建和部署，无需每次手动点击发布，也不需要创建 Release。
3. 在仓库 **Settings → Pages** 查看部署状态，发布完成后打开上面的在线体验链接验证。
4. 修改涉及图片或脚本时，重点检查 `assets/stories/` 资源是否正常加载、三个故事的交互流程及手机端布局；如浏览器仍显示旧内容，可强制刷新后再测试。

> 说明：当前采用的是分支发布方式，仓库中的文档和测试文件并不会因使用 GitHub Pages 而自动从发布源中排除。若日后希望仅发布筛选后的静态文件，可再考虑切换到 GitHub Actions 构建发布。

项目说明书记录了 **2026-11-11** 的上线检查情况，详见[项目说明书的上线检查记录](docs/项目说明书.md#九上线检查记录)。该历史记录不替代每次更新后的在线功能回归检查。

### 版本发布说明

GitHub Pages 用于提供可直接访问的在线游戏；GitHub Release 主要用于标记可下载的版本，**不是网站上线的必需步骤**。当前仍属于心理教育原型阶段，可先持续迭代。日后如需在作品集中标记稳定的原型版本，可按实际完成情况创建 `v0.1.0` 等版本标签，并写明验证范围与已知限制。

## 文件

- `game.js`：故事内容、纯状态逻辑。
- `app.js`：页面路由、交互和内容呈现。
- `art.js`、`styles.css`：图片呈现、SVG 表情和植物、界面样式。
- `assets/stories/`：使用内置图像工具生成的三张故事插图；[完整提示词与素材记录](assets/README.md)。
- `tests/game.test.mjs`：内容完整性和状态边界检查。
- [文献与内容审核](docs/content-evidence-review.md)：来源、证据边界、上线内容门槛。
- [设计文档](docs/superpowers/specs/2026-11-11-emotion-island-design.md)。

## 内容与隐私边界

不根据情绪选择、作品或身体信号诊断；不要求披露真实经历；没有情绪排名或打卡奖惩。没有外部字体、统计脚本、API 或存储。普通网站访问日志由托管平台管理，点击外部研究链接适用第三方隐私政策。
家长不应强迫儿童完成。困扰持续影响生活时建议专业评估，有即时危险优先寻求现实中的保护和紧急帮助。

## 许可

代码、原创插画和原创文案采用 [MIT](LICENSE)。外部文章、论文、机构名称及其材料不属于本项目授权范围；本项目不包含复制的课程或量表，不暗示相关机构认可产品。
