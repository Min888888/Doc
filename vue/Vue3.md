# 组件

## vue注册组件名

- npm install unplugin-vue-define-options -D

- ```js
  import { defineConfig } from 'vite';
  import vue from '@vitejs/plugin-vue';
   
  import DefineOptions from 'unplugin-vue-define-options/vite';
   
  // https://vitejs.dev/config/
  export default defineConfig({
    plugins: [vue(), DefineOptions()],
  });d
  ```

- ```js
  <template>
    <button> </button>
  </template>
   
  <script lang="ts" setup>
    defineOptions({
      name: 'TButton',
    });
  </script>
   
  <style scoped></style>
  
  ```


# node 16 vue2启动实践

1. devDependencies { "node-sass": "^6.0.1","sass-loader": "^10.2.0"};
2. dependencies {"core-js": "^2.6.12"};
3. npm install              -----不要用cnpm:缺少core-js



## Reached heap limit Allocation failed - JavaScript heap out of memory

```json
"serve": "node --max_old_space_size=4999 node_modules/@vue/cli-service/bin/vue-cli-service.js serve --open",
```

