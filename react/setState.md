# setState

## 不能直接修改state，直接更新dom不会更新
## setState可能会被合并
## 传入对象会被合并，只执行一次
## 传入函数不会被合并
## this.setState(newState)
## newState存入pending队列
## 是否处于batch update
## 是：保存于 dirtyComponents中
## 否：遍历所有的dirtyComponents，调用updateComponent，更新pending state or props

## batchUpdate机制：
## batchUpdate机制那些能命中：
## 生命周期，React中注册的事件,React可以管理的入口
## 普通：异步更新 
## 定时器,自定义dom事件：同步更新
## 执行函数设置true，结束设置false
## 处于batchUpdate异步执行，不处于异步执行
## 如何判断处于机制isBatchingUpdates是false还是true

xxx = () => {
	//开始:处于batchUpdate机制
	//isBatchingUpdates =ture
	this.setState({ xxx }) //直接执行
	//结束isBatchingUpdates =false
}

xxx = () => {
	//开始:处于batchUpdate机制
	//isBatchingUpdates =ture
	setTimeout(() => {
		//此时isBatchingUpdates=false
		this.setState({ xxx })
	}) //开始被跳过
	//结束isBatchingUpdates =false
}