<template>
  <div class="search-container">
    <!-- 顶部的搜索栏 -->
  <form action="/">
    <van-search
      v-model="value"
      show-action
      placeholder="请输入搜索关键词"
      background="#3296fa"
      @search="onSearch"
      @cancel="onCancel"
    />
  </form>
    <!-- /顶部的搜索栏 -->
  </div>
</template>

<script>
export default {
  name: 'SearchIndex',
  components: {},
  props: {},
  data () {
    return {
      value: ''
    }
  },
  computed: {},
  watch: {},
  created () {},
  mounted () {},
  methods: {
    onSearch (val) {
      console.log(val)
    },
    onCancel  () {
      this.$router.back()
    }
  }
}
</script>

<style lang='less' scoped>
  .search-container {
    .van-search_action {
      color: #fff;
    }
  }
</style>
