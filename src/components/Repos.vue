<template>
    <simplebar data-simplebar-auto-hide="false" class="wrapper">
        <div v-if="fetching" class="loader">loading</div>
        <div v-if="errorInfo" class="errorInfo"><span>{{errorInfo}}</span></div>
        <div v-if="!errorInfo&&!fetching" class="repos">
            <Repo v-for="repo in repos" :key="repo.url" :repo="repo"></Repo>
        </div>
    </simplebar>
</template>

<script>
import simplebar from 'simplebar-vue';
import 'simplebar/dist/simplebar.min.css';
import Repo from './Repo.vue'

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
        Repo,
        simplebar,
    },
}
</script>

<style lang="scss" scoped>
    .errorInfo{
        display:flex;
        justify-content: center;
        align-items:center;
        height:500px;
        span{
            color:#002BDC;
            font-size: 20px;
        }
    }
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
    .repos{
        display:grid;
        grid-template-columns: repeat(2, 1fr);
        grid-gap: 20px;
    }
</style>