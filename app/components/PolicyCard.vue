<template>
  <div class="rounded-3xl border border-slate-100 bg-slate-50/70 p-6">
    <h3 class="mb-4 flex items-center gap-2 font-black text-miori-navy">
      <i class="fa-solid fa-paw text-xs text-miori-blue" aria-hidden="true"></i>
      {{ title }}
    </h3>
    <ul class="list-disc space-y-2 pl-5 text-sm text-slate-500 marker:text-miori-blue">
      <slot />
    </ul>
  </div>
</template>

<script setup lang="ts">
defineProps<{
  title: string;
}>();
</script>
