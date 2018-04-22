# Bootstrap 按钮（Button）插件

* 如需向按钮添加加载状态，只需要简单地向 `button` 元素添加 `data-loading-text`="Loading..." 作为其属性即可，如下面实例所示：

##### 实例
```html
<button id="fat-btn" class="btn btn-primary" data-loading-text="Loading..." 
    type="button"> 加载状态
</button>
<script>
    $(function() {
        $(".btn").click(function(){
            $(this).button('loading').delay(1000).queue(function() {
            // $(this).button('reset');
            // $(this).dequeue(); 
            });
        });
    });  
</script>
```
##### 效果
![](https://i.imgur.com/I4cXc0W.png)