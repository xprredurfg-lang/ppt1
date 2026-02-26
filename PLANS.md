# ExecPlan

## M1 项目初始化
- 目标：搭建 Slidev 项目骨架、目录结构、脚本入口。
- 验收点：`npm run dev` 可启动，存在 `tools/ components/ theme/ public/ slides.md README.md PLANS.md`。
- 自测：`npm install`、`npm run dev -- --help`（或启动日志检查）。

## M2 主题与视觉系统
- 目标：实现暗色科技风主题、统一卡片栅格、低配模式开关。
- 验收点：全局背景/卡片样式生效；支持关闭粒子与动效。
- 自测：`npm run dev` 本地预览每页样式一致。

## M3 内容生成
- 目标：实现 `tools/docx_to_slidev.py`，支持 docx/txt fallback，输出 Slidev markdown。
- 验收点：可从 `./source/V4.docx` 或 `./source/V4.txt` 生成 `slides.md`；支持“Slide X｜标题”与标题分段。
- 自测：运行脚本后 `slides.md` 为 16-20 页。

## M4 交互组件
- 目标：完成 Token 模拟器、Prompt 解剖器、RAG 流程、三工具工作流、Agent 时间线。
- 验收点：5 个组件可点击交互、无控制台报错。
- 自测：`npm run dev` 手动点击检查。

## M5 性能与离线
- 目标：离线资源可用，构建产物可静态部署。
- 验收点：`npm run build` 成功，`dist/` 产物可 `npm run preview`。
- 自测：执行 build/preview，确认无外链依赖。

## M6 文档与验收
- 目标：完善 README（使用说明、低配模式、脚本说明），完成最终提交。
- 验收点：README 说明完整；git commit + PR 信息齐备。
- 自测：`npm run build` 最终复验。
