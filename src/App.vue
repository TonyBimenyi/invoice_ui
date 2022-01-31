
<template>
  <div id="wrapper">
    <nav class="navbar">
      <div class="navbar-brand">
        <router-link to="/" class="navbar-logo"><strong>Invoicely</strong></router-link>
      </div>
      <div class="navbar-menu">
        <div class="navbar-end">
          <template v-if="$store.state.isAuthenticated">
            <router-link to="/dashboard" class="navbar-item">Dashboard</router-link>
          </template>
          <template v-else>
            <router-link to="/home" class="navbar-item">Home</router-link>
            <router-link to="/sign-up" class="btn1">Sign up</router-link>
            <router-link to="/log-in" class="btn2">Log in</router-link>
          </template>
        </div>
      </div>
    </nav>
    <section class="section">
      <router-view/>
    </section>
  </div>

  <footer class="footer">
    <p class="text">Copyright (c) 2022</p>
  </footer>
</template>
<script>
  import axios from 'axios'
  export default{
    name: 'App',
    beforeCreate(){
 
    this.$store.commit('initializeStore')    
    const token = this.$store.state.token

    if(token){
      axios.defaults.headers.common['Authorization'] = "Token"+token
    }else{
       axios.defaults.headers.common['Authorization'] = ""
    }
    }
  }
</script>
<style lang="scss">
    @import url(./assets/styles/home.css);
</style>
