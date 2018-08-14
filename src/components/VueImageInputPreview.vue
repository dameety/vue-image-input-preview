<template>
    <div class="vue-image-input-preview-container">
        <slot name="template" :chooseImage="chooseImage" :image_src="image_src" :fileName="fileName">

            <div class="body">
                <img class="image" :src=image_src alt="file" v-if="image_src">
                <input type="file" accept="image/*" class="input" name="file" @change="chooseImage">
            </div>

        </slot>
    </div>
</template>

<script>
    /* eslint-disable */
  export default {
    name: 'VueImageInputPreview',

      data () {
          return {
              image_src: null,
              fileInput: '',
              fileName: ''
          }
      },

      methods: {
          chooseImage (e) {
              let files = e.target.files;

              if(files.length === 0) {
                  this.image_src = null
                  return
              }

              this.fileName = e.target.files[0].name

              let reader = new FileReader();
              reader.onload = (e) => {
                  this.image_src = e.target.result;
              }

              reader.readAsDataURL(files[0]);
          }
      }
  }
</script>

<style scoped>
    .vue-image-input-preview-container {
        width: 100%;
        height: 100%;
    }
    .vue-image-input-preview-container .body {
        width: 100%;
        display: flex;
        flex-direction: column;
    }

    .vue-image-input-preview-container img {
        width: 100%;
        height: 100%;
    }

</style>
