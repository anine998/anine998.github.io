# NINE Portfolio V2（独立中文版）

公开网站：https://anine998.github.io/portfolio-v2/

编辑管理：https://anine998.github.io/portfolio-v2/admin/

原版网站（保持原样）：https://anine998.github.io/

## 架构

- `index.html`：公开互动作品集（所有访客只读）
- `content.json`：可编辑的首页、职业经历、商业案例、AI/内容制作及游戏研究信息
- `admin/index.html`：GitHub 权限验证后可保存文字并上传图片
- `assets/uploads/`：通过管理页上传的图片存放目录（首次上传后自动创建）

## 如何编辑文字与图片

1. 登录 GitHub 的 `anine998` 账号。
2. 在 GitHub 的 Settings → Developer settings → Personal access tokens → Fine-grained tokens 创建短期有效的令牌。Repository access 仅选择 `anine998.github.io`，Repository permissions 仅赋予 **Contents: Read and write**（Metadata 由 GitHub 默认附加）。
3. 打开 `/portfolio-v2/admin/`，将令牌粘贴到权限验证输入框。请勿发送令牌给任何人，尤其不要写进仓库或聊天记录。
4. 修改首页文字、职业和日本经历、项目详细说明。项目封面或中央头像可以填写 `https://` 图片链接，也可以在网页上传 JPG/PNG/WebP/GIF，建议每张不超过 5MB。
5. 点击**保存并发布到 GitHub**。页面会向 GitHub Contents API 提交到仓库 `main` 分支。随后 GitHub Pages 会在完成构建后自动更新公开站。
6. 管理令牌只存在当前网页的 JavaScript 内存中，不使用 cookie、localStorage 或 sessionStorage 持久保存；刷新或关闭页面后需要重新输入。

## 授权与安全模型

- 公开页面本身和管理页面的前端代码都可以被访问；**编辑权不是依靠隐藏管理 URL**，而是靠 GitHub 身份和 GitHub 仓库写入权限控制。
- 管理页只接受 GitHub 当前用户 `anine998`，同时尝试检查 GitHub 返回的仓库 `permissions.push`。无论前端判断如何，GitHub API 都会在每次提交时校验令牌权限。
- GitHub Pages 是静态站点，没有自己的账号密码系统。若想改成普通 GitHub OAuth 登录（不用粘贴访问令牌），需要额外部署 OAuth 后端或 GitHub App，不能仅靠纯静态 HTML 安全实现。
- 所有修改可在仓库提交历史里追踪和回滚。
- 建议定期撤销闲置访问令牌，不给令牌扩大授权范围。

## 公开内容审核

用户上传的旧 PPT 和 PDF 中包含历史商业数据。已经把内部数字保留在研究依据中，但公开站首版只展示可以清楚说明职责的概述。发布实际数字、明星图片、内部报表前，需要自行确认对外披露和图像使用权限。

## 编辑原则

- 不直接把带整页中文说明的 PPT 截图作为项目主图。
- 项目封面只存视觉素材；标题、时间、职责、结果等都由 JSON 和页面 HTML 动态渲染，便于后续国际化。
- 保留原站（根目录 `index.html` 不变），所有新版开发放在 `portfolio-v2/`。