<template>
  <div class="wrapper">
    <div class="compainer">
      <div class="header">
        <router-link :to="{name:'root'}">
          <img src="../assets/cnodejs_light.svg" alt />
        </router-link>
        <ul>
          <li>
            <a href="#">首页</a>
          </li>
          <li>
            <a href="#">新手入门</a>
          </li>
          <li>
            <a href="#">API</a>
          </li>
          <li>
            <a href="#">关于</a>
          </li>
          <li>
            <a href="#">注册</a>
          </li>
          <li>
            <a href="#">登录</a>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Header"
};
</script>

<style scoped>
* {
  margin: 0;
  box-sizing: border-box;
}
.wrapper{
  background-color:#5a5555 ;
}
.compainer {
  width: 80%;
  margin: 0 auto;
}
.header {
  height: 50px;
}
img {
  max-width: 120px;
  margin-top: 10px;
}
ul {
  list-style: none;
  float: right;
  margin: 4px;
}
li {
  display: inline-block;
  padding: 10px 15px;
}
ul > li:last-child {
  margin-right: 0;
  padding-right: 0;
}
a {
  text-decoration: none;
  color: #ccc;
  font-size: 14px;
  text-shadow: nonr;
}
</style>
