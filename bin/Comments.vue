<template>
  <div class="comments-wrapper">
    <component
    v-show="isShow"
    :is="componentName"
    :options="options" />
  </div>
</template>

<script>
import Valine from './Valine.vue'
import Vssue from './Vssue.vue'
export default {
  components: { Valine, Vssue },
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
    // 是否显示评论
    isShow () {
      const frontmatter = this.$frontmatter
      return !(this.isShowComments == false || frontmatter.isShowComments == false || frontmatter.home == true)
    },
    solution () {
      const { solution: slt } = this.commentsOptions,
            { valineConfig, vssueConfig } = this.$themeConfig;
      if (slt !== undefined) {
        return slt
      } else if (valineConfig !== undefined) {
        return 'valine'
      } else if (vssueConfig !== undefined) {
        return 'vssue'
      }
      return ''
    },
    options () {
      const { options: opt } = this.commentsOptions,
            { valineConfig, vssueConfig } = this.$themeConfig;

      if (opt !== undefined) {
        return opt
      } else if (valineConfig !== undefined) {
        return valineConfig
      } else if (vssueConfig !== undefined) {
        return vssueConfig
      }
      return null
    },
    componentName () {
      const solution = this.solution
      return solution === 'valine' ? 'Valine' : solution === 'vssue' ? 'Vssue' : ''
    }
  }
}
</script>
