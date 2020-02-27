<template>
  <h1 class="heading">{{content}}</h1>
</template>

<script>
export default {
    name:'Heading',
    props:{
        content:{
            type:String,
            required:true
        }
    }
}
</script>

<style lang="scss" scoped>
    .heading{
        color: #002BDC;
        font-weight: bold;
        font-size: 48px;
        line-height: 56px;
        margin:0;
    }
</style>