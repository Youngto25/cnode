<template>
  <div class="header">
    <img src="../assets/cnodejs_light.svg" alt="">
    <ul>
      <li><a href="#">首页</a></li>
      <li><a href="#">新手入门</a></li>
      <li><a href="#">API</a></li>
      <li><a href="#">关于</a></li>
      <li><a href="#">注册</a></li>
      <li><a href="#">登录</a></li>
    </ul>
  </div>
</template>
<script>
export default {
  name: 'Header'
}
</script>
<style scoped>
.header{
  background-color: #5a5555;
  height: 50px;
  display: flex;
  align-items: center;
}
img{
  max-width: 120px;
  margin-left: 30px;
}
ul{
  position: absolute;
  right: 40px;
}
ul>li{
  display: inline-flex;
  margin-left: 25px;
}
ul>li>a{
  color: #ccc;
  font-size: 14px;
  text-shadow: none;
}
</style>
