<template>
  <section id="model-spec"
    class="bg-white py-24 px-6 relative border-t border-slate-100 font-sans antialiased">
    <div class="max-w-6xl mx-auto">
      <div class="mb-12 flex flex-wrap items-end justify-between gap-6">
        <div>
          <div class="w-12 h-1 bg-gradient-to-r from-miori-red to-miori-blue rounded-full mb-4"></div>
          <h2 class="text-4xl md:text-5xl font-bold text-miori-navy leading-none">3D Model</h2>
          <p class="text-xs text-slate-500 tracking-widest pt-3">キャラクターデザイン・3Dモデル</p>
        </div>
      </div>

      <p class="mb-6 text-sm text-slate-600 leading-loose">
        紺のジャージにヘッドホン。長い髪には赤い差し色が入っています。深瀬みおりのオリジナルアバターです。
      </p>

      <div class="model-switch" role="group" aria-label="設定画と3Dモデルの表示切り替え">
        <button v-for="view in views" :key="view.id" type="button"
          :aria-pressed="activeView === view.id" aria-controls="model-spec-panel"
          :class="{ 'is-active': activeView === view.id }" @click="activeView = view.id">
          {{ view.label }}
        </button>
      </div>

      <div id="model-spec-panel" class="model-panel" role="region" :aria-label="selectedView.description">
        <Transition name="model-fade" mode="out-in">
          <img :key="selectedView.id" :src="selectedView.src"
            :width="selectedView.width" :height="selectedView.height"
            loading="lazy" decoding="async" :alt="selectedView.description"
            class="w-full h-full object-contain" />
        </Transition>
      </div>

      <p class="mt-5 text-xs text-slate-500 leading-relaxed">キャラクター・モデル素材：オリジナル／自作</p>
    </div>
  </section>
</template>

<script setup lang="ts">
const views = [
  { id: 'model', label: 'モデル三面図', src: '/images/miori-views.webp', width: 2106, height: 1248, description: '深瀬みおりのモデル三面図' },
  { id: 'front', label: '正面', src: '/images/miori-front.webp', width: 810, height: 1440, description: '深瀬みおりの正面' },
  { id: 'right', label: '右側面', src: '/images/miori-right.webp', width: 810, height: 1440, description: '深瀬みおりの右側面' },
  { id: 'back', label: '背面', src: '/images/miori-back.webp', width: 810, height: 1440, description: '深瀬みおりの背面' },
  { id: 'design', label: 'イラスト三面図', src: '/images/miori-design.webp', width: 1672, height: 941, description: '深瀬みおりのイラスト三面図' },
] as const;
const activeView = ref<(typeof views)[number]['id']>('model');
const selectedView = computed(() => views.find(view => view.id === activeView.value) ?? views[0]);
</script>

<style scoped>
.model-switch {
  display: inline-flex;
  flex-wrap: wrap;
  gap: 4px;
  padding: 5px;
  margin-bottom: 20px;
  border: 1px solid var(--line);
  border-radius: 18px;
  background: var(--paper);
}
.model-switch button {
  min-height: 44px;
  padding: 10px 24px;
  border-radius: 999px;
  color: #526b83;
  font-size: 13px;
  font-weight: 700;
  transition: background-color .2s, color .2s;
}
.model-switch button:hover { color: var(--navy); }
.model-switch button.is-active { background: var(--navy); color: white; }
.model-panel {
  overflow: hidden;
  border: 1px solid var(--line);
  border-radius: var(--radius);
  background: white;
  height: clamp(360px, 54vw, 720px);
}
.model-fade-enter-active, .model-fade-leave-active { transition: opacity .18s ease; }
.model-fade-enter-from, .model-fade-leave-to { opacity: 0; }
@media (prefers-reduced-motion: reduce) {
  .model-switch button, .model-fade-enter-active, .model-fade-leave-active { transition: none; }
}
</style>
