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

  .simplebar-track.simplebar-vertical {
      width: 4px;
      right: 13px;
      background-color: #E1E1E1;
      border-radius: 50px;
      margin-bottom: -6px;
      margin-top: -6px;
  }
  .simplebar-scrollbar {
      background-color: #A8A8A8;
      border-radius: 50px;
  }
  .simplebar-content{
      min-height:100%;
  }

</style>
