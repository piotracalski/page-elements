<template>
  <div class="container-chunk">
    <div class="container-example" v-for="[width, height] in [[480, 300], [1000, 625], [1600, 1000]]" :key="width">
      <h2>{{ `Image - ${width}x${height}px` }}</h2>
      <Image
        :src="'/assets/example-image.jpg'"
        :alt="'A very nice image'"
        :title="'example image'"
        :width="width"
        :height="height"
        :renditions="state.renditions"
      />
    </div>
    <div class="container-example" v-for="width in [480, 1000, 1600]" :key="width">
      <h2>{{ `Image - no dimensions specified - small (${width}px)` }}</h2>
      <div :style="{width: `${width}px`}">
        <Image
          :src="'/assets/example-image.jpg'"
          :alt="'A very nice image'"
          :title="'example image'"
          :renditions="state.renditions"
          :breakpoints="state.breakpoints"
        />
      </div>
    </div>
  </div>
</template>

<script>
import { reactive, onMounted } from 'vue'
import Image from '../components/Image'
import { imageRenditions, layoutBreakpoints } from '../assets/base'

export default {
  name: 'ImageView',
  components: {
    Image
  },
  setup() {
    onMounted(() => {
    })

    const state = reactive({
      renditions: imageRenditions,
      breakpoints: layoutBreakpoints
    })

    return {
      state
    }
  }

}
      // :width="'400'"
      // :height="'250'"
</script>

<style lang="scss" scoped>
  .container-chunk {
    padding: 0;
  }
</style>