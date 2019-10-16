<template>
  <div class="valine-wrapper">
    <div id="valine"></div>
  </div>
</template>

<script>

export default {
  name: 'Valine',
  props: {
    options: {
      type: Object,
      default () {
        return {}
      }
    }
  },
  mounted: function () {
    this.initValine()
  },
  methods: {
    initValine () {
      const Valine = require('valine')
      const AV = require('leancloud-storage')
      const valineOptions = {
        el: '#valine',
        placeholder: 'just go go',
        notify: false,
        verify: false,
        avatar: 'retro',
        visitor: true,
        recordIP: false,
        path: window.location.pathname,
        ...this.options
      }

      if (typeof window !== 'undefined') {
        this.window = window
        window.AV = AV
      }


      new Valine(valineOptions)
    }
  },
  watch: {
    '$route' (to, from) {
      if (to.path !== from.path) {
        // 切换页面时刷新评论
        // this.$router.go(0)
        setTimeout(() => {
          this.initValine()
        }, 300)
      }
    }
  }
}
</script>


