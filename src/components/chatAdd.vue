<template>
    <div id="chatAdd" class="chatAdd">
         <div id="form">
            <ul>
                <li>
                    <label for="">聊天室名称</label>
                    <input type="text" v-model="title" name="title" id="title" placeholder="请输入聊天室名称">
                </li>
                <li>
                    <label for="">聊天室介绍</label>
                    <textarea id="body" v-model="body" name="body" placeholder="请输入聊天室介绍" ></textarea>
                </li>
                <li>
                   <span id="info"></span> 
                </li>
                <li>
                    <button type="button" id="send" @click="chatAdd">创建聊天室</button>
                </li>
            </ul>
         </div>
    </div>
</template>

<script>

import qs from 'qs'

import { getCookie, setCookie } from 'tiny-cookie'

export default {
    name:"chatAdd",
    data(){
        return{
                title:"",
                body:""
      }
    },
    methods:{
        chatAdd(){
            // let userData = {
            //     title:this.info.title,
            //     body:this.info.body,
            //     send:"创建聊天室"
            // }
            // let uD = qs.stringify(userData); 
            let fromData = "send=创建聊天室&title="+this.title+"&body="+this.body;
            this.axios.get('http://jsf5211314.gz01.bdysite.com/dist/api/chatAddSave.php?'+fromData).then((res)=>{
                if(res.data.valid){
                     this.$router.push({path:"/"})
                }else{
                    console.log(res.data.message)
                    console.log(res.data)
                }
            })
        }
    }
}
</script>



<style>
#chatAdd{
        width:70%;
        margin:10vh auto;
        padding:10px;
    }
    #chatAdd ul{
        display: flex;
        flex-flow: column;

    }
    #chatAdd ul li{
        display: flex;
        flex-flow: column;
    }

    #chatAdd ul li label{
        margin:.5rem 0;
    }
    #chatAdd ul li input,
    #chatAdd ul li textarea{
        border-radius: .15625rem;
        border:none;
        height:1.5625rem;
        padding:.3125rem;
        outline: none;
    }

    #chatAdd ul li textarea{
        height:5.125rem;

    }
    #chatAdd ul li #info{
        color:red;
        text-align: center;
        font-size:.75rem;
        margin-top: .46875rem;
    }
        #chatAdd ul li button{
            border-radius: .3125rem;
            height:2.1875rem;
            margin-top:1rem;
            padding:.3125rem 0;
            border:none;
            outline: none;
            color:#fff;
            background: #0c8b21;
        }
</style>