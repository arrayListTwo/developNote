# 删除DOM

* 删除一个节点，首先要获得该节点本身以及它的父节点，然后，调用父节点的`removeChild`把自己删掉
```JavaScript
// 拿到待删除节点:
var self = document.getElementById('to-be-removed');
// 拿到父节点:
var parent = self.parentElement;
// 删除:
var removed = parent.removeChild(self);
removed === self; // true
```

* 删除的节点虽然不在文档树中，但还在内存中，可以随时再次被添加到别的位置

* 当遍历一个父节点的子节点并进行删除操作时，`children`属性是一个只读属性，并且它在**子节点变化时会实时更新**