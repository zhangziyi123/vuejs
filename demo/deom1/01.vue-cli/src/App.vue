<!--
<template>
  <div id="app">
    <img src="./assets/logo.png">
    <p>
      &lt;!&ndash; 使用 router-link 组件来导航. &ndash;&gt;
      &lt;!&ndash; 通过传入 `to` 属性指定链接. &ndash;&gt;
      &lt;!&ndash; <router-link> 默认会被渲染成一个 `<a>` 标签 &ndash;&gt;
      <router-link to="/foo">Go to Foo</router-link>
      <router-link to="/bar">Go to Bar</router-link>
    </p>
    &lt;!&ndash; 路由出口 &ndash;&gt;
    &lt;!&ndash; 路由匹配到的组件将渲染在这里 &ndash;&gt;
    <router-view></router-view>
  </div>
</template>

<script>
export default {
  name: 'app'
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
-->

<template>

  <div id="app" class="todoapp">
    <MyHeader @addTodoHandle="addTodo" />
 <!--   <Todos />-->
    <!-- 路由匹配到的组件将渲染在这里 -->
    <router-view></router-view>
    <MyFooter />
  </div>
</template>

<script>
  import MyHeader from './components/Header/Header'
  import MyFooter from './components/Footer/Footer'
  // import Todos from './components/Todos/Todos'
  export default {
    name: 'app',
    data () {
      return {
        todos: [], // 存储所有todos
        visibility: 'all' // 存储当前过滤条件
      }
    },
    methods: {
      addTodo (value) {
        console.log(value) // 输出看看子组件发送的消息内容
      }
    },
    components: {
      MyHeader, MyFooter //, Todos
    },
    created () {
      let filter = this.$route.params.filter
      if (!filter) {
        this.$router.replace({ path: 'All' })
      }
    }
  }

</script>
<style>
  @import '../node_modules/todomvc-app-css/index.css';
</style>
