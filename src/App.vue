<template>
  <div id="app">
    <Header></Header>
    <div class="main">
      <router-view name="slidebar"></router-view>
      <router-view name="main"></router-view>
    </div>
  </div>
</template>
<script>
import Header from "./components/Header";
import PostList from "./components/PostList";
export default {
  name: "App",
  components: {
    Header,
    PostList
  },
  mounted(){}
};
</script>
<style lang="scss" scoped>
@media screen and (min-width: 800px){
  #app{
    background-color: #fff;
  }
  .main {
    width: 80%;
    margin: 0 auto;
  }
}

@media screen and (max-width: 799px){
  #app{
    background: #fff;
    .main{
      width: 100vw;
      display: flex;
      flex-direction: column;
      align-items: center;
      overflow: hidden;
    }
  }
}

</style>
