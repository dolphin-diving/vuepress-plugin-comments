# @vuepress-reco/vuepress-plugin-comments

## Introduce

Comments plugin for vuepress-theme-reco or other vuepress theme.

### Name

- **As plugin**: `@vuepress-reco/vuepress-plugin-comments`
- **As component**: `Comments (评论)` / `AccessNumber (使用 Valine 时的访问量)`（主题开发时使用）

## Option API

### Valine

---

需配置 `config.js`

```javscript
// 更改 /docs/.vuepress/config.js

module.exports = {
  theme: 'reco',
  themeConfig: {
    // valine
    valineConfig: {
      appId: '...',// your appId
      appKey: '...', // your appKey
    }
  }  
}
```

### appId

- required: `yes`
- description: 从 LeanCloud 的应用中得到的 appId
- type: `String`

### appKey

- required: `yes`
- description: 从 LeanCloud 的应用中得到的APP Key
- type: `String`

### placeholder

- required: `no`
- description: 评论框占位提示符
- type: `String`
- default: `just go go`

### notify

- required: `no`
- description: 评论回复邮件提醒，请参考[配置](https://github.com/xCss/Valine/wiki/Valine-%E8%AF%84%E8%AE%BA%E7%B3%BB%E7%BB%9F%E4%B8%AD%E7%9A%84%E9%82%AE%E4%BB%B6%E6%8F%90%E9%86%92%E8%AE%BE%E7%BD%AE)
- type: `Boolean`
- default: `false`

### verify

- required: `no`
- description: 验证码服务
- type: `Boolean`
- default: `false`

### avatar

- required: `no`
- description: Gravatar 头像展示方式，更多信息请查看[头像配置](https://valine.js.org/avatar.html)
- type: `String`
- default: `retro`

### visitor

- required: `no`
- description: 文章访问量统计
- type: `Boolean`
- default: `true`

### recordIP

- required: `no`
- description: recordIP
- type: `Boolean`
- default: `false`

### AccessNumber

---

### idVal

- description: valine 记录浏览数的 id 值
- type: `String`

### numStyle

- description: 浏览量的数字样式（用于调整不同位置的显示风格）
- type: `Object`

