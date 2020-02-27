<template>
    <simplebar data-simplebar-auto-hide="false" class="wrapper">
        <div v-if="fetching" class="loader">loading</div>
        <div class="repos" v-for="repo in repos" :key="repo.url">
            <div class="repo">
                {{repo}}
            </div>
        </div>
    </simplebar>
</template>

<script>
import simplebar from 'simplebar-vue';
import 'simplebar/dist/simplebar.min.css';

export default {
    name:"Repos",
    props:{
        repos:{
            type:Array
        },
        errorInfo:{
            type:String
        },
        fetching:{
            type:Boolean
        }
    }, 
    components:{
        simplebar,
    },
}
</script>

<style lang="scss" scoped>
    .wrapper{
        border-radius: 10px;
        margin-top: 25px;
        padding: 0 40px;
        height: 100%;
        border-top: solid 40px #fff;
        border-bottom: solid 34px #fff;
        display: flex;
        justify-content: center;
        align-items: center;
        box-shadow: 1px 0px 16px rgba(0, 0, 0, 0.17);
    }
    .repo{
        margin:70px 0;
    }
</style>