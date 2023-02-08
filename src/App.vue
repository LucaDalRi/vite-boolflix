<script>
import { store } from './store';
import NomeApp from './components/HelloWorld.vue';

export default {
  name: "App",
  components: {
    NomeApp,
  },
  data() {
    return {
      store
    }
  }

};
</script>

<template>

  <NomeApp />

</template>

<style lang="scss" scoped>

</style>
