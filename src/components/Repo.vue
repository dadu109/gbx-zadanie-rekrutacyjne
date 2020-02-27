<template>
    <div class="repo">
        <img :src="repo.avatar">
        <div class="repoBody">
            <h3>{{repo.name}}</h3>
            <p>{{repo.desc?adjustDesc(repo.desc):'To repozytorium nie posiada opisu'}}</p>
            <div>{{repo.branch}}</div>
        </div>
        <div class="repoButton">
            <a target="_blank" :href="repo.url">
                <svg width="36" height="30" viewBox="0 0 36 30" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M35.4142 16.4142C36.1953 15.6332 36.1953 14.3668 35.4142 13.5858L22.6863 0.857866C21.9052 0.0768177 20.6389 0.0768176 19.8579 0.857866C19.0768 1.63891 19.0768 2.90524 19.8579 3.68629L31.1716 15L19.8579 26.3137C19.0768 27.0948 19.0768 28.3611 19.8579 29.1421C20.6389 29.9232 21.9052 29.9232 22.6863 29.1421L35.4142 16.4142ZM-1.74846e-07 17L34 17L34 13L1.74846e-07 13L-1.74846e-07 17Z" fill="#A5B8FF"/>
                </svg>
            </a>
        </div>
    </div>
</template>

<script>
export default {
    name:"Repo",
    props:{
        repo:{
            type:Object,
            required:true,
        }
    },
    methods:{
        adjustDesc:function(desc){
            const maxChar = 80;
            if(typeof(desc)==='string'){
                return desc.length > maxChar ? `${desc.slice(0, maxChar).split(' ').slice(0, -1).join(' ')}...` : desc;
            }else{
                throw 'Provided description is not a string'
            }
        }
    }
}
</script>

<style lang="scss" scoped>
    .repo{
        width: 555px;
        height: 130px;
        background: #F1F4FF;
        border-radius: 10px;
        padding: 26px 30px 11px;
        display:flex;

        img{
            height:60px;
            border-radius: 100%;
        }
        .repoBody{
            margin:0 19px;
            display:flex;
            flex-direction: column;
            h3{
                margin:0;
                font-weight: 500;
                font-size: 24px;
                line-height: 24px;
                color: #304389;
                display:block;
                width:335px;
                overflow: hidden;
                white-space: nowrap;
                position:relative;
                &::after{
                    content:'';
                    position:absolute;
                    right:0px;
                    width:35px;
                    height:100%;
                    background:linear-gradient(90deg,transparent,#F1F4FF)
                }
            }
            p{
                width:335px;
                margin:8px 0 0;
                font-weight: normal;
                font-size: 16px;
                line-height: 20px;
                color: #848484;
            }
            div{
                font-weight: normal;
                font-size: 10px;
                color: #A5B8FF;
                margin-top:auto;
            }
        }
        .repoButton{
            margin-left:auto;
            padding: 40px 0;
            svg{
                transform:translateY(-50%);
            }
            path{
                transition:fill .2s ease-in-out;
            }
            &:hover path{
                fill:#304389;
            }
        }
    }
</style>