<template>
  <VssueComponent
    :title="title"
    :options="vssueOptions"
  />
</template>

<script>
import { VssueComponent } from 'vssue'
import GithubV3 from '@vssue/api-github-v3'
import 'vssue/dist/vssue.css'

export default {
  name: 'Vssue',
  components: { VssueComponent },
  props: {
    options: {
      type: Object,
      default () {
        return {}
      }
    }
  },
  data () {
    return {
      title: 'vuepress-theme-reco',
      platformOptions: {
        github: GithubV3
      }
    }
  },
  computed: {
    vssueOptions () {
      const { platformOptions, options, options: { title } } = this
      const platform = platformOptions[options.platform]
      if (title !== undefined) {
        this.title = title
        delete options.title
      }
      console.log(options)
      return { ...options, api: platform }
    }
  }
}
</script>
