<template>
  <div class="container-chunk">
    <h2>Image - 480x300px - renditions set</h2>
    <Image
      :src="'/assets/example-image.jpg'"
      :alt="'A very nice image'"
      :title="'example image'"
      :width="'480'"
      :height="'300'"
      :renditions="state.renditions"
    />
    <h2>Image - 1000x625px - renditions set</h2>
    <Image
      :src="'/assets/example-image.jpg'"
      :alt="'A very nice image'"
      :title="'example image'"
      :width="'1000'"
      :height="'625'"
      :renditions="state.renditions"
    />
    <h2>Image - 1600x1000px - renditions set</h2>
    <Image
      :src="'/assets/example-image.jpg'"
      :alt="'A very nice image'"
      :title="'example image'"
      :width="'1600'"
      :height="'1000'"
      :renditions="state.renditions"
    />
  </div>
</template>

<script>
import { reactive } from 'vue'
import Image from '../components/Image'

export default {
  name: 'ImageView',
  components: {
    Image
  },
  setup() {
    const state = reactive({
      standardImageWidth: '',
      renditions: [
        {width: 1920, height: 1200},
        {width: 1200, height: 750},
        {width: 768, height: 480}
      ]
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