<template>
  <div id="nav">
    <router-link to="/Home">Home</router-link> |
    <router-link to="/News">News</router-link>

    <!-- <div v-if="showModal">
      <MessageBox />
    </div> -->
  </div>
  <router-view/>
</template>

<script>
import MessageBox from './components/MessageBox.vue'

export default{
  data() {
    return {
      showModal: true
    }
  },
  components: {
    MessageBox
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
  margin-left: 30px;
  margin-right: 30px;
}

#nav {
  padding: 10px;
}

body {
  background: rgb(240, 236, 236);
}
/* #nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
} */
</style>
