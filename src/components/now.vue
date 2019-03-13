<template>
<div class="container">
    <x-header :right-options="{showMore: False}"  :left-options="{showBack: ture}">Login</x-header>
  <x-input title="手机号" mask="999 9999 9999"  :max="13" is-type="phone" v-model="phone"></x-input>
  <x-input title="密  码"  :max="13" type="password" v-model="password" ></x-input>
  <box gap="10px 10px">
  <x-button :gradients="['#1D62F0','#19D5FD']" @click.native="Login">登录</x-button>
  </box>
   </div>
</template>

<script>
import { XButton, XInput, XHeader, AlertModule, Box } from 'vux'

export default {
  name: 'HelloWorld',
  data () {
    return {
      password: '',
      phone: ''
    }
  },
  methods: {
    Login () {
      if (this.password === '123456') {
        this.$router.go(-1)
        this.$router.push({ path: '/' })
      } else {
        AlertModule.show({
          title: '登录失败',
          content: '密码错误'
        })
      }
    }
  },
  HelloFromVux: {
    goBack () {
      this.$router.push('/HelloFromVux')
    }
  },
  components: {
    Box,
    AlertModule,
    XButton,
    XInput,
    XHeader
  }
}
</script>

  

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>

