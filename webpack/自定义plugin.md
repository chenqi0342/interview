# 自定义plugin

## Webpack插件是一个具有apply方法的js对象apply方法会被webpack compiler调用，并且在整个编译生命周期都可以访问compiler对象
## 通过在生命周期的钩子中挂载函数，来实现功能拓展
## environment 环境准备好
## compile 编译开始
## compilation 编译结束
## emit 打包资源到output之前 //最后挂载功能的机会
## afterEmit 打包资源到output之后
## done 打包完成

##	//必须声明apply方法,webpack启动时被自动调用
##	apply(compiler) {
##		//在钩子挂载功能 tap方法注册，插件名称，挂载到钩子上的函数
##		compiler.hooks.emit.tap('MyPlugin', (compilation) => {
## 		//compilation打包上下文 assets访问
##		for (const name in compilation.assets) {    