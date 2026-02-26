<script setup lang="ts">
import { ref } from 'vue'

const phases = [
  { t:'0-30天', d:'选2条流程试点，沉淀全局Prompt与复核清单', r:'避免全员铺开', k:'周报周期缩短30%' },
  { t:'30-60天', d:'接入RAG知识库与权限分层', r:'版本漂移与越权', k:'引用准确率>90%' },
  { t:'60-90天', d:'Agent自动流转+任务闭环看板', r:'责任归属模糊', k:'整改闭环时长下降20%' },
]
const active = ref(0)
</script>
<template>
  <div class="glass-card">
    <div style="display:flex;gap:12px">
      <div v-for="(p,i) in phases" :key="p.t" @click="active=i" :style="`cursor:pointer;flex:1;padding:8px;border-radius:10px;border:1px solid #4d6da8;background:${active===i?'#29466f':'#13213a'}`">
        <strong>{{ p.t }}</strong>
      </div>
    </div>
    <div style="margin-top:10px">
      <p><b>交付物：</b>{{ phases[active].d }}</p>
      <p><b>风险控制：</b>{{ phases[active].r }}</p>
      <p><b>验收指标：</b>{{ phases[active].k }}</p>
    </div>
  </div>
</template>
