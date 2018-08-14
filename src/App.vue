<template>
  <div id="app">

    <div class="image-box">

      <VueImageInputPreview>

        <div slot="template" slot-scope="{chooseImage, image_src, fileName}" class="body">
          <img class="image" :src=image_src alt="file" v-if="image_src">
          <input type="file" accept="image/*" class="input" name="file" @change="chooseImage">
        </div>

      </VueImageInputPreview>
    </div>

  </div>
</template>

<script>
import VueImageInputPreview from './components/VueImageInputPreview.vue'

export default {
  name: 'app',
  components: {
    VueImageInputPreview
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  /*color: #2c3e50;*/
  margin-top: 60px;
}
  .image-box {
    width: 300px;
    height: 200px !important;
  }
</style>
