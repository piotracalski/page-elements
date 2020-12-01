<template>
  <nav>
    <div class="container-main">NAVIGATION</div>
  </nav>
  <section>
    <div class="container-main">
      <ImageView />
    </div>
  </section>
  <footer>
    <div class="container-main">FOOTER</div>
  </footer>
</template>

<script>
import ImageView from './views/ImageView'

export default {
  name: 'App',
  components: {
    ImageView
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 30px;
  padding: 50px;
  display: flex;
  flex-direction: column;

  .container-main {
    box-sizing: border-box;
    width: 100%;
    height: 100%;
    margin-bottom: 50px;
    padding: 10px;
    background-color: #3b444d;
    color: #aeb6be;
    overflow: hidden;

    h2 {
      font-size: 18px;
    }
  }
}
</style>
