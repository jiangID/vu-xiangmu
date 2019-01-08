<template>
    <div class="Login">
        <div class="container">
            <form>
                  <h1>用户登陆<small>哈哈哈</small></h1>
                  <label for="">
                      <input type="text" v-model="info.name" name="username" placeholder="请输入您的帐号">
                  </label>
                  <label for="">
                      <input type="password" v-model="info.password" name="password" placeholder="请输入您的密码">
                  </label>
                  <label for="" id="success"></label>
                  <label for="" class="u">
                      <button type="button" @click="login">登陆</button>
                      <button @click="register">注册</button>
                  </label>
            </form>
        </div>
    </div>
</template>

<script>

import qs from 'qs'
import { getCookie, setCookie } from 'tiny-cookie'

export default {
  name: 'Login',
  data(){
      return{
          info:{
                name:"",
                password:"",
                userId:""
            }
      }
  },
  created(){
   
  },
  methods:{
        register(){
            this.$router.push("/register")
        },
        login(){
            let userData = {
                username:this.info.name,
                password:this.info.password,
                send:1
            }
            let uD = qs.stringify(userData); 
            this.axios.post('http://jsf5211314.gz01.bdysite.com/dist/api/loginSave.php',uD).then((res)=>{
                console.log(res.data)
                if(res.data.userId){
                     this.$router.push({path:"/"})
                }else{
                    alert("cuowu")
                }
            })
        }
    },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    #app{
    height: 100vh;
    width:100%;
    font-size:.5625rem;
}
.container{
    width: 40%;
    height: 500px;
    margin:100px auto 0;
    text-align: center;
}
input{
    width: 500px;
    height: 40px;
    margin-top:30px;
}
</style>