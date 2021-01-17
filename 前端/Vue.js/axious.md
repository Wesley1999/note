# axious
Vue.js推荐使用axios来完成ajax请求。
官方文档：https://cn.vuejs.org/v2/cookbook/using-axios-to-consume-apis.html

## 用法
```
new Vue({
  el: '#app',
  data () {
    return {
      info: null
    }
  },
  mounted () {
    axios.post("/api/get_all_apps.action")
        .then(function (returnData) {
            main_page.app_filter_options = returnData.data.data;
        });
  }
})
```
其中，`axios.post`的第二个参数是ajax请求的参数，默认为json对象。

如果要以键值对的形式传参，可以创建一个URLSearchParams对象：
```
let params = new URLSearchParams();
params.append("cve", cve);
axios.post('/api/get_plugins_by_cve.action', params)
    .then(function (returnData) {
        if (returnData.data.status === 0) {
            let data = returnData.data.data;
            // ...
        } else {
            // ...
        }
    })
```