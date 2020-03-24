## 关于group的子项不移动的解决方案调研

#### link
* [prevent-a-vertex-from-being-moved-into-a-group](https://stackoverflow.com/questions/17536387/prevent-a-vertex-from-being-moved-into-a-group)
* [how-to-avoid-drag-and-drop-of-any-mxcell-or-vertex-from-a-group](https://stackoverflow.com/questions/36767869/how-to-avoid-drag-and-drop-of-any-mxcell-or-vertex-from-a-group)
* [mxGraph.isCellLocked](https://jgraph.github.io/mxgraph/docs/js-api/files/view/mxGraph-js.html#mxGraph.isCellLocked)

#### code

我的一个解决方案。感觉过于简单，相对于stackoverflow上面那个人的解决方案。这个比较受限，要求只能有一层layer。

```javascript
graph.isCellLocked= function(cell){
    if(cell.parent !== this.getDefaultParent()){
        return true;
    }
return false;
}
```

## 关于使用html

参考htmllabel的例子。

在mxGraph中想使用html，重要的方法是 `graph.convertValueToString`。例子中推荐的是定义xml节点，
关于要生成的html信息会写在xml上。当调用 `insertVertex` 时把xml对象以value的形式传给该函数，函数内部会在指定的位置触发 `convertValueToString`，这样就会把html节点渲染到graph中。

#### 知识点

* `graph.setHtmlLabels(true)` 启用对于html标签的支持；
* override `graph.convertValueToString` 进行对于xml节点的渲染方式；
* `mxUtils.isNode(cell.value)` 判断是否为xml节点；
* `obj.setAttribute` 只有xml节点才有该函数；
* 内部插入的dom节点是不会随主体zoom改变的，好像是给的文字内容都不会变化；
