# 自定义loader

## markdown文件加载器，能够直接在代码中导入markdown文件，一般被转html后。在页面上显示
## Loader本质上就是一个ESM模块，它导出一个函数，在函数中对打包资源进行转换 
## 通过source参数接收输入
## 声明一个读取markdown文件内容的loader
## marked(将markdown语法转成html)
## loader-utils(接受loader的配置项) //webpack5不需要