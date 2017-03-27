<template>
  <div>
    <doc :name="name"
         :desc="desc"
         :parm_desc="parm_desc"
         :parms="parms"
         :code="code"
    >
      <img src="http://wx4.sinaimg.cn/orj360/006vNY3Pgy1fe1a6g1jm2j30m80etadw.jpg" @click="img_path='http://wx4.sinaimg.cn/large/006vNY3Pgy1fe1a6g1jm2j30m80etadw.jpg'" title="点击显示预览" alt=""/>
    </doc>
    <bz v-model="img_path"></bz>
    
    <div id="markhere">
      <a href="javascript:;" class="image-popup-delete-btn" :style="{display:display_close_icon}">
        <img src="../assets/delete-btn.svg">
      </a>
      <div class="ui basic modal image-popup">
        <div class="image content" style="justify-content:center;">
          <img class="image" src="http://wx4.sinaimg.cn/orj360/006vNY3Pgy1fe1a6g1jm2j30m80etadw.jpg">
        </div>
      </div>
    </div>
    
  </div>
</template>

<script>
  // import toastr from 'toastr'
  import Bz from './Bz'
  import Doc from 'bz-doc'
  export default {
    components: {
      Bz,
      Doc
    },
    data: function () {
      return {
        name: 'bz-image-popup',
        desc: '弹出预览',
        parms: [
          {parm: 'img_path', desc: '大图url'}
        ],
        parm_desc: ``,
        code: `<bz v-model="img_path"></bz>`,
        img_path: ''
      }
    }
  }
</script>
