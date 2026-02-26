<script setup lang="ts">
import { ref } from 'vue'

const parts = [
  { key: 'Role', text: '你是制造质量审核助手', why: '固定角色降低表达漂移' },
  { key: 'Goal', text: '目标：输出可审计的整改建议', why: '明确成功标准，避免空泛建议' },
  { key: 'Input', text: '输入：异常描述、检测数据、历史8D', why: '限定信息边界，减少臆测' },
  { key: 'Constraints', text: '约束：必须引用来源，未知项标注待验证', why: '直接抑制幻觉与责任不清' },
  { key: 'Output', text: '输出：结论/依据/不确定 三列表', why: '结构化输出便于评审与追责' },
]
const active = ref(parts[0].key)
</script>

<template>
  <div class="grid-2">
    <div class="glass-card">
      <div v-for="p in parts" :key="p.key" @mouseenter="active = p.key" :style="`padding:8px;border-radius:8px;margin-bottom:6px;cursor:pointer;${active===p.key?'background:#243759':'':''}`">
        <strong>[{{ p.key }}]</strong> {{ p.text }}
      </div>
    </div>
    <div class="glass-card">
      <h4>{{ active }} 为什么让输出更稳？</h4>
      <p>{{ parts.find(p => p.key === active)?.why }}</p>
    </div>
  </div>
</template>
