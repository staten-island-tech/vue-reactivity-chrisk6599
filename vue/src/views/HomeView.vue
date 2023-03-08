<script>
export default {
  name: 'Home',
  components: {},
  data() {
    return {
      loggedIn: false
    }
  },
  methods: {
    authState: function () {
      if (this.loggedIn === false) {
        this.loggedIn = true
      } else {
        this.loggedIn = false
      }
    }
  }
}
</script>

<template>
  <div class="home">
    <button @click="authState" v-if="loggedIn">Log Out</button>
    <button @click="authState" v-else>Login</button>
  </div>
</template>

<style scoped>
h1 {
  color: red;
}
</style>
