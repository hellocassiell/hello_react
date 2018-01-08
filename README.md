 ## JSX （就是 JavaScript 对象）
 #### 添加类名
 ```
 <div className={className}>
 ```
 #### for循环
 ```
 <label htmlFor='male'>Male</label>
 ```
 #### 条件返回
 ```
  {isGoodWord
          ? <strong> is good</strong>
          : <span> is not good</span>
        }
 ```
 #### 显示或者隐藏某些元素
 ```
  {isGoodWord
          ? <strong> is good</strong>
          : null
        }
 ```

 #### 事件监听
 ```
  <h1 onClick={this.handleClickOnTitle}>React 小书</h1>
```
##### event 对象
React.js 中的 event 对象并不是浏览器提供的，而是它自己内部所构建的。
```
handleClickOnTitle (e) {
    console.log(e.target.innerHTML)
  }
```
##### 关于事件中的 this
React.js 调用你所传给它的方法的时候，并不是通过对象方法的方式调用（this.handleClickOnTitle），而是直接通过函数调用 （handleClickOnTitle）
```
 handleClickOnTitle (e) {
    console.log(this) // => null or undefined
  }
```
如果想在事件函数当中使用当前的实例，你需要手动地将实例方法 bind 到当前实例上再传入给 React.js。
```
 <h1 onClick={this.handleClickOnTitle.bind(this)}>React 小书</h1> 
```
 ## 组件
 自定义的组件都必须要用大写字母开头

 在 Header组件 里面使用 Title组件
 ```
 class Header extends Component {
  render () {
    return (
      <div>
        <Title />
      </div>
    )
  }
}
```
### state
 React.js 的 setState 把传进来的状态缓存起来，稍后才会更新到 state 上