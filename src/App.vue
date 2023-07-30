<template>  <!-- vue 구성요소1 template - html -->
  <div class="container"> <!-- bootstrap class : 왼쪽, 오른쪽 띄어줌-->
    <h2>To-Do List</h2>  <!-- TodoSimpleForm : 자식 component, App.vue : 부모 component -->
    <TodoSimpleForm @add-todo="addTodo" /> <!-- 자식의 context.emit의 add-todo로 부터 data 받아, addTodo(부모) 실행 -->
    <div v-if="!todos.length">  <!-- todos 원소 개수가 0일때, 보여줌 -->
      추가된 todo가 없습니다.
    </div>
    <TodoList :sendTodos="todos" /> <!-- 부모 -> 자식으로 sendTodos란 속성으로 todos 데이터 전송 -->
  </div>
</template>

<script>  // vue 구성요소2 script - js
import {ref} from 'vue';
import TodoSimpleForm from '@/components/TodoSimpleForm.vue'
import TodoList from '@/components/TodoList.vue'

export default {  
  components: {
    TodoSimpleForm,
    TodoList,
  },
  setup() {       
    const todos = ref([]);

    const addTodo = (todo) => { // todo : 자식 componet에서 넘겨준 object
      todos.value.push(todo);
    }

    const todoStyle = {
      textDecoration: 'line-through', // text-decoration -> textDecoration 사용
      color: 'gray',
    }

    const deleteTodo = (index) => { // todo 삭제
      todos.value.splice(index, 1);  // array 에서 index 일치하는 놈, 1개만 제거
    };

    return {      
      todos,
      todoStyle,
      deleteTodo, 
      addTodo,
    };
  }
}
</script>

<style> /* vue 구성요소3 style - css */
.todo {
  color: gray;
  text-decoration: line-through;
}
</style>