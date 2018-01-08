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
 ```
  handleClickOnLikeButton () {
    this.setState((prevState) => {
      return { count: 0 }
    })
    this.setState((prevState) => {
      return { count: prevState.count + 1 } // 上一个 setState 的返回是 count 为 0，当前返回 1
    })
    this.setState((prevState) => {
      return { count: prevState.count + 2 } // 上一个 setState 的返回是 count 为 1，当前返回 3
    })
    // 最后的结果是 this.state.count 为 3
  }
```
实际上组件只会重新渲染一次，而不是三次；这是因为在 React.js 内部会把 JavaScript 事件循环中的消息队列的同一个消息中的 setState 都进行合并以后再重新渲染组件。

### 配置组件的props
```
const likedText = this.props.likedText || '取消'
const unlikedText = this.props.unlikedText || '点赞'
```
**怎么把 props 传进去呢？在使用一个组件的时候，可以把参数放在标签的属性当中，所有的属性都会作为 props 对象的键值**
   
```
render () {
    return (
      <div>
        <LikeButton likedText='已赞' unlikedText='赞' />
      </div>
    )
  }
```
   