# 组件更新过程
## js是单线程，且和dom渲染共用一个线程
## reconciliation阶段：执行diff算法，纯js计算
## commit阶段：将diff结果渲染dom（无法拆分）
## Fiber：将reconciliation阶段进行任务拆分
## Dom需要渲染时暂停，空闲时恢复