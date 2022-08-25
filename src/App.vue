<template>
  <SiteHeader/>

  <AllCarts/>      
  
  <SiteFooter/>   
      
</template>

<script>
import SiteHeader from './components/SiteHeader.vue';
import SiteFooter from './components/SiteFooter.vue';
import AllCarts from './components/AllCarts.vue';


export default {
  name: 'App',
  components: {
    SiteHeader,
    SiteFooter,
    AllCarts,
  },
  data() {
    return{

    }
  },
}
</script>

<style>
#app {
  font-family: 'EB Garamond', serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #d7be8a;
  
}

@import url('https://fonts.googleapis.com/css2?family=Lavishly+Yours&display=swap');
@import url('https://fonts.googleapis.com/css2?family=EB+Garamond&display=swap');

</style>