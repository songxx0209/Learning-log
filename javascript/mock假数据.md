## 前端独立开发之mock假数据的方式

**mock假数据的方式**

1. 第一次接触mock假数据是在使用antd提供的脚手架上
2. 使用什么`esay mock`，`rap`，`ssr.js`，`json-server`、`dyson`

**antd也是使用的mockjs，具体实现后面研究一下**

。。。。。。。

**目前先研究一下esay mock的使用：**

这个感觉不太好用；

**json-server的使用：**

[学习地址](https://github.com/typicode/json-server)

配合mockjs 使用；

```
var ssa = require('mockjs');

function getdata() {
  let ss = ssa.mock({
    "data": {
      "msg": "",
      "data": {
        "total_count": 10,
        "total_page_num": 1,
        "trans_list": [
          "trans_time": "2017-12-15 10:40:00",
          "amount": "-816.00",
          "is_credit": false, // false:支出，true:收入
          "trans_id": 41512603, //#交易流水id
          "order_info": {
            "order_id": "00000300000005", // #订单id
            "service_type": "server", // #订单类型，server:服务器，disk:磁盘，lb:负载均衡
            "resource_id": "100106", // #资源id
          },
        ],
      },
      "success": "true"
    },
  })
  return ss;
}

module.exports = getdata
```



如何配置请求类型：post、get等；