<template>
<div class="UserInfo">
  <!--在数据未返回的时候，显示这个正在加载的gif-->
  <div class="loading" v-if="isLoading">
    <img src="../assets/loading.gif" >
  </div>
  <div class="userInfomation" v-else>
    <section>
      <dir class="logo">
        <img :src="userinfo.avatar_url" >
        <span>{{userinfo.loginname}}</span>
      </dir>
      <p>
        {{userinfo.score}}积分
      </p>
      <p>
        注册时间：{{userinfo.create_at | formatDate}}
      </p>
    </section>
    <div class="replies">
      <p>回复的主题</p>
      <ul>
        <li v-for="(item,index) in userinfo.recent_replies" :key="index">
          <router-link :to="{
          name:'post_content',
          params:{
            id:item.id
          }
          }">
            {{item.title}}
          </router-link>
        </li>
      </ul>
    </div>
    <div class="topics">
      <p>创建的主题</p>
      <ul>
        <li v-for="(item,index) in userinfo.recent_topics" :key="index">
          <router-link :to="{
          name:'post_content',
          params:{
            id:item.id
          }
          }">
            {{item.title}}
          </router-link>
        </li>
      </ul>
    </div>
  </div>
</div>
</template>
<script>
export default {
  name: "UserInfo",
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
            this.isLoading = false;
            this.userinfo = res.data.data;
          })
          .catch(function (err) {
            console.log(err)
          })
      }
  },
  beforeMount(){
    this.isLoading = true;
    this.getData();
  }
}
</script>

<style lang="scss" scoped>
@media screen and (max-width: 799px){
  .userInfomation{
    width: 100vw;
  }
}

@media screen and (min-width: 800px){
  .userInfomation{
    width: 75%;
  }
}

.userInfomation {
  background: #fcfcfc;
  margin: 10px auto;
}
.userInfomation section {
  padding: 12px;
  p{
    margin: 4px 0;
  }
}

.userInfomation li {
  list-style:none;
}
.userInfomation .replies,
.userInfomation .topics {
  font-size: 0.72rem;
  border-top: 10px #DDDDDD solid;
}
.userInfomation > div > p {
  padding: 12px 0 12px 12px;
  background-color: rgba(212, 205, 205, 0.17);
  font-size: 0.75rem;
  margin: 0;
}
.userInfomation > div >ul > li {
  padding: 4px 0 4px 12px;
  white-space: nowrap;
  font-size: 0.72rem;
  text-overflow: ellipsis;
  overflow: hidden;
  line-height: 30px;
  vertical-align: middle;
}
.userInfomation > div >ul > li > a {
  color: #094E99;
  text-decoration: none;
}

.logo{
  display: flex;
  align-items: center;
  img{
    width: 30px;
    height: 30px;
    border-radius: 50%;
    margin-right: 8px;
  }
}

</style>
