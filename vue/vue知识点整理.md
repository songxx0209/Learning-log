## vue知识点整理

1. 声明式渲染

   Vue.js 的核心是一个允许采用简洁的模板语法来声明式地将数据渲染进 DOM 的系统：

2. 条件与循环



3. 组件

   ```
   <template>
     <div class="btn" v-title :data-title="title"></div>
   </template>
   
   <script>
   export default {
       data() {
           return {
               A: xxx,
           }
       },
       
       beforeCreate() {},
       created() {},
       beforeMount() {},
       mounted() {},
       beforeUpdate() {},
       updated() {},
       activated() {},
       deactivated() {},
       beforeDestroy() {},
       destroyed() {},
   }
   </script>
   ```

   