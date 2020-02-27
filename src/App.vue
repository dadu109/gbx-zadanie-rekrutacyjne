<template>
  <div id="app">
    <Navbar />
    <Wrapper  />
  </div>
</template>

<script>
import Navbar from './components/Navbar.vue'
import Wrapper from './components/Wrapper.vue'

export default {
  name: 'App',
  
  components: {
    Navbar,
    Wrapper
  },
}
</script>

<style lang="scss">
  @import url('https://fonts.googleapis.com/css?family=Roboto:400,500,700&display=swap');

  *,*::before,*::after{
    box-sizing: border-box;
  }

  body{
    margin:0;
  }

  #app {
    margin:0 auto;
    max-width: 1200px;
    height: calc(100vh - 30px);
    font-family: 'Roboto';
    @media (max-width: 1199px) {
      display:none;
    }
  }

</style>
