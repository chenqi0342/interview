# webpack基础

## webacpk 功能
### 1.将多个文件合并，减少http请求
### 2.将代码进行编译，保证浏览器兼容性
### 3.对代码进行压缩，减少文件大小，提高加载速度
### 4.检测代码格式，确保代码质量
### 5.提供热更新服务，提高开发效率
### 6.针对不同环境，提供不同的打包策略

## 打包css
### use['style-loader','css-loader']
### style-loader把包含css内容的js代码，挂载到页面的<style>标签中
### css-loader 将css转化为js代码
### mini-css-extract-plugin 打包成独立文件
### postcss-loader autoprefixer 添加样式前缀 兼容不同浏览器
### stylelint stylelint-config-standard stylelint-webpack-plugin 格式校验
### optimize-css-assets-webpack-plugin 压缩css

## 打包html
### html-webpack-plugin
### 自动生成html文件（用于服务器访问），并在html中加载所有打包资源
### 指定html模版 设置html变量 压缩html

## 编译js 
### 将es6+转成es5，从而保证，js在低版本浏览器的兼容性
### babel-loader 通过babel进行转译
### @babel/core 包含js转译的插件
### @babel/preset-env 转译的规则集,转译不彻底，不能转移高级特性
### @babel/polyfill 转译所有js新语法，所有的都转译，不管用没用
### core-js 按需转译Js新语法
### eslint 校验js代码格式的工具
### eslint-config-airbnb-base 最流行的js代码格式规范
### eslint-webpack-plugin  webpack的eslint插件
### eslint-plugin-import 用于在package.json中读取eslintConfig配置项

## 打包图片
### file-loader:将用到的图片复制到输出目录，过滤掉不用的图片
### url-loader:需要配合file-loader
### file-loader的升级版，如果图片小于配置大小，会转成base64字符串,转成base64字符串后，图片会跟js一起加载（减少图片的请求次数）

## 字体文件
### file-loader
### copy-webpack-plugin 不需要特殊处理的文件，直接复制到输出目录
### clean-webpack-plugin 每次打包之前，先删除历史文件

## webpack5 资源模块(Asset Modules)
### 资源模块是一种模块类型，它允许使用资源文件，而无需配置额外的loader
### 字体，图片，图标，HTML…
### asset/resource发送一个单独的文件并导出URL(之前通过file-loader实现)
### asset/inline 导出一个资源的data URI(之前通过使用url-loader实现)
####  asset默认使用，asset/inline，大了选择asset/resource
##### type:'asset',
##### parser:{dataUrlContion:{maxSize:8*1024}}
##### generator:{filename:""}
### asset/source 导出资源的源代码（之前通过raw-loader实现）
### asset 在导出一个data URI和发送一个单独文件之间自动选择(url-loader)

## DevServer
### Webpack Dev Server
### 发布web服务，提高开发效率
### Webpack4: webpack-dev-server  hot:true
### Webpack5: 1 webpack serve 2 liveReIoad: true(禁用hot)   target:’web’
### proxy(配置接口代理):解决跨域问题
###			proxy: {
###				// http://localhost:9200/api 访问这个地址，指向github地址 
###             http://localhost:9200/api/users=> https://api.github.com/api/users
###				'/api': {
###					target: 'https://api.github.com',
###					//匹配路径里有/api，给他设置为空
###					pathRewrite: {
###						'^/api': '',
###					},
###					//不能localhost:9200作为github主机名,会报错
###					changeOrigin: true,
###				},
###			},