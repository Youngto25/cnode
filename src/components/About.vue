<template>
<div>
  <div class="all">
    <div class="introduce">
      <p>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;该项目使用 Vue 还原 CNode 官方社区，项目调用 CNode 官方社区提供的 API，以 Vue CLI 创建项目模版，使用 axios 获取数据，使用 Vue Router 进行前端路由的切换及传参，使用 watch 监听路由的变化，使用媒体查询引入不同 CSS，Webpack 打包。</p>
    </div>
  </div>
  <div  class="footer">
    <Footer></Footer>
  </div>
</div>
</template>
<script>
import Footer from "./Footer";
export default {
  components: {
    Footer
  }
}
</script>
<style lang="scss" scoped>
.all{
  width: 100%;
  height: 80vh;
  display: flex;
  justify-content: center;
  align-items: center;
  .introduce{
    background: #ecf0f1;
    width: 80%;
    padding: 20px;
  }
}
.footer{
  position: fixed;
  bottom: 0px;
  left: 0;
  right: 0;
}
</style>
