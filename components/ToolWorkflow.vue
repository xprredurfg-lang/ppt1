<script setup lang="ts">
import { ref } from 'vue'

const steps = [
  { n:'输入资料', tool:'DeepSeek', stop:'事实完整性' },
  { n:'结构化', tool:'DeepSeek', stop:'根因证据充分性' },
  { n:'草稿', tool:'WPS', stop:'数值/条款一致性' },
  { n:'任务派发', tool:'飞书', stop:'责任人与截止日期' },
  { n:'闭环复盘', tool:'飞书+知识库', stop:'有效性验证' },
]
const idx = ref(0)
const next = () => { idx.value = Math.min(idx.value + 1, steps.length - 1) }
</script>
<template>
  <div class="glass-card">
    <div style="display:flex;gap:10px;align-items:center;flex-wrap:wrap">
      <div v-for="(s,i) in steps" :key="s.n" :style="`padding:8px 10px;border-radius:10px;border:1px solid #3f5c95;background:${i<=idx?'#274168':'#0f1b31'};min-width:120px`">
        <div>{{ i+1 }}. {{ s.n }}</div>
        <small>{{ s.tool }}</small>
      </div>
    </div>
    <button style="margin-top:10px" @click="next">下一步</button>
    <p style="margin-top:8px">当前步骤：<b>{{ steps[idx].n }}</b><span class="stop-tag">停止点：{{ steps[idx].stop }}</span></p>
  </div>
</template>
