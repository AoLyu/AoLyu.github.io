### promise async await异步编程

避免函数嵌套地狱。

```javascript
function A() {
    // 两个回调函数， pending 待定状态。分别对应执行成功和失败
    return new Promise((resolve,reject)=>{
            if(成功) { 
                resolve('执行成功')
            }
        	else {
            	reject('执行失败')
            }
    }
                      )
}
```

promise对象

.then接收已兑现(fullfilled)的结果

.catch接收已拒绝（reject)的结果

```javascript
const promise = A()
promise.then(res=>{
	console.log(res) // res为 resolve和reject里的参数
})
```

可以链式编写

```javascript
A().then((res)=>{
    //sth todo with res...
    //B返回的也是promise对象
    return B()
}).then((res)=>{
    //sth to do with res
}
)
```

大量链式调用也不好看

升级, 简化

**async**      **await**，必须一起使用

```javascript
async function test() {
    const resA = await A()
    console.log(resA)
    
    const resB = await B()
    console.log(resB)
    
    const resC = await C()
    console.log(resC)
}
```

优化多次请求的例子

```javascript
pA() {
    return new Promise((resolve,reject)=> {
        console.log('执行a接口的逻辑')
        wx.request({
            url:'....',
            success:()=>{
                resolve(res)
            },
            fail:(err)=> {
                reject(err)
            }
        }
        )
    })
}

// 。。。 类似 pB() pC()

async onAsyncClick() {
    const resA = await this.pA();
    //sth to do
    const resB = await this.pB();
    //sth to do
    const resC = await this.pC();
},
```

