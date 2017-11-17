<template>
  <div class='todo'>
    <h1>Todo List</h1>

    <ul class='list'>

      <todo-item
        v-for='todo in todoList'
        v-bind:todo='todo'
        v-bind:key='todo.id'
        v-on:checkTodo='todo.checked = !todo.checked'>
      </todo-item>

      <todo-item-add-new
        v-bind:addnew='addnew'
        v-on:addNewTodo='this.addNewTodo'>
      </todo-item-add-new>

    </ul>
  </div>
</template>

<script>
  import TodoItem from './TodoItem.vue'
  import TodoItemAddNew from './TodoItemAddNew.vue'

  export default {
    name: 'TodoApp',
    components: {
      TodoItem, TodoItemAddNew
    },
    data: function () {
      return {
        todoList: [{
          id: 0,
          title: 'first todo',
          description: 'un truc a faire sympa',
          checked: false,
          editMode: false
        }, {
          id: 1,
          title: 'un autre todo',
          description: 'lui il est pénible par contre',
          checked: true,
          editMode: false
        }, {
          id: 2,
          title: 'un petit dernier',
          description: 'tfaçon je te ferai jamais toi',
          checked: false,
          editMode: false
        }],
        addnew: {
          visible: false,
          title: '',
          description: ''
        }
      }
    },
    methods: {
      addNewTodo: function () {
        this.todoList.push({
          id: this.todoList.reduce((acc, td) => td.id > acc ? td.id : acc, 0) + 1,
          title: this.addnew.title,
          description: this.addnew.description,
          checked: false,
          editMode: false
        })
        this.addnew = {
          visible: false,
          title: '',
          description: ''
        }
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  h1 {
    font-weight: normal;
  }
  .list {
    width: 300px;
    margin: 0 auto;
    list-style: none;
    text-align: left;
    padding-left: 0;
  }
</style>
