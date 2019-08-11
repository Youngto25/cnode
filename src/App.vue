<template>
  <div id="app">
    <Header></Header>
    <div class="main">
      <router-view name="slidebar" v-if="show"></router-view>
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
  data(){
    return {
      show: true
    }
  },
  components: {
    Header,
    Footer,
    PostList
  },
  mounted(){
    this.z = true
    window.addEventListener('resize',()=>{
      let width = document.documentElement.clientWidth
      width < 800 ? this.show = false : this.show = true
    })
  }
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
