<template>
  <Vssue
    :title="title"
    :options="options"
  />
</template>

<script>
import { VssueComponent } from 'vssue'
import GithubV3 from '@vssue/api-github-v3'
import 'vssue/dist/vssue.css'

export default {
  name: 'VssueDemo',

  components: {
    'Vssue': VssueComponent,
  },

  data () {
    return {
      title: 'Vssue Demo',
      options: {
        api: GithubV3,
        owner: 'OWNER_OF_REPO',
        repo: 'NAME_OF_REPO',
        clientId: 'YOUR_CLIENT_ID',
        clientSecret: 'YOUR_CLIENT_SECRET', // 只有在使用某些平台时需要
      },
    }
  },
}
</script>