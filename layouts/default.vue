<template>
  <div class="max-w-3xl w-full mx-auto px-8 pt-32">
    <div class="pb-64 text-center">
      <NuxtLink v-for="page in pages" :key="page" :to="page" class="underline mx-4">
        {{ page }}
      </NuxtLink>
    </div>
    <Nuxt />

    <div
      class="fixed left-0 w-full h-0 border-t-2 border-dashed border-black"
      :style="{ top: triggerTop + 'px' }"
    >
      <p>Offset: {{ offset }}</p>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      pages: ['Basic', 'Progress', 'StickyGraphic1', 'StickyGraphic2'],
      triggerTop: 0,
      offset: 0.6
    }
  },
  mounted () {
    window.addEventListener('resize', this.handleResize)
    this.handleResize()
  },
  methods: {
    handleResize () {
      this.triggerTop = this.offset * window.innerHeight
    }
  }
}
</script>
