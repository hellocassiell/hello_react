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