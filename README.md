# V4_AI_LLM_Agent_Training｜Slidev 网页版内训课件

面向制造质量部门的离线可演示 Web Slide Deck（16:9，暗色科技风）。

## 目录结构

- `部门内训PPT文字稿（V4重构版）_重新发送_2026-02-26.docx`：原始文档（可直接放根目录）
- `source/V4.docx` / `source/V4.txt`：脚本优先读取位置
- `tools/docx_to_slidev.py`：docx/txt 转 Slidev 的生成脚本
- `components/`：交互组件（A~E）
- `theme/custom.css`：全局视觉主题
- `public/`：静态资源
- `slides.md`：Slidev 主文件
- `PLANS.md`：执行计划与里程碑

## 如何放置 V4.docx / V4.txt

1. 推荐：放到 `source/V4.docx`
2. 如果 docx 读取失败，放 `source/V4.txt`
3. 兼容读取：仓库根目录中的 `部门内训PPT文字稿（V4重构版）_重新发送_2026-02-26.docx`

## 生成 slides.md

```bash
python3 tools/docx_to_slidev.py
```

脚本规则：
- 若检测到 `Slide X｜标题`：按 Slide 分割。
- 否则按标题特征智能分段。
- 输出为 Slidev 格式 `slides.md`。

## 启动 / 构建 / 预览

```bash
npm install
npm run dev
npm run build
npm run preview
```

## 低配模式（会议室设备优化）

- 演示右上角按钮 `低配模式：开/关`
- 开启后：关闭粒子背景与大部分动画过渡，提升流畅度。

## 交互组件清单

- `TokenSimulator.vue`：Token 生成模拟器（含 temperature）
- `PromptAnatomy.vue`：Prompt 解剖器
- `RagFlow.vue`：RAG 流程可视化
- `ToolWorkflow.vue`：DeepSeek→WPS→飞书流程
- `AgentTimeline.vue`：90天路线图交互时间线
