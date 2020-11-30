<template>
  <div class="base-image">
    <picture>
      <source>
      <img
        :src="src"
        :alt="alt"
        :title="title"
        :width="width"
        :height="height"
      />
    </picture>
  </div>
</template>

<script>
export default {
  name: "Image",
  props: {
    src: {
      type: String,
      required: true
    },
    height: {
      type: String,
      required: true
    },
    width: {
      type: String,
      required: true
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
    }
  },
  mounted() {
    console.log(this.renditions)
  }
}
</script>

<style lang="scss" scoped>
  .base-image {
    padding: 0;

    img {
      display: block;
    }
  }
</style>