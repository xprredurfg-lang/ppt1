<script setup lang="ts">
import { ref } from 'vue'

const nodes = [
  { id:'检索', detail:'按问题检索SOP/8D/检验记录', risk:'召回不足', gov:'建立版本标签+召回评测' },
  { id:'拼接', detail:'将片段按来源拼接上下文', risk:'噪声过多', gov:'限制chunk与重排' },
  { id:'生成', detail:'基于上下文草拟答案', risk:'过度推断', gov:'要求未知项声明' },
  { id:'引用', detail:'输出文件名/章节/页码', risk:'引用错位', gov:'引用粒度最小到段落' },
  { id:'复核', detail:'人工复核责任/数字/条款', risk:'遗漏停止点', gov:'复核清单签名留痕' },
]
const current = ref(nodes[0])
</script>
<template>
  <div class="glass-card">
    <div style="display:flex;gap:8px;flex-wrap:wrap;margin-bottom:10px">
      <button v-for="n in nodes" :key="n.id" @click="current = n" :style="`padding:6px 10px;border-radius:999px;border:1px solid #3d5a91;background:${current.id===n.id?'#2a436c':'#131f34'}`">{{ n.id }}</button>
    </div>
    <div class="grid-3">
      <div><h4>做法</h4><p>{{ current.detail }}</p></div>
      <div><h4>风险</h4><p>{{ current.risk }}</p></div>
      <div><h4>治理要点</h4><p>{{ current.gov }}</p></div>
    </div>
    <p style="margin-top:8px;color:#9bc7ff">引用示例：`《来料检验规范V3》/ 4.2 抽样规则 / p.12`</p>
  </div>
</template>
