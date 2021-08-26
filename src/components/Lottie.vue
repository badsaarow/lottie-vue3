<script setup lang="ts">
import { onMounted, ref } from 'vue'
import lottie from 'lottie-web'

interface Props {
  options: any
  height?: string
  width?: string
}

const props = withDefaults(defineProps<Props>(), {
  height: '100%',
  width: '100%',
})

const emit = defineEmits(['animCreated'])
const style = {
  width: props.width,
  height: props.height,
  overflow: 'hidden',
  margin: '0 auto',
}

const aniContainer = ref<HTMLElement>()

onMounted(() => {
  const anim = lottie.loadAnimation({
    container: aniContainer.value as HTMLElement,
    renderer: 'svg',
    loop: !!props.options.loop,
    autoplay: !!props.options.autoplay,
    animationData: props.options.animationData,
    rendererSettings: props.options.rendererSettings,
  })
  emit('animCreated', anim)
})
</script>

<template>
  <div ref="aniContainer" :style="style"></div>
</template>
