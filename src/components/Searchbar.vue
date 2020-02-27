<template>
    <form @submit.prevent="onSubmit" class="form">
        <p class="title">{{title}}</p>
        <div :class="{'searchbar-disabled' : fetching}" class="searchbar">
            <input v-model="username" :disabled="fetching" :class="{'searchbar-disabled' : fetching}"  type="text" class="username-input">
            <button type="submit" :disabled="fetching" class="submit-button">
                <svg width="17" height="16" viewBox="0 0 17 16" fill="none" xmlns="http://www.w3.org/2000/svg" class="arrow">
                    <path d="M15.7899 8.66887C16.1804 8.27834 16.1804 7.64518 15.7899 7.25465L9.42591 0.890694C9.03539 0.500169 8.40222 0.500169 8.0117 0.890694C7.62118 1.28122 7.62118 1.91438 8.0117 2.30491L13.6686 7.96176L8.0117 13.6186C7.62118 14.0091 7.62118 14.6423 8.0117 15.0328C8.40222 15.4234 9.03539 15.4234 9.42591 15.0328L15.7899 8.66887ZM0.120361 8.96176H15.0828V6.96176H0.120361V8.96176Z" fill="#F1F4FF"/>
                </svg>
            </button>
        </div>
    </form>
</template>

<script>
export default {
    name:'Searchbar',
    data() {
        return {
        username: '',
        };
    },
    props:{
        title:{
            type:String,
            required:true
        },
        fetchData:{
            type:Function,
        },
        fetching:{
            type:Boolean,
        }
    },
    methods:{
        onSubmit: function(){
            this.fetchData(this.username)
        }
    }
}
</script>

<style lang="scss" scoped>
    .form{
        display:flex;
        flex-direction: column;
        align-items: flex-start;
        width: 398px;
        .title{
            margin:0 0 0 7px;
            font-weight: 400;
            font-size: 12px;
            line-height: 18px;
            color: #304389;
        }
        .searchbar{
            border: 2px solid #F1F4FF;
            border-radius: 10px;
            width: 398px;
            height: 42px;
            display:flex;
            justify-content: space-between;
            transition:border .2s ease-in-out;
            padding:10px 6px;
            &:focus-within{
                border: 2px solid #304389;
                .arrow path{
                    fill:#304389;
                }
            }
            &-disabled{
                background-color: rgb(240, 240, 240);
            }
            .username-input{
                font-weight: 400;
                font-size: 18px;
                line-height: 18px;
                height:100%;
                flex:1;
                color: #848484;
                border:none;
                outline:none;

            }
            .submit-button{
                background:none;
                padding:0 25px;
                height:100%;
                border:none;
                outline:none;
                cursor: pointer;
                .arrow path{
                    transition: fill .2s ease-in-out;
                }
                &:hover .arrow path{
                    fill:#304389;
                }
            }
        }
    }
</style>