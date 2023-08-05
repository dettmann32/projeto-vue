<template>
  <header>
    <NavBar :logo="logo_src" :alt="app_name"></NavBar>
    <router-view/>
    <FooTer></FooTer>
  </header>
</template>

<script>
import NavBar from "../src/components/NavBar.vue"
import FooTer from './components/FooTer.vue'
export default{
  components:{
    NavBar,FooTer
  },
  data(){
    return{
      logo_src: "/img/logo.png",
      app_name: "Make Your Burger"
    }
  }
}
</script>
