<template>
    <div class="wrapper">
        <div class="header">
            <Heading content="Rekrutacja GBX Soft" />
            <Searchbar title="Wpisz nazwę użytkownika repo" />
        </div>
    </div>
</template>

<script>
import Heading from './Heading.vue'
import Searchbar from './Searchbar.vue'

export default {
    name:'Wrapper',
    components:{
        Heading,
        Searchbar,
    }
  }
</script>

<style lang="scss" scoped>
    .wrapper{
        width:100%;
        height: 602px;
    }
    .header{
        display:flex;
        justify-content: space-between;
    }
</style>