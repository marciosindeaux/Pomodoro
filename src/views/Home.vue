<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld :msg="this.msg"/>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue';

export default {
  name: 'home',
  data() {
    return {
      msg: 'Welcome to Your Vue App',
    };
  },
  components: {
    HelloWorld,
  },
};
</script>
<style scoped>
</style>
