<template>
  <div>
    <Header></Header>
    <div class="article_list">
      <ul>
          <!-- v-for循环数据 -->
        <li v-for="i in list" :key="i.id">
            <!-- v-text="i.create_at"渲染时间数据 -->
          <time v-text="$utils.goodTime(i.create_at)"></time>
          <!-- router-link：vuerouter2声明式导航 -->
          <router-link :to="'/content/' + i.id">
            {{ i.title }}
          </router-link>
        </li>
      </ul>
    </div>
    <Footer></Footer>
  </div>
</template>
<script>
import Header from '../components/header.vue'
import Footer from '../components/footer.vue'
export default {
  components: { Header, Footer },
  data () {
    return {
      list: []
    }
  },
  created () {
    this.getData()
  },
  methods: {
    getData () {
      this.$api.get('topics', null, r => {
        this.list = r.data
      })
    }
  }
}
</script>