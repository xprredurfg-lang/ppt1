<script setup lang="ts">
import { computed, ref } from 'vue'

const question = ref('如何降低8D报告反复退回率？')
const generated = ref('')
const temperature = ref(0.7)
const bank = ['建议', '先', '统一', '证据链', '模板', '并', '设置', '停止点', '复核', '机制', '。']

const candidates = computed(() => {
  const base = ['建议', '可', '先', '通过', '建立', '统一', '模板', '并', '执行', '复核']
  return base.map((t, i) => {
    const sharp = Math.max(0.05, 1 - temperature.value)
    const raw = Math.abs(Math.sin(i + 1 + temperature.value * 3)) * (0.7 + sharp)
    return { token: t, prob: Math.round(raw * 100) }
  }).sort((a, b) => b.prob - a.prob).slice(0, 6)
})

function nextToken() {
  if (generated.value.length > 32) return
  const idx = Math.floor(Math.random() * Math.max(1, Math.round(temperature.value * bank.length)))
  generated.value += (generated.value ? '' : '') + bank[idx]
}

function reset() { generated.value = '' }
</script>

<template>
  <div class="glass-card">
    <div>输入问题：<input v-model="question" style="width:70%;background:#0f1a2f;border:1px solid #2b4269;border-radius:8px;padding:4px 8px"></div>
    <div style="margin-top:8px">Temperature: {{ temperature.toFixed(1) }}
      <input v-model="temperature" type="range" min="0.1" max="1.2" step="0.1" style="width:220px;margin-left:8px"/>
    </div>
    <div style="margin-top:8px">
      <button @click="nextToken" style="margin-right:8px">生成下一 token</button>
      <button @click="reset">重置</button>
    </div>
    <div style="margin-top:8px;color:#9ed9ff">输出：{{ generated || '（点击开始生成）' }}</div>
    <div v-for="c in candidates" :key="c.token" style="display:flex;align-items:center;gap:8px;margin-top:4px">
      <span style="width:56px">{{ c.token }}</span>
      <div style="height:8px;background:#1f2a43;flex:1;border-radius:99px"><div :style="`width:${c.prob}%;height:100%;background:#4cf3ff;border-radius:99px`"></div></div>
      <span>{{ c.prob }}%</span>
    </div>
  </div>
</template>
