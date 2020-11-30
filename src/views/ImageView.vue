<template>
  <div class="container-chunk">
    <h2>Image - aligned to the left side</h2>
    <Image
      :src="'/assets/example-image.jpg'"
      :alt="'A very nice image'"
      :title="'example image'"
      :width="'400'"
      :height="'250'"
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
      standardImageWidth: ''
    })

    return {
      state
    }
  }

}
</script>

<style lang="scss" scoped>
  .container-chunk {
    padding: 0;
  }
</style>