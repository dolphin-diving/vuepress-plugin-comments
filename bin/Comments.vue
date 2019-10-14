<template>
  <div v-show="isShowComments">
    <component 
      :is="solution === 'valine' ? Valine : solution === 'vssue' ? Vssue : ''"
      :options="options" />
  </div>
</template>

<script>
import Valine from './Valine'
import Vssue from './Vssue'
export default {
  props: {
    isShowComments: {
      type: Boolean,
      default: true
    },
  },
  data () {
    return {
      commentsOptions: COMMENTS_OPTIONS
    }
  },
  computed: {
    solution () {
      const { solution: slt } = commentsOptions,
            { valineConfig, vssueConfig } = this.$themeConfig,
            solution = slt || valineConfig !== undefined ? 'valine' : vssueConfig !== undefined ? 'vssue' : ''
      return solution
    },
    options () {
      const { options: opt } = commentsOptions,
            { valineConfig, vssueConfig } = this.$themeConfig,
            options = opt || valineConfig !== undefined ? 'valine' : vssueConfig !== undefined ? 'vssue' : ''
      return options
    }
  }
}
</script>