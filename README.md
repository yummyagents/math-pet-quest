# 三年级数学闯关 · 宠物救援

一个给三年级孩子练计算与算理的像素闯关小游戏。**纯静态单页，无需构建、无需服务器、无外部依赖**，丢到 GitHub Pages 上就能玩。

- 五关五种场景与玩法：水晶洞窟（碰水晶）→ 火山熔炉（踩泡泡）→ 沙漠神殿（跳够神灯）→ 机械工坊（顶齿轮箱）→ 夜晚城堡（BOSS 三连战）
- 答对救出宠物，收进 8 族图鉴；完全体宠物给护盾
- 1-3-7 复习阶梯：答对的题隔 1 天、3 天、7 天再考一次，连过三轮才算真会
- 进度保存在浏览器本地（localStorage），不上传任何数据

## 文件说明

| 文件 | 用途 | 必需 |
|---|---|---|
| `index.html` | 游戏本体（首页） | ✅ |
| `题库总览.html` | 给家长看的题库与玩法说明页 | 可选 |
| `.nojekyll` | 关闭 Jekyll 处理，避免 Pages 忽略特殊文件名 | ✅ 建议保留 |
| `可选-GitHub-Actions/pages.yml` | 想用 Actions 部署时用，默认不需要 | 可选 |

> `.nojekyll` 是个空文件，在 Finder 里默认看不到（按 `Cmd+Shift+.` 显示隐藏文件）。用网页上传时如果拖不进去，可以跳过它——本仓库没有 `_` 开头的目录，影响不大。

---

## 方法一：网页上传（最省事，推荐）

1. 打开 GitHub，右上角 **+ → New repository**
   - Repository name：`math-quest`（随你喜欢）
   - 可见性选 **Public**（Pages 免费版要求公开仓库）
   - 勾选 **Add a README file** → Create repository
2. 进入仓库 → **Add file → Upload files**
   - 把本目录里的 `index.html`、`题库总览.html`、`.nojekyll` 一起拖进去
   - 底部 **Commit changes**
3. 仓库页 → **Settings → Pages**
   - **Source** 选 `Deploy from a branch`
   - **Branch** 选 `main`，目录选 `/ (root)` → **Save**
4. 等 1～2 分钟刷新页面，顶部会出现你的网址：

```
https://<你的用户名>.github.io/math-quest/
```

打开即玩，手机/平板浏览器直接访问即可。

---

## 方法二：命令行（之后要频繁改动用这个）

```bash
cd github-deploy
git init -b main
git add .
git commit -m "三年级数学闯关 · 宠物救援"
git remote add origin https://github.com/<你的用户名>/math-quest.git
git push -u origin main
```

推送后仍按方法一第 3 步开启 Pages（只需开一次）。

---

## 方法三：GitHub Actions（可选）

如果想每次 push 自动发布：

```bash
mkdir -p .github/workflows
cp 可选-GitHub-Actions/pages.yml .github/workflows/pages.yml
git add .github && git commit -m "add pages workflow" && git push
```

然后 Settings → Pages → **Source** 改为 `GitHub Actions`。注意：Source 一旦选了 Actions，方法一的分支发布就失效了，二选一即可。

---

## 更新游戏内容

改完 `index.html` 后：

- 网页方式：进入文件 → 右上角铅笔图标编辑，或重新 Upload files 覆盖
- 命令行方式：`git add . && git commit -m "update" && git push`

推送后 1 分钟左右线上自动更新，**网址不变**。

## 几点提醒

- **进度存在浏览器里**：按域名隔离。孩子在同一台设备、同一浏览器里会一直积累图鉴；换设备、换浏览器、清缓存都会重置。
- **公开仓库**：任何人都能看到这两个文件。里面只有游戏和题库说明，没有孩子的姓名、学校、成绩等个人信息。如果不想公开，Private 仓库用 Pages 需要 GitHub Pro；免费替代方案是 Cloudflare Pages（支持私有仓库，免费）。
- **自定义域名**：Settings → Pages → Custom domain 填自己的域名，按提示加一条 CNAME 记录即可（国内访问 GitHub Pages 有时不稳定，自定义域名也解决不了线路问题）。
- 画面建议横屏，iPad / 平板体验最好。
