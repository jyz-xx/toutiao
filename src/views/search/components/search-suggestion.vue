<template>
  <div class="search-suggestion">
    <van-cell
    v-for="(item, index) in suggestions"
    :key="index"
    :title="item"
    icon="search"></van-cell>
  </div>
</template>

<script>
import { getSearchSuggestion } from '@/api/search.js'

export default {
  name: 'SearchSuggestion',
  components: {},
  props: {
    searchText: {
      type: String,
      required: true
    }
  },
  data () {
    return {
      suggestions: []
    }
  },
  computed: {},
  watch: {
    searchText: {
      handler (value) {
        this.loadSearchSuggestion(value)
      },
      // 第一次触发 handler
      immediate: true
    }
  },
  created () {},
  mounted () {},
  methods: {
    async loadSearchSuggestion (q) {
      try {
        const { data } = await getSearchSuggestion(q)
        this.suggestions = data.data.options
      } catch {
        this.$toast('获取失败，请稍后再试')
      }
    }
  }
}
</script>

<style lang='less' scoped>

</style>
