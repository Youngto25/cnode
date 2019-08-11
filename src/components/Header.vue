<template>
  <div class="wrapper">
    <div class="compainer">
      <div class="header">
        <router-link :to="{name:'root'}">
          <img src="../assets/cnodejs_light.svg" alt />
        </router-link>
        <ul>
          <li>
            <router-link :to="{name: 'root'}">
              首页
            </router-link>
          </li>
          <li>
            <router-link :to="{name: 'about'}">
              关于
            </router-link>
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
<style lang="scss" scoped>
@media screen and (max-width: 799px){
  .wrapper{
    background-color:#5a5555;
    .compainer{
      padding: 0 8px;
      .header{
        height: 50px;
        img {
          max-width: 100px;
          margin-top: 10px;
        }
        a {
          text-decoration: none;
          color: #ccc;
          font-size: 14px;
          text-shadow: nonr;
        }
        ul {
          list-style: none;
          float: right;
          margin: 4px;
          li {
            display: inline-block;
            padding: 10px 4px;
            &:last-child {
              margin-right: 0;
              padding-right: 0;
            }
          }
        }
      }
    }
  }
}

@media screen and (min-width: 800px){
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
}
</style>
