# CSS 文件设计与维护

## 文件结构设计

> 为了便于维护，最好将样式表划分为几大块

* 一般性样式  /* @group general styles */
	* 主体样式
	* reset样式
	* 链接
	* 标题
	* 其他元素
* 辅助样式  /* @group helper styles */
	* 表单
	* 通知和错误
	* 一致的条目
* 页面结构  /* @group page structure */
	* 标题、页脚和导航
	* 布局
	* 其他页面结构元素
* 页面组件  /* @group page components */
	* 各个页面
* 覆盖     /* @group overrides */