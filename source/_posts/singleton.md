### 单例模式
* javascript类实现单例模式
1. 构造类实现单例模式
```
const Obj=function(name,age){
  this.name=name;
  this.age=age;
}
Obj.prototype.init=function(){
  console.log('实现单例模式')
}
Obj.getState=function(data,val){
  let state;
  if(!state){
    state=new Obj(data,val)

  }
  return state;
}
const a=Obj.getState('zhangsan',22);
const b=Obj.getState('lisi',33);
console.log(a===b)
  //输出true
```
2. 代理类实现单例模式
```
const Obj=function(name){
  this.name=name;
}
Obj.prototype.init=function(){
  console.log('实现单例模式')
}
//代理类实现单例模式
const ProxyClass=(function(){
  let state;
  return function(val){
    if(!state){
    state=new Obj(val)
    }
    return state;
  }
})();
const a=new ProxyClass('zhangsan')
const b=new ProxyClass('lisi')
console.log(a===b);
  //输出true
```
* javascript中函数实现单例模式
3. 惰性单例模式
```
const test=function(){
     console.log('创建的dom节点'+new Date())
}
const singFn=(function(fn){
      let  state;
      return function(){
      return state || (state=fn.apply(this,arguments))
      //这里涉及到短路或的知识点
      // const a=3&&4 短路与，左边的是true就会返回右边的值，a=3||4 如果左边的是false，就会返回右边的值
      }
    })()
const a=singFn(test)
const b=singFn(test)
  consle.log(a===b)//输出true
```
