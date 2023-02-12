<script>
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';

export default {
  name: "App",
  components: {
    AppHeader,
    AppMain,
  },
  data() {
    return {
    }
  },
  mounted() {
    setTimeout(() => {
      document.getElementById('loader').remove('loader');
    }, 3000);
  }
};
</script>

<template>

  <div id="loader">
    <img src="./assets/logo.png" alt="">
  </div>
  <AppHeader />
  <AppMain />

</template>

<style lang="scss" scoped>

  #loader{
    position: absolute;
    background-color: black;
    height: 100vh;
    width: 100vw;
    img{
      position: relative;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      animation: ease-in 1s loadingImg;
    }
  }
  @keyframes loadingImg {
    from {filter: opacity(0%);}
    to {filter: opacity(100%);}
    
  }
  
</style>
