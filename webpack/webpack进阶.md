# webpack进阶
## 区分打包环境
## 通过环境变量区分
## Webpack4: webpack --env.production
## Webpack5: webpack --env production开发环境不需要压缩
## webpack.config.js判断env

## 通过配置文件区分
### webpack-merge
### webpack.dev.conf.js
### webpack.prod.conf.js
### 执行打包时，指定配置文件(webpack --config webpack[dev|prod].conf.js)

## Webpack DefinePlugin
### 		new webpack.DefinePlugin({
###			//开发环境下的接口地址
###			// API_BASE_URL: 'xxxxxxxx' //打包之后不是一个字符串，变量后面的值是代码片段
###			API_BASE_URL: JSON.stringify('12341234'),
###		}),

## 代码分离
### 1所有代码打包到一起，可能最终的代码非常大，从而影响加载时间
### 2很多代码初始是不需要的.因此，我们可以根据代码使用的紧急程度，将代码分割打包后，按需加载如何代码分离

### 1.多入口打包：配置entry加载多个入口文件

### 2.提取公用模块
### 如果多个页面都用到了一个公共文件，每个页面都将公共文件打包一次是不合理的，需要将公共文件提取出来
###		optimization: {
###			splitChunks: {
###				chunks: 'all', //提取所有公共文件
###			},
###		},

### 3.动态导入：按需加载
### 默认不加载，事件触发后才加载
### 预加载 先等待其他资源加载，浏览器空闲时，再加载 network中可以查看
###   //import 启动懒加载
###  //webpackChunkName: 'desc' 指定打包文件的名称
###  //webpackPrefetch:true 启动预加载//network中可以看见,移动端有兼容性
###  // eslint-disable-next-line
###  import(/*webpackChunkName: 'desc',webpackPrefetch:true*/ './wp').then(({ desc }) => {
###    alert(desc())
###  })

### 排除依赖(externals)
### 一般来说，一些成熟的第三方库，是不需要打包的，例如jquery
### externals: { jquery: 'jQuery' },
## 源码分割（Source Map）
### 是一种源代码与构建后代码之间的映射技术
### 通过.map文件，将构建后的代码与源代码之间建立映射关系
### 可以快速定位代码问题
### devtool: '映射模式’
### 通过source-map会得到两类文件.js和.map,.js和.map会建立联系通过//# sourceMappingURL
### 开发环境（eval-cheap-module-source-map）//没有经过loader加工
### 生产环境（none|nosources-source-map）

### Tree Shaking
### 删除未引用的代码：1return后面的代码  2只声明，而未使用的函数 3只引入，未使用的代码
### 使用ES Modules规范的模块，才能执行Tree Shaking,依赖于ES Modules的静态语法分析

### sideEffects
### 无副作用：如果一个模块单纯的导入导出变量，那它就无副作用
### 有副作用：一个模块修改其他模块或者全局的东西，就有副作用
### 修改全局变量，在原型上拓展方法，css引入
### 删除未使用且无副作用的内容
### sideEffects:true
### False:所有代码都没有副作用
### True：所有代码都有副作用
### sideEffects:[xxx,xxx]告诉webpack哪些有副作用

### 生产模式会自动开启
###		optimization: {
###			//标记未被使用的代码
###			usedExports: true,
###         sideEffects:true
###			//删除被usedExports标记的未使用的代码
###			minimize: true,
###			splitChunks: {
###				chunks: 'all', //提取所有公共文件
###			},
###		},

### Tree Shaking和Source Map存在兼容性问题
### eval模式，将js输出为字符串，不是ES Modules规范，导致tree shaking失效

### babel缓存							
### 第二次构建时，会读取之前的缓存
### cacheDirectory: true
### 如果代码在缓存期内，代码更新后看不到实时效果
### 解决：将代码文件名称，设置为哈希名称，名称发生变化时，就加载最新的内容
### webpack 哈希值
### hash(每次webpack打包生成的hash值)
### chunkhash(不同的chunk的hash值不同，同一次打包可能生成不同的chunk)//只会影响一路的打包
### contenthash(不同内容的hash值不同，同一个chunk中可能有不同的内容)//针对一类内容

### 模块解析
### resolve
### 配置模块解析的规则
### alias:配置模块加载的路径别名
### alias:{'@‘:resolve(’src')}
### extensions:引入模块时，可以省略那些后缀

