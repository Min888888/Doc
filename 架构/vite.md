# 依赖

## postcss

概念： [PostCSS](https://so.csdn.net/so/search?q=PostCSS&spm=1001.2101.3001.7020) 也是用来处理 CSS 的，只不过它更像是一个工具箱，可以添加各种各样的插件来处理 CSS 。像我们经常遇到的样式兼容性问题，如高级 CSS 语法的降级、前缀补全等，都可以通过 PostCSS 来解决。 

 npm install postcss-preset-env -D 

```js
// vite.config.js
import { defineConfig } from 'vite'
import postcssPresetEnv from 'postcss-preset-env'

export default defineConfig({
  css: {
    postcss: {
      plugins: [postcssPresetEnv()]
    }
  }
})
```

vite我爱你
