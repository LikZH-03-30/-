<template>
  <div class="app">
    <!-- $time_evening  你怎么还没下班呀！ -->
    <MyHeader title="全场只要一块多" color="green"></MyHeader>
    <MyGoods v-for="item in goodsList" :key="item.goods_id" :goods='item'></MyGoods>
    <MyFooter :goodsList='goodsList'></MyFooter>
  </div>
</template>

<script>
import MyHeader from './components/MyHeader.vue'
import MyGoods from './components/MyGoods.vue'
import MyFooter from './components/MyFooter.vue'
import axios from 'axios'
export default {
  components: {
    MyHeader,
    MyGoods,
    MyFooter
  },
  data() {
    return {
      goodsList: []
    }
  },
  created() {
    this.getGoods()
  },
  methods: {
    async getGoods() {
      const res = await axios({ url: '/api/cart' })
      this.goodsList = res.data.list
      console.log(res)
    }
  }
}
</script>

<style scoped>
.app {
  box-sizing: border-box;
  padding: 50px 0;
  max-height: 100vh;
  overflow: auto;
}
</style>
