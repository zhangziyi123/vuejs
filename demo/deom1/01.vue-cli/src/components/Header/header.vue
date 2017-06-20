<template>
  <header class="header">
    <h1>todos</h1>
    <input class="new-todo" autofocus autocomplete="off"
      placeholder="what needs to be done?"
      v-model="newTodo" @keyup.enter="addTodo">
  </header>

</template>

<script>
  export default{
    name: 'header',
    data () {
      return {
        newTodo: ''  // 使用v-model将input的vulue属性绑定到newTodo
      }
    },
    methods: {
      addTodo () {
        // 主动触发addTodoHandle方法，'addTodoHandle'为向父组件传递的数据
        this.$emit('addTodoHandle', this.newTodo)
      }
    }
  }

</script>
