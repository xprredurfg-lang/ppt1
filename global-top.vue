<script setup lang="ts">
import { onMounted, onUnmounted, ref, watch } from 'vue'

const lowPerf = ref(false)
const canvasRef = ref<HTMLCanvasElement | null>(null)
let raf = 0
let particles: Array<{x:number;y:number;vx:number;vy:number}> = []

const draw = () => {
  const canvas = canvasRef.value
  if (!canvas || lowPerf.value) return
  const ctx = canvas.getContext('2d')
  if (!ctx) return
  const { width, height } = canvas
  ctx.clearRect(0, 0, width, height)
  particles.forEach((p) => {
    p.x += p.vx
    p.y += p.vy
    if (p.x < 0 || p.x > width) p.vx *= -1
    if (p.y < 0 || p.y > height) p.vy *= -1
    ctx.beginPath()
    ctx.arc(p.x, p.y, 1.5, 0, Math.PI * 2)
    ctx.fillStyle = 'rgba(76,243,255,0.5)'
    ctx.fill()
  })
  raf = requestAnimationFrame(draw)
}

onMounted(() => {
  const canvas = canvasRef.value
  if (!canvas) return
  const resize = () => {
    canvas.width = window.innerWidth
    canvas.height = window.innerHeight
  }
  resize()
  window.addEventListener('resize', resize)
  particles = Array.from({ length: 45 }).map(() => ({
    x: Math.random() * window.innerWidth,
    y: Math.random() * window.innerHeight,
    vx: (Math.random() - 0.5) * 0.4,
    vy: (Math.random() - 0.5) * 0.4,
  }))
  draw()
  onUnmounted(() => {
    window.removeEventListener('resize', resize)
    cancelAnimationFrame(raf)
  })
})

watch(lowPerf, (v) => {
  document.documentElement.classList.toggle('low-motion', v)
  if (v) {
    cancelAnimationFrame(raf)
    const ctx = canvasRef.value?.getContext('2d')
    if (ctx && canvasRef.value) ctx.clearRect(0, 0, canvasRef.value.width, canvasRef.value.height)
  } else {
    draw()
  }
})
</script>

<template>
  <canvas ref="canvasRef" style="position:fixed; inset:0; pointer-events:none; z-index:0; opacity:0.45" />
  <button
    style="position:fixed;top:12px;right:20px;z-index:99;font-size:12px;padding:6px 10px;border-radius:999px;background:#1d2f4f;border:1px solid #4cf3ff55;color:#cde8ff"
    @click="lowPerf = !lowPerf"
  >
    {{ lowPerf ? '低配模式：开' : '低配模式：关' }}
  </button>
</template>
