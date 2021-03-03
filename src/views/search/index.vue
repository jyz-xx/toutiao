<template>
  <div class="search-container">
    <!-- 顶部的搜索栏 -->
  <form action="/">
    <van-search
      v-model="searchText"
      show-action
      placeholder="请输入搜索关键词"
      background="#3296fa"
      @search="onSearch"
      @cancel="onCancel"
      @focus="isResultShow = false"
    />
  </form>
    <!-- /顶部的搜索栏 -->
    <!-- 搜索结果 -->
    <search-result v-if="isResultShow" />
    <!-- 搜索结果 -->

    <!-- 搜索历史记录 -->
    <search-suggestion
    v-else-if="searchText"
    :search-text = "searchText"
    />
    <!-- /搜索历史记录 -->

    <!-- 搜索历史记录 -->
    <search-history v-else/>
    <!-- /搜索历史记录 -->
    </div>
</template>

<script>
import SearchHistory from './components/search-history'
import SearchSuggestion from './components/search-suggestion'
import SearchResult from './components/search-result'
export default {
  name: 'SearchIndex',
  components: {
    SearchHistory,
    SearchSuggestion,
    SearchResult
  },
  props: {},
  data () {
    return {
      searchText: '',
      isResultShow: false
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
