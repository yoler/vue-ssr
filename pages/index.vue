<template>
  <section class="container">
    <div class="item" v-for="(item, index) in list" :key="index">{{item.description}}</div>
  </section>
</template>

<script>
import Logo from '~/components/Logo.vue'
import axios from 'axios'

export default {
  components: {
    Logo
  },
  async asyncData (context) {
    let { data } = await axios.get('https://www.edrawsoft.cn/viewer/public/api/publish?offset=30&count=30&order=PV&sort=DESC&search=&lang=CN&price=1')
    return {
      title: data.data[0].title,
      list: data.data
    }
  },
  head () {
    return {
      title: this.title
    }
  }
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  flex-wrap: wrap;
}
.item{
  width: 20%;
  margin: 5%;
  background: #eee;
}
</style>
