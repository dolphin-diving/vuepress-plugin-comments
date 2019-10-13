<template>
  <div class="valine-wrapper" v-show="isShowComment">
    <div id="valine"></div>
  </div>
</template>

<script>

export default {
  props: {
    isShowComment: {
      type: Boolean,
      default: true
    }
  },
  mounted: function () {
    this.createValine()
  },
  methods: {
    createValine () {
      const valineConfig = this.$themeConfig.valineConfig
      if (valineConfig) {
        const Valine = require('valine')
        const AV = require('leancloud-storage')
        if (typeof window !== 'undefined') {
          this.window = window
          window.AV = AV
        }

        new Valine({
          el: '#valine',
          appId: valineConfig.appId, // your appId
          appKey: valineConfig.appKey, // your appKey
          placeholder: valineConfig.placeholder || 'just go go',
          notify: valineConfig.notify || false,
          verify: valineConfig.verify || false,
          avatar: valineConfig.avatar || 'retro',
          visitor: valineConfig.visitor || true,
          recordIP: valineConfig.recordIP || false,
          path: window.location.pathname
        })
      }
    }
  },
  watch: {
    '$route' (to, from) {
      if (to.path !== from.path) {
        // 切换页面时刷新评论
        // this.$router.go(0)
        setTimeout(() => {
          this.createValine()
        }, 300)
      }
    }
  }
}
</script>


