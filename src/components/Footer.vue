<template>
  <footer>
    <div class="wrapper">
        Designed by 
        <svg class="icon" aria-hidden="true">
          <use xlink:href="#icon-github"></use>
        </svg>
        <a href="https://github.com/Youngto25" target="_blank">Youngto</a>
    </div>
  </footer>
</template>
<script>
import '../svg/code'
export default {
  name: 'Footer'
}
</script>
<style lang="scss" scoped>
.wrapper{
  height: 50px;
  margin: 0 auto;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 14px;
  color: #333333;
  .icon{
    width: 20px;
    height: 20px;
    margin: 0 8px;
  }
}
a{
  text-decoration: none;
  color: #333333;
}
</style>
