## flex布局实践学习

[阮哥flex学习资料](http://www.ruanyifeng.com/blog/2015/07/flex-grammar.html)

**使用：**

```
<!DOCTYPE html>
<html>
<head>
	<title></title>

	<style type="text/css">
		.container {
			width: 1000px;
			height: 500px;
			border: 1px solid red;
			display: flex;
			display: -webkit-flex;
			flex-wrap: nowrap;
			align-items: center;
		}

		.odiv {
			width: 100px;
			height: 100px;
			border: 1px solid black;
		}
	</style>
</head>

<body>
	<div class="container">
		<div class="odiv"></div>
		<div class="odiv"></div>
		<div class="odiv"></div>
		<div class="odiv"></div>
	</div>
</body>
</html>
```

大致的使用方式如上，具体细节 看阮哥总结；



**运用场景，哪些地方可以用、哪些不能用？**

```
display: -webkit-box;
display: -webkit-flex;
display: -ms-flexbox;
display: flex;
```

这种写兼容前缀的工作可以交给 工程化工具来实现，比如webpack 使用postcss