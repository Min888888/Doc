# web 优化

## 实践

### 在页面加载后获取js

- js defer 保证脚本在源码定义中顺序执行
- 预连接第三方主机 proconnect     `https://cdn.staticfile.org`
  		<link rel="preconnect" href="https://">
  		preconnect并不是没有成本的，千万不能滥用。<link rel="preconnect">会占用宝贵的 CPU 时间，如果用户没有在 10 秒内使用该连接，资源浪费的情况就会变得更严重，因为当浏览器关闭连接时，所有已完成的连接都将遭到浪费。                                              <!--10秒内需要访问预连接网站-->
    <link rel="preconnect" href="https://cdn.staticfile.org"> 
- 预加载文件 rel="preload"，高优先级获取,  需要指定有效的as 值，如 style,script                                                                                                                  <link href="https://cdn.staticfile.org/element-plus/2.2.17/index.css" rel="preload stylesheet" as="style">