<template>
<div class="article">
  <div class="loading" v-if="isLoading">
    <img src="../assets/loading.gif" >
  </div>
  <div v-else>
    <div class="topic_header">
      <div class="topic_title">{{post.title}}</div>
      <ul>
        <li>• 发布于：{{post.create_at | formatDate}}</li>
        <li>• 作者：
          <router-link :to="{
            name:'user_info',
            params:{
              name:post.author.loginname
            }
          }">
          {{post.author.loginname}}
          </router-link>
        </li>
        <li>• {{post.visit_count}}次浏览</li>
        <li>• 来自{{post | tabFormatter}}</li>
      </ul>
      <div v-html="post.content" class="topic_content" id="content" ref="p"></div>
    </div>
    <div id="reply">
      <div class="topbar">回复</div>
      <div v-for="(reply,index)  in post.replies" class="replySec" :key="index">
        <div class="replyUp">
          <router-link :to="{
          name:'user_info',
          params:{
            name:reply.author.loginname
          }
          }">
            <img :src="reply.author.avatar_url" alt="">
          </router-link>
          <router-link :to="{
          name:'user_info',
          params:{
            name:reply.author.loginname
          }
          }">
            <span>{{reply.author.loginname}}</span>
          </router-link>
          <span class="lou">
          {{index+1}}楼
        </span>
          <span v-if="reply.ups.length>0" >
          ☝ {{reply.ups.length}}
        </span>
          <span v-else>
        </span>
        </div>
      <p v-html="reply.content" id="content"></p>
      </div>
    </div>
  </div>
</div>
</template>
<script>
export default {
  name: "Article",
  data(){
    return {
      isLoading: false,
      post: {}
    }
  },
  methods:{
    getArticleData(){
      this.$http.get(`https://cnodejs.org/api/v1/topic/${this.$route.params.id}`)
        .then(res=>{
          if(res.data.success == true){
            this.isLoading =false;
            this.post = res.data.data;
          }
        })
        .catch(function (err) {
          console.log(err)
        })
    }
  },
  beforeMount(){
    this.isLoading =true;
    this.getArticleData();
  },
  mounted(){
    this.$nextTick(()=>{})
  },
  watch:{
    '$route'(to,from){
      this.getArticleData()
    }
  },
}
</script>
<style lang="scss" scoped>
@import url('../assets/markdown-github.css');

@media screen and (max-width: 799px){
  .article{
    width: 100vw;
  }
  .topic_header{
    .topic_content{
      p{
        overflow: hidden;
      }
    }
  }
  #reply img {
    width: 20px;
    height: 20px;
    position: relative;
    bottom: -9px;
  }
}

@media screen and (min-width: 800px){
  .article:not(:first-child) {
    margin-right: 340px;
    margin-top: 15px;
  }
  
  .topic_content .markdown-text img {
    width: 92% !important;
  }
}

a{
  text-decoration: none;
  color: #778087;
}

.topbar {
  width: 98%;
  margin: 0 auto;
  padding: 10px 20px;
  background-color: #f6f6f6;
  font-size: 12px;
  border: 1px solid #cccccc;
}

#reply, .topic_header {
  //background-color: #fcfcfc;
}

#reply {
  margin-top: 15px;
}

#reply a, #reply span {
  font-size: 13px;
  color: #666;
  text-decoration: none;
}
.replySec{
  padding:0 10px;
  margin: 8px 0;
  .replyUp{
    padding: 8px;
    border: 1px solid #cccccc;
    border-bottom: none;
    background: #f6f6f6;
    border-top-left-radius: 8px;
    border-top-right-radius: 8px;
    display: flex;
    align-items: center;
    position: relative;
    img{
      height: 25px;
      width: 25px;
      border-radius: 50%;
      margin-right: 8px;
    }
    .lou{
      position: absolute;
      right: 10px;
    }
  }
  p{
    padding: 8px;
    color: #778087;
    font-size: 14px;
    border: 1px solid #cccccc;
    border-top: none;
    border-bottom-left-radius: 8px;
    border-bottom-right-radius: 8px;
    word-wrap: break-word;
  }
}

.loading {
  text-align: center;
  padding-top: 300px;
  img{
    border-radius: 50%;
  }
}

.replyUp a:nth-of-type(2) {
  margin-left: 0px;
  display: inline-block;
}

.topic_header {
  padding: 10px;
}

.topic_title {
  font-size: 20px;
  font-weight: bold;
  padding-top: 8px;
  text-align: center;
}

.topic_header ul {
  list-style: none;
  padding: 0px 0px;
  margin: 6px 0px;
  text-align: center;
}

.topic_header li {
  display: inline-block;
  font-size: 12px;
  color: #838383;
  &:not(:last-child){
    margin-right: 8px;
  }
}

.topic_content {
  border: 1px solid #cccccc;
  color: #000000;
  font-size: 14px;
  padding: 8px;
  border-radius: 8px;
}

</style>
