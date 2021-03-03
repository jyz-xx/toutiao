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

import { debounce } from 'lodash'

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
      // 防抖
      handler: debounce(function (value) {
        this.loadSearchSuggestion(value)
      }, 400),
      // handler (value) {
      //    this.loadSearchSuggestions(value)
      //   console.log(value)
      // },
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
      } catch (err) {
        this.$toast('获取失败，请稍后再试')
      }
    }
  }
}
</script>

<style lang='less' scoped>

</style>
