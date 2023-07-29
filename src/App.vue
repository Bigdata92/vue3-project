<template>  <!-- vue 구성요소1 template - html -->
  <div class="container"> <!-- bootstrap class : 왼쪽, 오른쪽 띄어줌-->
    <h2>To-Do List</h2>
    <form action="" @submit.prevent="onSubmit"> <!-- @submit : 제출시 함수 사용 / .prevent(Modifier) : 새로고침x  -->
      <div class="d-flex">
        <div class="flex-grow-1 mr-2"> <!-- 너비 늘어나게  -->
          <input type="text" v-model="todo" class="form-control" placeholder="Type new to-do"> <!-- 너비에 text 맞추기  -->
        </div>
        <div>
          <button class="btn btn-primary" type="submit">
            Click
          </button>
        </div>
      </div>
      <div v-show="hasError" style="color: red;">
        This field cannot be empty
      </div>
    </form>
    <div class="card mt-2" v-for="todo in todos" :key="todo.id">  <!-- for문 "object in arr" :key=objec.key  -->
      <div class="card-body p-2">
        <div class="form-check">
          <input type="checkbox" class="form-check-input" v-model="todo.completed">
          <label class="form-check-label" 
            :style="completed ? todoStyle : {}"
            :class="{ todo: todo.completed }">  <!-- style .todo는 todo.completed 가 true 일때만 -->
            {{ todo.subject }}  <!-- completed : true 일때만, style 적용되게 -->
          </label>
        </div>
      </div>
    </div>
  </div>
</template>

<script>  // vue 구성요소2 script - js
import {ref} from 'vue';

export default {  
  setup() {       
    const todo = ref('');
    const todos = ref([]);
    const hasError = ref(false);
    const todoStyle = {
      textDecoration: 'line-through', // text-decoration -> textDecoration 사용
      color: 'gray',
    }

    const onSubmit = () => {
      if (todo.value === '') {
        hasError.value = true;
      } else {
        console.log(todo.value);
        todos.value.push({  // []에 object push
          id: Date.now(),  // unique
          subject: todo.value,
          completed: false,   // default : false
        });
        hasError.value = false;
        todo.value = '';  // Click 버튼 클릭 후, 이전 검색어 제거
      }
    }


    return {      
      todo,
      todos,
      onSubmit,
      hasError,
      todoStyle,

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