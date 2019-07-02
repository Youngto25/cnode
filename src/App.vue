<template>
  <div id="app">
    <Header></Header>
    <div class="main">
      <router-view name="slidebar"></router-view>
      <router-view name="main"></router-view>
    </div>
    <div class="footer"> 
      <Footer></Footer>
    </div>
  </div>
</template>

<script>
import Header from "./components/Header";
import Footer from "./components/Footer";
import PostList from "./components/PostList";
export default {
  name: "App",
  components: {
    Header,
    PostList,
    Footer
  }
};
</script>

<style scoped>
#app{
  background-color: #fff;
}
.main {
  width: 80%;
  margin: 0 auto;
}
.footer{
  background-color: #f7fbfd;
  margin-top: 10px;
}
</style>
