<template>
    <div class="wrapper">
        <div class="header">
            <Heading content="Rekrutacja GBX Soft" />
            <Searchbar 
                :fetchData="fetchData" 
                :fetching="fetching" 
                title="Wpisz nazwę użytkownika repo"
            />
        </div>
        <Repos :errorInfo="errorInfo" :fetching.sync="fetching" :repos="repos"/>
    </div>
</template>

<script>
import Heading from './Heading.vue'
import Searchbar from './Searchbar.vue'
import Repos from './Repos.vue'

export default {
    name:'Wrapper',
    data() {
        return {
          fetching:false,
          errorInfo:'',
          repos:[]
        };
    },
    components:{
        Heading,
        Searchbar,
        Repos
    },
    methods:{
    fetchData:function(username){
        this.fetching = true;
        fetch(`https://api.github.com/users/${username}/repos`)
            .then(res=>{
                if (res.status !== 200) {
                    throw new Error("Taki użytkownik nie istnieje")
                } else {
                    return res.json()
                }
            })
            .then(r=>{
                if(r.length>0){
                    this.repos = r
                    .sort((a, b) => new Date(a.updated_at) - new Date(b.updated_at))
                    .map(e=>({
                        avatar:e.owner.avatar_url,
                        name:e.name,
                        desc:e.description,
                        branch:e.default_branch,
                        url:e.html_url,
                    }))
                    this.errorInfo = '';
                }
                else{
                    this.repos = [];
                    this.errorInfo = 'Ten użytkownik nie posiada żadnych repozytoriów';
                }
                this.fetching = false;
            })
            .catch(()=>{
                this.repos = [];
                this.errorInfo = 'Taki użytkownik nie istnieje';
                this.fetching = false;
            })
        }
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