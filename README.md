# Cnode
## 描述
基于 Vue 框架的仿 Cnode 网站。主要包含组件 Header PostList Pagination Footer Article SliderBar UserInfo  About。

## 路由情况
```
import Router from 'vue-router'
import Vue from 'vue'

Vue.use(Router)

export default new Router({
  routes: [
    {
      name:'root',
      path:'/',
      components:{
        main:PostList
      }
    },
    {
      name:'post_content',
      path:'/topic/:id&author=:name',
      components:{
        main:Article,
        slidebar:SlideBar
      }
    },
    {
      name:'user_info',
      path:'/userinfo/:name',
      components:{
        main:UserInfo
      }
    },
    {
      name:'about',
      path:'/about',
      components:{
        main:About
      }
    }
  ]
})
```
## 布局
![layout](https://github.com/Youngto25/cnode/blob/master/image/jiegou.png)

## 网页之间的跳转
如在 articel 中点击作者姓名，跳转到 userinfo

要跳转的路由，并提供参数
```
<li>• 作者：
  <router-link :to="{
    name:'user_info',
    params:{
      name:post.author.loginname
    }
  }">
  {{post.author.loginname}}
  </router-link>
```

通过 conde 社区提供的 API 获取作者相关信息
```
beforeMount(){
  this.$http.get(`https://cnodejs.org/api/v1/user/${this.$route.params.name}`)
    .then(res=>{
      this.isLoading = false; //加载成功，去除动画
      this.userinfo = res.data.data;
    })
    .catch(function (err) {
      //处理返回失败后的问题
      console.log(err)
    })
  }
}
```
