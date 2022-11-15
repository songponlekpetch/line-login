<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p>
      FOR A <b>LINE LOGIN</b> TESTING ON MAKALIN BOOKING,<br>
      check access token at below
    </p>
    <table>
      <tr>
        <td>ID token</td>
        <td><textarea id="w3review" name="w3review" rows="4" cols="60">{{idToken}}</textarea></td>
      </tr>
      <tr>
        <td>Access token</td>
        <td><textarea id="w3review" name="w3review" rows="4" cols="60">{{accessToken}}</textarea></td>
      </tr>
    </table>
    <button v-on:click="logout">Logout</button>
  </div>
</template>

<script>
import liff from '@line/liff';

export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data () {
    return {
      accessToken: '',
      idToken: ''
    }
  },
  methods: {
    getToken () {
      var self = this
      if (liff.isLoggedIn()) {
        const accessToken = liff.getAccessToken()
        self.accessToken = accessToken
        const idToken = liff.getIDToken()
        self.idToken = idToken
      }
    },
    logout() {
      if (liff.isLoggedIn()) {
        liff.logout();
        window.location.reload();
      }
    }
  },
  mounted () {
    this.getToken()
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
table {
  font-family: arial, sans-serif;
  border-collapse: collapse;
  margin: 0;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

td, th {
  border: 1px solid #dddddd;
  text-align: left;
  padding: 8px;
}

tr:nth-child(even) {
  background-color: #dddddd;
}


</style>
