<template>
  <img alt="Vue logo" :src="pic" width="100" height="100">
  <HelloWorld :msg="name"/>
</template>

<script>
import liff from '@line/liff';
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  },
  data: function () {
    return {
      pic: '',
      name: ''
    }
  },
  beforeCreate () {
    liff.init({
      liffId: '1656801260-KRjZwV6q',
      withLoginOnExternalBrowser: true,
    })
  },
  created () {
    var self = this
    if (liff.isLoggedIn()) {
      const idToken = liff.getDecodedIDToken();
      self.pic = idToken.picture
      self.name = idToken.name
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

img {
  border-radius: 50%;
}

</style>
