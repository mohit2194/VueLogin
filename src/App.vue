<template>
  <div id="app">
    <form action="">
      <input type="email" v-model="name" required>
      <input type="password" v-model="password" required>
      <button @click="checkcreds()">Login</button>
    </form>

    <p v-if="!authenticate">Incorrect creds</p>
  </div>
</template>

<script>
import store from './store/index';
export default {
  name: 'app',
  store,
  data: function () {
    return {
      authenticate: true,
      name: '',
      password: '',
      mockAccountEmail: '',
      mockAccountPass: ''
      
    }
  },
  mounted: function() {
   this.mockAccountEmail = this.$store.state.mockName;
   this.mockAccountPass = this.$store.state.mockPassword;
  },

  methods: {
    checkcreds: function() {
      if (this.name !== this.mockAccountEmail) {
        this.authenticate = false;
      }
      if (this.password !== this.mockAccountPass) {
        this.authenticate = false;
      }
    },
  }
  
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

#app input,
#app button {
  display: block;

}
</style>
