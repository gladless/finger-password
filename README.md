# 图形密码  finger-password
finger-password | graphical password | 图形密码 | 九宫格密码

![示例](https://github.com/glad-less/finger-password/blob/master/images/finger-password.png)


### 用法
1. 先安装依赖 npm install --save finger-password
2. 在项目中导入  import Finger from 'finger-password'
3. 在代码中使用  var finger = new Finger(config, callback)

#### config配置如下
```
    id: 'canvas', // 父元素的id 必传
    width: 600, // 宽
    height: 600, // 高
    bgColor: '#eee', // 背景色
    lineColor: '#0089FF', // 线条颜色
    lineSize: 3, // 线条粗细
    errorColor: '#f56c6c', // 错误颜色
    cols: 3, // 一行有几个点
    rows: 3, // 一列有几个点
```

#### callback及相关操作
* callback 接收一个参数，参数为数组，值为连接的路径，当鼠标弹起绘制完成时返回，比如 [2, 4, 6, 3]
* Finger对象的drawResult方法， 可以直接调用Finger.drawResult(path, error) 来绘制路径，path为数组，比如[2, 4, 6, 3]， error为是否是错误状态boolean，默认为false，当error为true将绘制错误颜色的图形
* Finger对象的reset方法会重置图形到初始样子
* 结合使用，在callback中接收到绘制结果，比如 [1, 2] 当判断这个结果不符合预期，那么调用 Finger.drawResult([1, 2], true)展示错误状态并提醒用户， 1秒之后再调用Finger.reset 重置即可
* 回调中调用drawResult 需要设置延迟 setTimeout(()=>{}, 0), 否则在返回path之后清除画布会清除掉重新画的内容


#### 常用方法
* Finger.drawResult(path:Array<Number>, error:Boolean) // 绘制图形
* Finger.reset() // 重置界面


#### 例子
项目中的 demo.html 