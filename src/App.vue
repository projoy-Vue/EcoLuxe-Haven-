<template>
  <div id="app">
    <Navigation />
    <router-view />
    <FooterComponent/>
  </div>
</template>

<script>
import FooterComponent from './components/FooterComponent.vue';
import Navigation from './components/Navigation.vue';


export default {
  name: "App",

  components: {
    Navigation,
    FooterComponent
  },
  data(){
    return{

    }
   
  }

};
</script>

<style scoped>
#app {
  /* background: linear-gradient(to right, #d5dae0, #c3cfe2); */
  /* height: 100vh;
  width: 100vw; */
}
</style>
