<!--
  cover — title slide, section breaks, mood/transition moments.
  Full-bleed photo via `background:` frontmatter + a scrim for contrast + one line.
  Add `class: grayscale` to desaturate the photo.
-->
<script setup lang="ts">
import { computed } from 'vue'

const props = defineProps<{ background?: string }>()

function resolveAssetUrl(url: string) {
  if (url.startsWith('/'))
    return import.meta.env.BASE_URL + url.slice(1)
  return url
}

const bgStyle = computed(() =>
  props.background
    ? { backgroundImage: `url("${resolveAssetUrl(props.background)}")` }
    : {},
)
</script>

<template>
  <div class="slidev-layout mono-cover">
    <div class="mono-cover__bg" :style="bgStyle" />
    <div class="mono-cover__scrim" />
    <div class="mono-cover__content">
      <slot />
    </div>
  </div>
</template>
