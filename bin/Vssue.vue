<template>
  <VssueComponent
    :key="key"
    :options="vssueOptions"
  />
</template>

<script>
import { VssueComponent } from 'vssue'
import GithubV3 from '@vssue/api-github-v3'
import GithubV4 from "@vssue/api-github-v4"
import GitlabV3 from "@vssue/api-gitlab-v4"
import BitbucketV2 from "@vssue/api-bitbucket-v2"
import GiteeV5 from "@vssue/api-gitee-v5"
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
      key: 'key',
      platformOptions: {
        'github': GithubV3,
        'github-v4': GithubV4,
        'gitlab': GitlabV3,
        'bitbucket': BitbucketV2,
        'gitee': GiteeV5
      }
    }
  },
  computed: {
    vssueOptions () {
      const { platformOptions, options } = this
      const platform = platformOptions[options.platform]
      return { ...options, api: platform }
    }
  },
  watch: {
    '$route' (to, from) {
      if (to.path !== from.path) {
        // 切换页面时刷新评论
        setTimeout(() => {
          this.key = `reco-${new Date().getTime()}`
        }, 300)
      }
    }
  }
}
</script>
