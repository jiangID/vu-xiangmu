<template>
    <div class="Index">
      <Top :message="message"></Top>
        <section class="news">
            <ul>
              <li v-for="(val,index) in news" :key="index">
                <router-link :to={path:/newView/+val.chatId}>{{index+1}} {{val.title}}</router-link>
                <span>{{val.createDate}}</span>
              </li>
            </ul>
        </section>
      <Foot :message="message"></Foot>
    </div>
</template>

<script>
import Top from './Top.vue'
import Foot from './Foot.vue'

export default {
  name: 'Index',
  // meta:{
  //   title:"首页"
  // },
  data () {
    return {
      msg: '欢迎来到vue.js的世界',
      message:{
        logo:require('../assets/logo.png'),
        title:"欢迎来到vue.js的世界",
        copyright:"版权所有@2018"
      },
      news:[]
    }
  },
  components:{
    Top,Foot
  },
  methods:{   
      getNewslist(){
        this.axios.get('http://jsf5211314.gz01.bdysite.com/dist/api/getChatList.php').then((res)=>{
          this.news = res.data;
          console.log(res.data)
        })
      }
  },
  created(){
    this.getNewslist();
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    /* header{
      background: #000;
      height: 50px;
    } */
    .news ul{
       margin:25px auto;
       width:96%;
   }
   .news ul li{
       line-height: 35px;
       position: relative;
   }
   span{
     position: absolute;
     right: 10px
   }
</style>