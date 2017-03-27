<template>
  <div>
    <a @click="show_image_popup=true" href="javascript:;">点击显示预览</a>
    <bz v-bind:img_path="img_path" :show_image_popup="show_image_popup" v-on:hideImagePopup="toggleImagePopup"></bz>
  </div>
</template>
<script>
  // import toastr from 'toastr'
  import Bz from './Bz'
  export default {
    components: {
      Bz
    },
    data: function () {
      return {
        img_path: 'http://wx1.sinaimg.cn/large/bd2370f9gy1fe1del7g4zj20mg0exae5.jpg',
        show_image_popup: false
      }
    },
    methods: {
      toggleImagePopup: function () {
        this.show_image_popup = !(this.show_image_popup)
      }
    }
  }
</script>
