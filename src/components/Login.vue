<template>
<div class="container">
    <x-header :right-options="{showMore: False}"  :left-options="{showBack: ture}">Login</x-header>
  <x-input title="手机号" mask="999 9999 9999"  :max="13" is-type="china-mobile"></x-input>
  <x-input title="密码"  :max="13" type="password" ></x-input>
  <x-button @click.native="Login">登录</x-button>
   </div>
</template>

<script>
import { XButton, XInput, XHeader } from 'vux'

export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  },
  methods: {
    Login () {
      window.history.length > 1
        ? this.$router.go(-1)
        : this.$router.push('/')
    }
  },
  HelloFromVux: {
    goBack () {
      this.$router.push('/HelloFromVux')
    }
  },
  components: {
    XButton,
    XInput,
    XHeader
  }
}
</script>

  

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
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

