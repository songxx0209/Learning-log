```
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>事件代理和addEventListener</title>
</head>

<body>
    <ul id="list">
        <li id="item1">item1</li>
        <li id="item2">item2</li>
        <li id="item3">item3</li>
        <li id="item4">item4</li>
    </ul>
    <script type="text/javascript">
    /*window.onload = function() {
        var ulNode = document.getElementById("list");
        var liNodes = ulNode.childNodes || ulNode.children;
        for (var i = 0; i < liNodes.length; i++) {
            liNodes[i].addEventListener('click', function(e) {
                alert(e.target.innerHTML);
            }, false);
        }
    }*/
    // 由上可以看出来，假如不停的删除或添加li，则function（）也要不停的更改操作，易出错，因此推荐使用事件代理
    // https://segmentfault.com/a/1190000002613617
    window.onload = function() {
        var ulNode = document.getElementById("list");
        ulNode.addEventListener('click', function(e) {
            console.log(e);
            if (e.target && e.target.nodeName.toUpperCase() == "LI") { /*判断目标事件是否为li*/
                alert(e.target.innerHTML);
            }
        }, true);
    };
    /*
        http://www.runoob.com/jsref/met-element-addeventlistener.html
        element.addEventListener(event, function, useCapture); IE9以下不支持该方法可以使用attachEvent()方法代替
        可以在文档中添加许多事件，添加的事件不会覆盖已存在的事件。
        document.getElementById("myBtn").addEventListener("click", myFunction);
        document.getElementById("myBtn").addEventListener("click", someOtherFunction);
    */
    </script>
</body>

</html>

```
