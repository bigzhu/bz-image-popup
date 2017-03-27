<template>
  <form class="ui form fluid ">
    <div :class="{ 'error': user_name_error }" class="field">
      <label>用户名</label>
      <input @focus="cleanError" v-model="user_name" :placeholder="user_name_placeholder" type="text">
    </div>
    <div :class="{ 'error': password_error }" class="field">
      <label>密码</label>
      <input v-model="password" @keyup.enter="check" @focus="cleanError" :placeholder="password_placeholder"  type="password">
    </div>
    <a @click="check" :class="{ loading: loading }" class="ui blue submit button">登录</a>
  </form>
</template>

<script>
  import toastr from 'toastr'
  export default {
    props: {
      user_name_placeholder: {
        type: String,
        default: '请输入用户名/邮箱'
      },
      password_placeholder: {
        type: String,
        default: '请输入密码'
      },
      loading: {
        type: Boolean,
        default: false
      }
    },
    components: {
    },
    data: function () {
      return {
        user_name: '',
        user_name_error: false,
        password: '',
        password_error: false
      }
    },
    methods: {
      check: function () {
        if (!this.user_name) {
          this.user_name_error = true
          toastr.error('请输入用户名')
          return
        }
        if (!this.password) {
          this.password_error = true
          toastr.error('请输入密码')
          return
        }
        this.$emit('check_done', this.user_name, this.password)
      },
      cleanError: function () {
        this.user_name_error = false
        this.password_error = false
      }
    }
  }
</script>