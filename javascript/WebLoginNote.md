# web login

### 1：登录首先应该做什么呢？

- 用户输入U，P，点击登录，向后台发送请求；

- 后台服务器接受到u，p后，会记录下来，生成一个sessionid，csrfken；

- 下面会有两步，一是将sessionid放到cookie中通过response返回给前端的请求；二是：将sessionid保存包后台的 session store中；

- ---

  sessionid用来验证用户登录， csrfken用于防止csrf攻击（具体原理查资料）



- 当前前端浏览器cookie已经记录住sessionid，csrf；
- 浏览器中当用户发送下一次请求时，请求会自动带上cookie，发送到后台；
- 后台等到cookie中的sessionid，和session store中比较，成功返回相应的数据；



