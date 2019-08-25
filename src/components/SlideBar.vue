<template>
<div class="autherinfo">
  <div class="authersummay">
    <div class="topbar"><span>作者</span></div>
    <router-link :to="{
          name:'user_info',
          params:{
            name:userinfo.loginname
          }
          }">
      <img :src="userinfo.avatar_url" alt="">
    </router-link>
  </div>
  <div class="recent_topics">
    <div class="topbar"><span>作者最近主题</span></div>
    <ul>
      <li v-for="(list,index) in topcilimitby5" :key="index">
        <router-link :to="{
        name:'post_content',
        params:{
          id:list.id,
          name:list.author.loginname
        }
        }">
          {{list.title}}
        </router-link>
      </li>
    </ul>
  </div>
  <div class="recent_replies">
    <div class="topbar"><span>作者最近回复</span></div>
    <ul>
      <li v-for="(list,index) in replylimitby5" :key="index">
        <router-link :to="{
        name:'post_content',
        params:{
          id:list.id,
          name:list.author.loginname
        }
        }">
          {{list.title}}
        </router-link>
      </li>
    </ul>
  </div>
</div>
</template>

<script>
export default {
  name: "SlideBar",
  data(){
      return {
        isLoading:false,
        userinfo:{}
      }
  },
  methods:{
    getData(){
      this.$http.get(`https://cnodejs.org/api/v1/user/${this.$route.params.name}`)
        .then(res=>{
          this.isLoading = false; //加载成功，去除动画
          this.userinfo = res.data.data;
        })
        .catch(function (err) {
          console.log(err)
        })
    }
  },
  computed:{
    topcilimitby5(){
      if(this.userinfo.recent_topics){
        return this.userinfo.recent_topics.slice(0,5);
      }
    },
    replylimitby5(){
      if(this.userinfo.recent_replies){
        return this.userinfo.recent_replies.slice(0,5);
      }
    }
  },
  beforeMount(){
    this.isLoading = true;//加载成功之前显示加载动画
    this.getData();//在页面加载之前获取数据
  }
}
</script>

<style lang="scss" scoped>
.authersummay{
  border: 1px solid #cccccc;
  border-radius: 8px;
  border-top: none;
}
.autherinfo {
  width: 328px;
  float: right;
}
li{
  padding: 3px 0 ;
}
.recent_replies ul, .recent_topics ul {
  list-style: none;
  border: 1px solid #cccccc;
  padding: 8px;
  border-bottom-left-radius: 8px;
  border-bottom-right-radius: 8px;
}

ul a {
  font-size: 12px;
  text-decoration: none;
  color: #778087;
}

.topbar {
  background-color: #f6f6f6;
  font-size: 12px;
  margin-top: 10px;
  display: flex;
  align-items: center;
  height: 24px;
  border: 1px solid #cccccc;
  border-bottom: none;
  border-top-left-radius: 8px;
  border-top-right-radius: 8px;
  span{
    margin-left: 8px;
  }
}

img {
  height: 48px;
  width: 48px;
  border-radius: 50%;
  margin: 10px;
}

.loginname {
  width: 100px;
  float: right;
  margin-top: 22px;
  margin-right: 159px;
  font-size: 14px;
}

.loginname a {
  text-decoration: none;
  color: #778087;
}

.authersummay .topbar {
  margin-top: 0px;
}
</style>
