---
theme: default
ratio: 16/9
title: V4_AI_LLM_Agent_Training
mdc: true
drawings:
  persist: false
transition: fade
layout: cover
class: text-center
fonts:
  sans: 'Inter, PingFang SC, Microsoft YaHei, sans-serif'
colorSchema: dark
css: ./theme/custom.css
toc: true
---

# AI/LLM/Copilot/Agent
### DeepSeek × 飞书 × WPS 制造质量可落地版

<div class="deck-subtitle">面向制造质量部门内训｜可落地、可审计、可追责</div>

::notes::
- 开场明确目标：不是概念科普，而是可落地执行。
- 强调“证据链+停止点”是课程主线。

---
# 课程结构与学习目标

<div class="grid-3">
<div class="glass-card"><h3>资产 1：全局 Prompt</h3><p>统一角色、目标、约束、输出格式。</p></div>
<div class="glass-card"><h3>资产 2：证据链模板</h3><p>结论｜依据｜不确定，输出天然可复核。</p></div>
<div class="glass-card"><h3>资产 3：4条工作流</h3><p>异常快报、周报、8D、审核整改闭环。</p></div>
</div>

::notes::
- 说明课程是“拿来就用型”。
- 每一部分都对应后续实操页面。

---
# 为什么 LLM 特别适合制造质量部门

<div class="grid-3">
<div class="glass-card"><h3>文本密集</h3><p>SOP、检验记录、8D、审核报告高度文本化。</p></div>
<div class="glass-card"><h3>证据链驱动</h3><p>每个结论都需来源可追溯，LLM适合结构化归纳。</p></div>
<div class="glass-card"><h3>对齐成本高</h3><p>跨班组、跨供应商口径不一，LLM可标准化表达。</p></div>
</div>

---
# 一张图讲清：AI → GenAI → LLM → Copilot → Agent

<div class="glass-card">
<p><b>AI</b>：规则/统计学习总称 → <b>GenAI</b>：生成文本/图像/代码 → <b>LLM</b>：大规模语言模型</p>
<p><b>Copilot</b>：人机协作副驾（人主导） → <b>Agent</b>：目标驱动执行体（可调用工具）</p>
<p class="deck-subtitle">质量部实践建议：先Copilot，再Agent，始终保留人工停止点。</p>
</div>

---
# LLM 如何回答问题（token→概率→逐步生成）

<TokenSimulator />

::notes::
- 通过温度滑杆解释“稳定性 vs 发散性”。
- 说明模型并非“理解真理”，而是“概率生成最可能下一个token”。

---
# Transformer / 注意力的通俗解释

<div class="grid-2">
<div class="glass-card"><h3>像“开卷关联检索”</h3><p>每个词都会看全句，决定关注哪些上下文。</p></div>
<div class="glass-card"><h3>擅长长文本与结构化</h3><p>注意力让模型能跨段落关联条款、数字、责任主体。</p></div>
</div>
<div class="glass-card" style="margin-top:10px">示意：问题词 ⇄ 关键证据句（权重更高）</div>

---
# Prompt 为什么有效：本质是收窄自由度

<PromptAnatomy />

::notes::
- 给模型“角色/目标/输入/约束/输出”就是在降低自由度。
- 自由度越低，结果越可预测、越可审计。

---
# Prompt 高级技巧

<div class="grid-3">
<div class="glass-card"><h3>两段式</h3><p>先出大纲，再逐段填充，减少跑偏。</p></div>
<div class="glass-card"><h3>缺口问题</h3><p>要求模型先提“还缺什么信息”。</p></div>
<div class="glass-card"><h3>三列表</h3><p>结论｜依据｜不确定，默认可复核结构。</p></div>
</div>

---
# 风险与红线

<div class="grid-2">
<div class="glass-card"><ul><li>幻觉：无依据但语气自信</li><li>条款/数字错误</li><li>责任归属模糊</li></ul></div>
<div class="glass-card"><ul><li>提示注入攻击</li><li>越权访问与数据泄露</li><li>对外材料必须人工复核<span class="stop-tag">停止点</span></li></ul></div>
</div>

::notes::
- 强调“对外发布、客户沟通、合规承诺”必须人工签核。

---
# 把输出变可信：引用 / 未知 / 再验证

<div class="three-col">
<div><h3>结论</h3><p>给出可执行建议与优先级。</p></div>
<div><h3>依据</h3><p>明确来源：文件、章节、页码、时间戳。</p></div>
<div><h3>不确定/需验证</h3><p>列出缺失数据与验证动作。</p></div>
</div>
<div class="glass-card" style="margin-top:10px">复核清单：数字一致性｜条款匹配｜责任人｜截止时间｜验证证据</div>

---
# 部门“全局 Prompt”与停止点

<div class="glass-card">
<p>你是制造质量审核助手。目标：输出可审计的整改建议。输入：异常描述、检测数据、历史8D。约束：必须引用来源；未知项标注待验证；涉及责任与对外承诺必须人工确认。输出：结论｜依据｜不确定。</p>
<p><span class="stop-tag">停止点</span> 根因是否有证据？措施有效性如何验证？责任归属是否明确？关键数值是否复核？</p>
</div>

::notes::
- 建议把全局Prompt放到部门知识库作为默认模板。

---
# 自定义知识库与 RAG：搭建方法与治理

<RagFlow />

::notes::
- 治理四件套：范围、版本、权限、评测。

---
# DeepSeek 在质量部怎么用：三步法

<div class="grid-3">
<div class="glass-card"><h3>1. 事实</h3><p>先喂原始记录，不做推断。</p></div>
<div class="glass-card"><h3>2. 缺口</h3><p>让模型列出缺失证据与待补数据。</p></div>
<div class="glass-card"><h3>3. 草稿</h3><p>按三列表输出可审阅初稿。</p></div>
</div>
<div class="glass-card" style="margin-top:8px">推荐输出格式：摘要（100字）+ 风险等级 + 行动清单（负责人/期限）</div>

---
# WPS AI 能带来什么突破

<div class="grid-3">
<div class="glass-card"><h3>文档</h3><p>周报自动整理、术语统一。</p></div>
<div class="glass-card"><h3>表格</h3><p>异常数据汇总、趋势说明自动生成。</p></div>
<div class="glass-card"><h3>PPT</h3><p>周报→一页解读→汇报稿快速成型。</p></div>
</div>

---
# 飞书 AI / 妙记 / 任务 / 知识库闭环

<div class="grid-2">
<div class="glass-card"><h3>会议到任务</h3><p>妙记提炼纪要 → 自动待办 → 指派责任人。</p></div>
<div class="glass-card"><h3>权限与留痕</h3><p>知识库分级授权，操作日志可追踪。</p></div>
</div>

---
# 4条可复制工作流（DeepSeek × WPS × 飞书）

<ToolWorkflow />

::notes::
- 强调每一步都要有“停止点”，不是全自动放行。

---
# 业务场景案例清单（今天就能用）

<div class="grid-2">
<div class="glass-card"><ol><li>来料异常快报</li><li>班组质量周报</li><li>8D初稿</li><li>审核不符合项整改</li><li>供应商沟通函</li></ol></div>
<div class="glass-card"><ol start="6"><li>客户投诉复盘</li><li>检验标准对照表</li><li>重复缺陷预警</li><li>培训题库生成</li><li>质量月报管理层摘要</li></ol></div>
</div>

---
# Agent 展望与 90 天路线图

<AgentTimeline />

::notes::
- 先试点再扩面，指标达成后再进入下一阶段。
