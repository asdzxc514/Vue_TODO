<template>
  
  <div id="app">
    <TodoHeader></TodoHeader>
    <TodoInput v-on:addTodo="addTodo"></TodoInput>
    <TodoList v-bind:propsdata="todoItems" @removeTodo="removeTodo"></TodoList>
    <TodoFooter v-on:removeAll="clearAll"></TodoFooter>
  </div>
</template>

<script>
import TodoHeader from './components/TodoHeader.vue'
import TodoInput from './components/TodoInput.vue'
import TodoList from './components/TodoList.vue'
import TodoFooter from './components/TodoFooter.vue'

export default {
  data(){
    return {
      todoItems: []
    }
  },
  created(){
      if(localStorage.length > 0){
          for(var i=0; i < localStorage.length; i++){
              this.todoItems.push(localStorage.key(i));
          }
      }
  },
  methods: {
    addTodo(todoItem) {
      // 로컬 스토리지에 데이터를 추가하는 로직
      localStorage.setItem(todoItem, todoItem);
      this.todoItems.push(todoItem);
    },
    removeTodo(todoItem, index) {
      localStorage.removeItem(todoItem);
      this.todoItems.splice(index, 1);
    },
    clearAll() {
      localStorage.clear();
      this.todoItems = [];
    }

  },
  
  components: {
    'TodoHeader': TodoHeader,
    'TodoInput': TodoInput,
    'TodoList': TodoList,
    'TodoFooter': TodoFooter,
  }
}
</script>

<style>
* { box-sizing: border-box; }
body { margin: 0; padding: 0; text-align: center; background-color: #f6f6f8; }
#app { padding: 0 0.9rem; }
input { padding: 0; border-style: groove; }
button { border-style: groove; }
.shadow { box-shadow: 5px 10px 10px rgba(0,0,0,0.03); }

</style>


