<!--
  image-right — mirror of image-left. Photo right, ≤4 short lines left.
  Photo via `image:` frontmatter; add `class: grayscale` to desaturate.
-->
<script setup lang="ts">
import { computed } from 'vue'

const props = defineProps<{ image?: string }>()

function resolveAssetUrl(url: string) {
  if (url.startsWith('/'))
    return import.meta.env.BASE_URL + url.slice(1)
  return url
}

const mediaStyle = computed(() =>
  props.image
    ? { backgroundImage: `url("${resolveAssetUrl(props.image)}")` }
    : {},
)
</script>

<template>
  <div class="slidev-layout mono-split">
    <div class="mono-split__body">
      <slot />
    </div>
    <div class="mono-split__media" :style="mediaStyle" />
  </div>
</template>
