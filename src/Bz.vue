<template>
  <div id="markhere">
    <a @click="hidePopup" href="javascript:;" class="image-popup-delete-btn" :style="{display:display_close_icon}">
      <img src="../assets/delete-btn.svg"></a>
    <div class="ui basic modal image-popup">
      <div class="image content" style="justify-content:center;">
        <img class="image" :src="img_path">
      </div>
    </div>
  </div>
</template>

<script>
  import $ from 'jquery'
  export default {
    props: ['img_path', 'show_image_popup'],
    components: {
    },
    watch: {
      show_image_popup: function () {
        if (this.show_image_popup) {
          this.showImagePopup()
        }
      }
    },
    computed: {
      display_close_icon: function () {
        return this.hide_close_icon ? 'none' : 'block'
      }
    },
    data: function () {
      return {
        hide_close_icon: true
      }
    },
    mounted: function () {
      this.$nextTick(function () {
        // code that assumes this.$el is in-document
      })
    },
    methods: {
      hidePopup: function () {
        this.hideImagePopup()
      },
      showImagePopup: function () {
        let self = this
        if ($('.image-popup').length > 1) { // 如果有多个, 那么要删掉之前的弹出
          $($('.image-popup')[0]).remove()
        }
        $($('.image-popup')[0])
          .modal({
            onShow: function () {
              // 显示关闭按钮
              self.showCloseIcon()
            },
            onHide: function () {
              // 隐藏关闭按钮
              self.hideCloseIcon()
              // 发送事件, 要求父组件修改状态
              self.$emit('hideImagePopup')
            }})
          .modal('show')
      },
      hideImagePopup: function () {
        $($('.image-popup')[0]).modal('hide')
      },
      showCloseIcon: function () {
        this.hide_close_icon = false
      },
      hideCloseIcon: function () {
        this.hide_close_icon = true
      }
    }
  }
</script>

<style>
  .image-popup-delete-btn {
    position: fixed;
    bottom: 1rem;
    left: 50%;
    margin-left: -2.5rem;
    z-index: 9999;
  }
</style>
