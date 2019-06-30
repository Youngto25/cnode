<template>
  <div>
    <Header></Header>
    <div>
      <PostList></PostList>
    </div>
  </div>
</template>

<script>
import Header from './components/Header'
import PostList from './components/PostList'
import './css/reset.css'
export default {
  name: 'app',
  components: {
    Header,
    PostList
  }
}
</script>

<style>

</style>
