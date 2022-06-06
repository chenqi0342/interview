## px,em,rem,vh&vw

### px 绝对单位
#### pixel的缩写，网页开发的基本长度单位

### em 相对单位
#### 相对于父元素进行计算
#### 通常用于字体缩进

### rem 相对单位
#### 相对html字体大小进行计算，通常html设置为100px
#### 用于响应式布局

### vw和vh 相对当前网页视口宽度和高度计算
#### 1vw视口宽度的1%，1vh视口高度的1%
#### 用于响应式布局
#### // window.innerHeight === 100vh
#### // window.innerWidth === 100vw

### px,em,rem转换
#### 默认16px=1em=1rem

### rem的弊端：“阶梯”性
### window.screen.height //屏幕高度
### window.innerHeight //网页视口高度
### window.body.clientHeight //body高度