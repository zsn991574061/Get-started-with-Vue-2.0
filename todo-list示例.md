# todo list示例

在本节中，我们将只使用vue来构建一个页内的todo list应用示例，本应用将通过一个根组件管理所有的数据，并下发给其他组件处理相关功能。

详细的项目源码可参看：[github地址](https://github.com/baka397/Vue-inpage-app)

## 功能点

1. 显示预设的todo list列表

2. 可以新增todo项

3. 可以标记、取消标记已取消的项

4. 记录todo list到localstorage


## 组件

1. list：载入todo模块；处理新增、删除、（添加、取消）标记；加载存储localstorage。

2. todo：显示todo项并发起事件到list模块。


## 数据结构

```
{
    "list":[{
        "content":"", //待办内容
        "complete":true //是否完成标记
    }]
}
```

