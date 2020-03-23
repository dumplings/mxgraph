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
