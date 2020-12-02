<template>
  <div class="base-image" ref="root" :style="{width: width + 'px', height: height + 'px'}">
    <!-- <picture>
      <source media="(max-width: 767px)" srcset="/assets/example-image-rendition-768-480.jpg">
      <source media="(min-width: 768px)" srcset="/assets/example-image-rendition-1200-750.jpg">
      <source media="(min-width: 1200px)" srcset="/assets/example-image-rendition-1920-1200.jpg">
      <img ref="image"
        :alt="alt"
        :title="title"
      />
    </picture> -->
    <!-- <div><p v-for="rendition in renditions" :key="rendition.width">{{ `rendition - width: ${rendition.width}, height: ${rendition.height}` }}</p></div> -->
    <picture>
      <img ref="image"
        :alt="alt"
        :title="title"
      />
    </picture>
  </div>
</template>

<script>
import { ref, onMounted } from 'vue'

export default {
  name: "Image",
  props: {
    src: {
      type: String,
      required: true
    },
    height: {
      type: String,
      required: false
    },
    width: {
      type: String,
      required: false
    },
    title: {
      type: String,
      required: true
    },
    alt: {
      type: String,
      required: true
    },
    renditions: {
      type: Array,
      required: false
    },
    breakpoints: {
      type: Array,
      required: false
    }
  },
  setup(props) {
    const root = ref(null)
    const image = ref(null)
    function renditionIntervals (renditions) {
      return renditions.map(rendition => rendition.width)
        .slice()
        .sort((a, b) => a - b)
        .map((cur, index, array) => index === 0 ? [0, cur] : [array[index - 1], cur])
    }
    
    function getRenditionWidth (intervals) {
      const interval = intervals.filter(interval => props.width > interval[0] && props.width <= interval[1])
      return interval.length > 0 ? interval[0][1] : Math.max(...props.renditions.map(rendition => rendition.width))
    }

    function getRenditionHeight (renditions, renditionWidth) {
      return renditions.filter(rendition => rendition.width === renditionWidth)[0].height
    }

    function getRenditionSrc(width, height) {
      let originalImage = props.src.split('.')
      return `${originalImage[0]}-rendition-${width}-${height}.${originalImage[1]}`
    }

    onMounted(() => {
      if (props.width) {
        console.log(`width is set to: ${props.width}`)
        const renditionWidth = getRenditionWidth(renditionIntervals(props.renditions))
        const renditionHeight = getRenditionHeight(props.renditions, renditionWidth)
        image.value.width = props.width
        image.value.height = props.height
        image.value.src = getRenditionSrc(renditionWidth, renditionHeight)
      } else {
        console.log('width is not set')
        const rootWidth = root.value.offsetWidth
        image.value.width = rootWidth
        image.value.src = props.src
      }
    })

    return {
      root,
      image
    }
  }
}

// DONE jeśli podana jest width to renditiony na podstawie tego propertiesu 
// jeśli nie są podane to renditiony na podstawie computed width parent node + ustawienie width img = width parent node
  // DONE get width of parent node
  // DONE set width of image to parent nodes width
  // DONE height should compensate
  // provide renditions - VERY EASY :) 
</script>

<style lang="scss" scoped>
  .base-image {
    padding: 0;

    img {
      display: block;
    }
  }
</style>

